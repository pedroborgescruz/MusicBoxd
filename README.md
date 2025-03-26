# MusicBoxd
RYM, AOTY, and others are shit. So I decided to create my own rating platform and community for music.

```mermaid
flowchart TD
  subgraph Clients
    A["Web Client (React/Next.js)"]
    B["Mobile Client (React Native/Flutter)"]
  end

  subgraph Edge
    C["CDN & DNS"]
    D["Load Balancer"]
  end

  subgraph API_Gateway [API Gway / Reverse Proxy]
    E["API Gateway"]
  end

  subgraph Backend_Services [Backend / App]
    F["Authentication Service"]
    G["User Service"]
    H["Music Data Service"]
    I["Review & Rating Service"]
    J["Social Interaction Service"]
    K["Notification Service (WebSockets)"]
  end

  subgraph Data_Layer [Data Storage & Caching]
    L[(Relational DB - PostgreSQL)]
    M[(Cache - Redis)]
    N[(Search Engine - Elasticsearch)]
  end

  subgraph External_Integrations [External Music Data APIs]
    O["Spotify API"]
  end

  %% Connections from Clients to Edge
  A --> C
  B --> C
  C --> D
  D --> E

  %% API Gateway to Backend Services
  E --> F
  E --> G
  E --> H
  E --> I
  E --> J
  E --> K

  %% Services to Data Layer
  F --> L
  G --> L
  H --> L
  I --> L
  J --> L
  K --> L

  %% Caching and Search Integration
  F --> M
  G --> M
  I --> M
  I --> N

  %% Music Data Service interacts with external APIs
  H --> O
