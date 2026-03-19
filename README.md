# 🌌 Celestial Bodies Database

Project developed as part of the **Relational Databases** certification by [freeCodeCamp](https://www.freecodecamp.org/).

A PostgreSQL database modelling the universe — including galaxies, stars, planets, and moons — with a focus on relational schema design and data integrity constraints.

---

## 🛠️ Stack

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat&logo=postgresql&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat&logo=postgresql&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)

---

## 📁 Structure

```
celestial-bodies-db/
└── universe.sql    # Full database schema and seed data
```

---

## 💡 What this project demonstrates

- Multi-table relational schema with at least 5 linked entities
- Use of primary keys, foreign keys, and `NOT NULL` constraints
- Column types including `INT`, `NUMERIC`, `TEXT`, `BOOLEAN`, and `SERIAL`
- Data modelling decisions: naming conventions, relationships, and referential integrity
- Restoring and querying a PostgreSQL database from a `.sql` dump

---

## 🗄️ Schema overview

| Table | Description |
|---|---|
| `galaxy` | Top-level entities — named galaxies with type and distance data |
| `star` | Stars belonging to a galaxy |
| `planet` | Planets orbiting a star |
| `moon` | Moons orbiting a planet |
| `constellation` | Star constellations as an additional related entity |

---

## 🚀 How to run locally

**Prerequisites:** PostgreSQL installed and running.

```bash
# 1. Create the database
createdb universe

# 2. Restore schema and data
psql -U postgres universe < universe.sql

# 3. Connect and explore
psql -U postgres universe
```

Example queries to get started:

```sql
-- List all planets and their parent star
SELECT p.name AS planet, s.name AS star
FROM planet p
JOIN star s ON p.star_id = s.star_id;

-- Count moons per planet
SELECT p.name, COUNT(m.moon_id) AS moon_count
FROM planet p
LEFT JOIN moon m ON p.planet_id = m.planet_id
GROUP BY p.name
ORDER BY moon_count DESC;
```

---

## 📚 Context

Mandatory project for the freeCodeCamp **Relational Databases** certification, completed as part of my career transition into **Data Engineering**.
