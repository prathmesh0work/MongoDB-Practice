# MongoDB Practice

Practice queries covering core MongoDB operations in `mongosh` — CRUD,
querying, sorting/limiting, projections, embedded documents/arrays, and
aggregation with `$lookup` — across seven sample databases.

## What's inside

`mongodb-practice.js` is one file, split into seven clearly marked sections:

| # | Database | Focus |
|---|---|---|
| 1 | `movieDB` | `insertMany`/`insertOne`, `deleteMany`, `updateMany`, `$gt`, `$regex`, `$inc`, `sort`, `limit` |
| 2 | `companyDB` | `updateMany`, `updateOne`, `deleteMany`/`deleteOne`, `$or`, `countDocuments` |
| 3 | `deptDB` | projections, `sort` + `limit`, `forEach`, `$or` combined with `$in` |
| 4 | `sales` | `aggregate`, `$match`, `$lookup`, `$exists` |
| 5 | `libraryDB` | compound filters across two related collections |
| 6 | `hospitalDB` | array fields, querying arrays and scalars together |
| 7 | `blogsDB` | embedded documents, `$elemMatch`, `$or` inside `$elemMatch` |

## Running it

```bash
mongosh
> load('mongodb-practice.js')
```

Or copy individual sections into the shell — each one starts with a
`use <database>` line so it can be run independently of the others.

## Notes

- Each `insertMany`/`insertOne` block seeds fresh sample data, so sections
  are safe to re-run against a scratch database.
- A couple of small bugs from the original drafts are fixed here: the
  `hospitalDB` field name (`specilization` → `specialization`) and the
  `$lookup` in the `sales` section, where a field name mismatch
  (`invoiceId` vs `invoiceID`) meant the join never actually matched.
- The `blogsDB` section had a few syntax issues in the original draft: missing
  commas after `postedAt`, unquoted `date` values (`2019-10-22` parses as
  subtraction, not a date), `$elematch` → `$elemMatch`, and a stray `find([...])`
  using an array instead of an object — all fixed.
