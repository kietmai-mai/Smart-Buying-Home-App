# Smart-Buying-Home-App
philly-heatmap/
│
├── README.md
├── LICENSE
├── .gitignore
├── .env.example
│
├── docs/                         # Architecture, diagrams, specs
│   ├── architecture/
│   │   ├── logical-architecture.md
│   │   ├── physical-architecture.md
│   │   └── diagrams/
│   │       ├── logical.mmd
│   │       └── physical.mmd
│   ├── data-dictionary.md
│   ├── scoring-model.md
│   └── api-spec.md
│
├── infrastructure/               # Infrastructure as Code
│   ├── terraform/
│   │   ├── modules/
│   │   │   ├── vpc/
│   │   │   ├── s3-datalake/
│   │   │   ├── aurora-postgres/
│   │   │   ├── databricks-workspace/
│   │   │   ├── api-gateway/
│   │   │   └── lambda/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   ├── outputs.tf
│   │   └── backend.tf
│   │
│   ├── cloudformation/           # Optional if using CFN
│   └── scripts/
│       ├── bootstrap.sh
│       └── deploy.sh
│
├── data-platform/                # Databricks + ETL logic
│   ├── notebooks/
│   │   ├── bronze/
│   │   │   ├── ingest_real_estate.py
│   │   │   ├── ingest_opa.py
│   │   │   ├── ingest_parcels.py
│   │   │   └── ingest_business_licenses.py
│   │   │
│   │   ├── silver/
│   │   │   ├── clean_properties.py
│   │   │   ├── geospatial_join.py
│   │   │   └── tenure_equity_calc.py
│   │   │
│   │   ├── gold/
│   │   │   ├── district_sales_aggregation.py
│   │   │   ├── hotness_score.py
│   │   │   └── ranked_leads.py
│   │   │
│   │   └── ml/
│   │       ├── feature_engineering.py
│   │       ├── train_model.py
│   │       └── evaluate_model.py
│   │
│   ├── pipelines/
│   │   ├── bronze_pipeline.yaml
│   │   ├── silver_pipeline.yaml
│   │   └── gold_pipeline.yaml
│   │
│   ├── schemas/
│   │   ├── bronze_schema.sql
│   │   ├── silver_schema.sql
│   │   └── gold_schema.sql
│   │
│   └── tests/
│       ├── test_data_quality.py
│       └── test_scoring.py
│
├── api/                          # Leads & subscription backend
│   ├── app/
│   │   ├── main.py               # FastAPI or Flask entrypoint
│   │   ├── config.py
│   │   ├── database.py
│   │   │
│   │   ├── routes/
│   │   │   ├── leads.py
│   │   │   ├── districts.py
│   │   │   ├── subscriptions.py
│   │   │   └── health.py
│   │   │
│   │   ├── services/
│   │   │   ├── scoring_service.py
│   │   │   ├── enrichment_service.py
│   │   │   └── crm_sync_service.py
│   │   │
│   │   └── models/
│   │       ├── lead.py
│   │       ├── district.py
│   │       └── subscription.py
│   │
│   ├── requirements.txt
│   └── Dockerfile
│
├── frontend/                     # Base44 / Web App integration
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   └── auth/
│   ├── public/
│   ├── package.json
│   └── README.md
│
├── crm-fabric/                   # Reverse ETL + Sync configs
│   ├── hightouch/
│   │   ├── leads_sync.yaml
│   │   └── subscriptions_sync.yaml
│   ├── airbyte/
│   └── dbt/
│       ├── models/
│       └── project.yml
│
├── analytics/                    # Tableau + Reporting
│   ├── tableau/
│   │   ├── police_district_heatmap.twb
│   │   └── sales_dashboard.twb
│   ├── sql/
│   │   ├── district_rollup.sql
│   │   └── lead_exports.sql
│   └── reports/
│
├── mlops/                        # Model serving & monitoring
│   ├── model_registry/
│   ├── batch_scoring/
│   ├── monitoring/
│   └── experiments/
│
├── tests/                        # End-to-end tests
│   ├── integration/
│   ├── api/
│   └── e2e/
│
└── scripts/
    ├── seed_database.py
    ├── backfill_24_months.py
    └── generate_sample_leads.py
