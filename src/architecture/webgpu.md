# WebGPU*

WebGPU implementation is powered by wgpu(-core).

## Architecture

```mermaid
flowchart TB
    subgraph Content Process
    Script[Script Thread]
    end

    subgraph Main Process
    direction TB
    WGPU--token(), wake()-->poller[WGPU poller]
    poller---->WGPU poller
    WGPU-->WebRender
    WGPU-->Constellation
    end

    Constellation<-->Script
    WGPU-->Script
    WGPU-->Script
```

WGPU and WGPU poller thread live in components/webgpu and