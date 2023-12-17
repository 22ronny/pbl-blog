---
layout: post
title: "Catchbook German"
---
![alternativtext](\pbl-blog\image\Banner.jpg)
## Einleitung
Als begeisterter Angler beschloss ich, ein Projekt übers Angeln zu erstellen. In dem Projekt werden alle Fänge aufgezeichnet. Die Fischarten, Köder, Ort, Zeit und Datum.

## Verwendete Programme
* Intellij
* Postman
* Proxmox 8 (Server OS)
* PostgerSQL
* pgAdmin
* Docker + Portainer
* draw.io (Planung)
* Visual Studio Code



## Datenbank
#### PostgreSQL
Die Datenbank wurden in einem LXC erstellt.  
Verbindung über VPN (Wireguard)
* mit Docker und Portainer
* mit Proxmox (Debian Bookworm - Eigener Server)   

## Highlights
Ein Filter mit mehreren Parametern, sollte kein Parameter gewählt werden wird die komplette Liste zurückgegeben.

Controller:


```java
    @RequestMapping("/getCatch")
    List<CatchDto> getCatch(
            @RequestParam(required = false) Long fishTypeId,
            @RequestParam(required = false) LocalDateTime startDate,
            @RequestParam(required = false) LocalDateTime endDate,
            @RequestParam(required = false) Long speciesId,
            @RequestParam(required = false) Long baitId,
            @RequestParam(required = false) Long placeId) {
        return service.getCatch(fishTypeId, startDate, endDate, speciesId, baitId, placeId);
    }
```
  

Specification Class:

```java
    public static Specification<Catch> withFilters(Long fishTypeId, LocalDateTime startDate, LocalDateTime endDate, Long speciesId, Long baitId, Long placeId) {
        return (root, query, criteriaBuilder) -> {
            List<Predicate> predicates = new ArrayList<>();

            if (fishTypeId != null) {
                predicates.add(criteriaBuilder.equal(root.get("species").get("fishType").get("id"), fishTypeId));
            }

            if (startDate != null) {
                predicates.add(criteriaBuilder.greaterThanOrEqualTo(root.get("catchTime"), startDate));
            }

            if (endDate != null) {
                predicates.add(criteriaBuilder.lessThanOrEqualTo(root.get("catchTime"), endDate));
            }

            if (speciesId != null) {
                predicates.add(criteriaBuilder.equal(root.get("species").get("id"), speciesId));
            }

            if (baitId != null) {
                predicates.add(criteriaBuilder.equal(root.get("bait").get("id"), baitId));
            }

            if (placeId != null) {
                predicates.add(criteriaBuilder.equal(root.get("place").get("id"), placeId));
            }

            return criteriaBuilder.and(predicates.toArray(new Predicate[0]));
        };
    }
}
```

