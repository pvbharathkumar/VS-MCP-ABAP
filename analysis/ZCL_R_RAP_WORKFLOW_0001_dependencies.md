ZCL_R_RAP_WORKFLOW_0001 - Dependency Map
flowchart TD

    A[ZCL_R_RAP_WORKFLOW_0001]

    A --> B[SAP Workflow API]
    B --> B1[CL_SWF_CPWF_API_FACTORY_A4C]
    B --> B2[IF_SWF_CPWF_API]
    B --> B3[IF_SWF_CPWFCALLBACK]
    B --> B4[CX_SWF_CPWF_API]

    A --> C[ZTRAVEL001]
    C --> C1[Travel ID to UUID Lookup]

    A --> D[ZR_TRAVEL000]
    D --> D1[RAP Travel Entity]
    D --> D2[Status Update]

    D --> E[ZBP_R_TRAVEL000]
    E --> E1[RAP Behavior Implementation]

    D --> F[ZTRAVEL_D]
    F --> F1[RAP Draft Table]

    D --> G[ZC_TRAVEL000]
    G --> H[ZUI_TRAVEL_O4]
    H --> I[ZUI_TRAVEL000_O4]

    A --> J[Workflow Context]
    J --> J1[CONTEXT]
    J --> J2[TYPE_CONTEXT]
    J --> J3[CALLBACK_CONTEXT]