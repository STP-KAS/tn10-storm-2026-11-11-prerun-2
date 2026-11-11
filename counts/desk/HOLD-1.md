MET

# HOLD-1, desk sender log, pre-run 2

> Counts only. The desk's sender log. It is not a chain count. Mini counts the chain.

Payment offer 1,013 tx/s at 150 sompi/gram, from 3 payment senders, one per kept public node. Families offer 1.2 hop/s, 16 families live, one family-sender process and one builder.

## Hop rate per cohort, as built

Floor (families 1–13): 100 sompi/gram per hop. Double (families 14–16): 200 sompi/gram per hop. The rate rides on each hop line to the one builder.

## Funding coins, as read from the desk node

The funding coins were not one size. Sizes seen, whole tKAS (coins): 33 (1,883), 34 (1,780), 32 (1,719), 35 (1,399), 31 (1,340), 36 (1,078), 37 (749), 30 (621), 38 (445), 39 (275), 40 (162), 28 (71), and 67 more sizes. The fee is not called the whole cause.

## Minutes

| Minute (UTC) | Pay submit-OK | Attempts | Rejects, rate | Rejects, full | Other | Floor OK / att / rate rej / full rej / waiting | Double OK / att / rate rej / full rej / waiting | Clean |
|---|---:|---:|---:|---:|---:|---|---|---|
| 2026-11-11T15:15 | 59,767 | 59,767 | 0 | 0 | 0 | 531 / 1087 / 0 / 0 / 13 | 147 / 260 / 0 / 0 / 3 | yes |
| 2026-11-11T15:16 | 59,767 | 59,767 | 0 | 0 | 0 | 439 / 1059 / 0 / 0 / 13 | 131 / 259 / 0 / 0 / 3 | yes |
| 2026-11-11T15:17 | 59,767 | 59,767 | 0 | 0 | 0 | 463 / 1081 / 0 / 0 / 13 | 128 / 255 / 0 / 0 / 2 | yes |

Within 10 percent means 54,702 to 66,858 submit-OK in the minute.

## Public nodes (local numbers)

Kept: 1, 4, 5. The family sender is on node 1. Both cohorts share that node.

| Node | Synced every sample | Last DAA | Pay submit-OK | Pay rejects | Dropped sockets | Answer ms, median |
|---:|---|---:|---:|---:|---:|---:|
| 1 | yes | 620740916 | 59,826 | 0 | 0 | 54 |
| 4 | yes | 620740916 | 59,826 | 0 | 0 | 51 |
| 5 | yes | 620740916 | 59,649 | 0 | 0 | 46 |

## Hop submit to landing, per cohort

| Cohort | Landed of OK | Median ms | Slow tail (p95) ms |
|---|---:|---:|---:|
| floor | 1433 of 1433 | 1223 | 2896 |
| double | 406 of 406 | 1061 | 2305 |

Landing is the accepting block header time the desk's coordinator read. Waiting is submitted-OK not yet landed at the minute's end.
