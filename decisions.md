# Decisions log

One line per decision. Fill in "Rows affected" from the notebook output.

| # | Step | Decision | Reason | Rows affected | Who / date |
|---|------|----------|--------|---------------|------------|
| 1 | Loading | Use the raw Kaggle file unchanged in `data/raw/` | Reproducibility | – | |
| 2 | Clustering | Group hosts, not listings | Hosts are Airbnb's customers (Ahmed) | 37,457 hosts | Fedi, 11 Nov 2026 |
| 3 | Clustering | Drop hosts without `median_min_nights` | All their listings were over 365 nights and removed in cleaning; k-means can't use empty values | 13 hosts dropped, 37,444 kept | Fedi, 11 Nov 2026 |
| 4 | Clustering | Build the groups from log listing count, log minimum stay, share of entire homes and average availability. No price, no reviews | Groups describe how hosts run their listings; price only describes the groups after (team rule) | – | Fedi, 11 Nov 2026 |
| 5 | Clustering | Leave out `n_neighbourhood_groups` | 99.7% of hosts are in one borough, so it can't separate hosts | – | Fedi, 11 Nov 2026 |
| 6 | Clustering | Use `avg_availability`, not `share_zero_availability` | The 0/1 version scores higher (silhouette 0.52 vs 0.46) but only rebuilds the yes/no combinations | – | Fedi, 11 Nov 2026 |
| 7 | Clustering | K-means with k = 7, seed 42 | Silhouette peaks at 7 (0.484); same groups with 4 seeds (ARI 1.0); first k where the 115 hosts with 10+ listings get their own group | 37,444 hosts in 7 types | Fedi, 12 Nov 2026 |
| 8 | Clustering | Compare with a rule-based baseline (7 groups) | Rules explain 24.7% of price variation vs 23.0% for k-means: k-means' value is finding the types; the real test is the price gaps | – | Fedi, 12 Nov 2026 |
| 9 | Clustering | DBSCAN not used | Results swing with eps: 15 groups and 12% noise at 0.3, 10 groups with one holding 41% at 0.5 | 10,000-host sample | Fedi, 11 Nov 2026 |
| 10 | Clustering | Group names say "not available", not "inactive" | The data can't tell fully booked from switched off | 22,692 hosts (2 groups) | Fedi, 12 Nov 2026 |
