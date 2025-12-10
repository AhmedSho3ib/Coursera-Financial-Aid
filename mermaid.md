
# Project Data Quality Flow

```mermaid
flowchart TD
    A[RAW ACTIVITY DATA<br>• Energy/Fuel/Distance<br>• Reported_at/Date<br>• Location/Region<br>• Technology type<br>• Source Physical/Service] --> B[Merge Source Axes (Guide 1)<br>• Compute source_quality_score<br>• Generate source_tags metadata]

    B --> C[Technical Data Quality Engine (DQS)<br>• Schema validation<br>• Completeness<br>• Format / Type / Range checks<br>• Output: dqs_final_score + label]

    B --> D[GHG Representativeness Engine (Guide 2)<br>• 5D scoring:<br>-- Source Quality (from merged)<br>-- Location<br>-- Age<br>-- Technology<br>-- Completeness<br>• Aggregate to radar chart + label]

    C --> E[Combine Results<br>• Keep DQS and GHG scores separate<br>• Prepare final_quality_summary]

    D --> E

    E --> F[FINAL QUALITY OBJECT<br>• activity_data (original + merged)<br>• source_quality_score / tags<br>• dqs_engine (scores + label)<br>• ghg_engine (5D + label)<br>• final_quality_summary]

    style A fill:#f9f,stroke:#333,stroke-width:1px
    style B fill:#bbf,stroke:#333,stroke-width:1px
    style C fill:#bfb,stroke:#333,stroke-width:1px
    style D fill:#ffb,stroke:#333,stroke-width:1px
    style E fill:#fbf,stroke:#333,stroke-width:1px
    style F fill:#aff,stroke:#333,stroke-width:2px
```
