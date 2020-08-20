---
sidebarDepth: 2
---

# Průvodce aktualizacemi

[[TOC]]

---

## 2.0.beta -> 2.0

tabulka oevent
event_category změna z json na integer
ALTER TABLE `oevents` CHANGE `event_category` `event_category` INT NULL DEFAULT NULL; 