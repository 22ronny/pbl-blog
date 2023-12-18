---
layout: post
title: "Catchbook English"
---
![alternative text](\pbl-blog\image\Banner.jpg)
## Introduction
As an avid angler, I decided to create a project about fishing. In this project, all catches are recorded, including the species, bait, location, time, and date.

## Programs Used
* Intellij
* Postman
* Proxmox 8 (Server OS)
* PostgreSQL
* pgAdmin
* Docker + Portainer
* draw.io (Planning)
* Visual Studio Code

## Database
#### PostgreSQL
The database was created in an LXC.
Connection via VPN (Wireguard)
* with Docker and Portainer
* with Proxmox (Debian Bookworm - Own server)

## Highlights
A filter with multiple parameters; if no parameter is chosen, the complete list is returned.
* **Dynamic Queries:**
  - Enables the creation of queries based on variable filter criteria. This is particularly useful when applications need to flexibly respond to user requests.

* **Reusability:**
  - The method can be reused in various parts of the application to create different queries with similar filter logic, without having to write a new method each time.

* **Adaptability:**
  - Allows users or other parts of the application to dynamically adjust the database query by changing only the relevant filter parameters.


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