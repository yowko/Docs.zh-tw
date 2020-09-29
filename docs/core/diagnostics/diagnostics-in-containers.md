---
title: 收集容器中的診斷
description: 在本文中，您將瞭解如何在 Docker 容器中使用 .NET Core 診斷工具。
ms.date: 09/01/2020
ms.openlocfilehash: e57f3696433bbf6f35b2e3e5d1e72ae8b1e3eeb3
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91451086"
---
# <a name="collect-diagnostics-in-containers"></a>收集容器中的診斷

相同的診斷工具對於診斷其他案例中的 .NET Core 問題也適用于 Docker 容器。 不過，有些工具需要特殊的步驟才能在容器中工作。 本文涵蓋收集效能追蹤和收集傾印的工具，可用於 Docker 容器。

## <a name="using-net-core-cli-tools-in-a-container"></a>在容器中使用 .NET Core CLI 工具

**這些工具適用于：✔️** .net CORE 3.0 SDK 和更新版本

.Net Core 全域 CLI 診斷工具 ([`dotnet-counters`](dotnet-counters.md) 、、 [`dotnet-dump`](dotnet-dump.md) [`dotnet-gcdump`](dotnet-gcdump.md) 和 [`dotnet-trace`](dotnet-trace.md)) 設計成可在各種不同的環境中運作，而且應該全都直接在 Docker 容器中工作。 因此，在容器中) 的情況下，這些工具是收集以 .NET Core 3.0 或更新版本為目標之 .NET Core 案例的診斷資訊的慣用方法 (或3.1 或更新版本 `dotnet-gcdump` 。

在容器中使用這些工具時，唯一的最複雜的因素是它們會隨 .NET Core SDK 一起安裝，而許多 Docker 容器則會在沒有 .NET Core SDK 存在的情況下執行。 解決此問題的一個簡單解決方案是在初始 Docker 映射中安裝這些工具。 這些工具不需要執行 .NET Core SDK，只能進行安裝。 因此，您可以建立具有 [多階段組建](https://docs.docker.com/develop/develop-images/multistage-build/) 的 Dockerfile，以將工具安裝在組建階段 (其中 .NET Core SDK 存在) 然後將二進位檔複製到最後的映射。 這種方法的唯一缺點是 Docker 映射大小的增加。

```dockerfile
# In build stage
# Install desired .NET CLI diagnostics tools
RUN dotnet tool install --tool-path /tools dotnet-trace
RUN dotnet tool install --tool-path /tools dotnet-counters
RUN dotnet tool install --tool-path /tools dotnet-dump

...

# In final stage
# Copy diagnostics tools
WORKDIR /tools
COPY --from=build /tools .
```

或者，您也可以視需要在容器中安裝 .NET Core SDK，以便安裝 CLI 工具。 請注意，安裝 .NET Core SDK 將會影響重新安裝 .NET Core 執行時間的副作用。 因此，請務必安裝符合容器中存在之執行時間的 SDK 版本。

### <a name="using-net-core-global-cli-tools-in-a-sidecar-container"></a>在側車容器中使用 .NET Core 全域 CLI 工具

如果您想要使用 .NET Core 全域 CLI 診斷工具來診斷不同容器中的進程，請記住下列其他需求：

1. 容器必須 [共用進程命名空間](https://docs.docker.com/engine/reference/run/#pid-settings---pid) (以便側車容器中的工具可以存取目標容器) 中的進程。
2. .NET Core 全域 CLI 診斷工具需要存取 .NET Core 執行時間寫入/tmp 目錄的檔案，因此必須透過磁片區掛接，在目標和側車容器之間共用/tmp 目錄。 例如，藉由讓容器共用一般 [磁片](https://docs.docker.com/storage/volumes/#create-and-manage-volumes) 區或 Kubernetes [emptyDir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir) 磁片區，即可完成這項操作。 如果您嘗試在不共用/tmp 目錄的情況下，從側車容器使用診斷工具，您將會收到有關「未執行相容的 .NET 執行時間」處理常式的錯誤。

## <a name="using-perfcollect-in-a-container"></a>`PerfCollect`在容器中使用

**此工具適用于：✔️** .net Core 2.1 和更新版本

[`PerfCollect`](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/linux-performance-tracing.md)腳本有助於收集效能追蹤，而且是建議用來在 .Net Core 3.0 之前收集追蹤的工具。 如果 `PerfCollect` 在容器中使用，請記住下列需求：

1. `PerfCollect`需要 ([ `SYS_ADMIN` 功能](https://man7.org/linux/man-pages/man7/capabilities.7.html)才能執行 `perf` 工具) ，因此請確定容器是[以該功能啟動](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities)。
2. `PerfCollect` 需要先設定某些環境變數，才能開始進行程式碼剖析。 這些可以在 [Dockerfile](https://docs.docker.com/engine/reference/builder/#env) 中或在 [啟動容器](https://docs.docker.com/engine/reference/run/#env-environment-variables)時設定。 因為這些變數不應該在一般生產環境中設定，所以在啟動將會進行分析的容器時，通常只需新增這些變數。 PerfCollect 所需的兩個變數如下：
    1. COMPlus_PerfMapEnabled = 1
    1. COMPlus_EnableEventLog = 1

### <a name="using-perfcollect-in-a-sidecar-container"></a>`PerfCollect`在側車容器中使用

如果您想要 `PerfCollect` 在一個容器中執行，以分析不同容器中的 .Net Core 進程，除了這些差異之外，此體驗幾乎相同：

1. 先前所述的環境變數 (COMPlus_PerfMapEnabled 和 COMPlus_EnableEventLog) 必須針對目標容器設定， (不是執行中 `PerfCollect`) 的容器。
2. 執行的容器 `PerfCollect` 必須有 `SYS_ADMIN` (並非目標容器) 的功能。
3. 這兩個容器必須 [共用進程命名空間](https://docs.docker.com/engine/reference/run/#pid-settings---pid)。

## <a name="using-createdump-in-a-container"></a>`createdump`在容器中使用

**此工具適用于：✔️** .net Core 2.1 和更新版本

的替代方案 `dotnet-dump` [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) 可以用來在 Linux 上建立核心傾印，同時包含原生和受控資訊。 此 `createdump` 工具會與 .Net Core 執行時間一起安裝，並可在 libcoreclr.so 的旁邊找到， (通常位於 "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]" ) 。 此工具在容器中的運作方式與在非容器化 Linux 環境中的運作方式相同，唯一的例外是工具需要此[ `SYS_PTRACE` 功能](https://man7.org/linux/man-pages/man7/capabilities.7.html)，因此必須以[該功能啟動](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities)Docker 容器。

### <a name="using-createdump-in-a-sidecar-container"></a>`createdump`在側車容器中使用

如果您想要使用 `createdump` 從不同容器的進程建立傾印，除了下列差異之外，此體驗幾乎相同：

1. 執行的容器 `createdump` 必須有 `SYS_PTRACE` (並非目標容器) 的功能。
2. 這兩個容器必須 [共用進程命名空間](https://docs.docker.com/engine/reference/run/#pid-settings---pid)。
