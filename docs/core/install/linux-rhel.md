---
title: 在 RHEL-.NET Core 上安裝 .NET Core
description: 示範在 RHEL 上安裝 .NET Core SDK 和 .NET Core 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 4a406fe1834c16bab9a5548b69206b51270b33fa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324717"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a>在 RHEL 上安裝 .NET Core SDK 或 .NET Core 執行時間

RHEL 支援 .NET Core。 本文說明如何在 RHEL 上安裝 .NET Core。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>註冊您的 Red Hat 訂用帳戶

若要從 RHEL 上的 Red Hat 安裝 .NET Core，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。 如果未在您的系統上完成此動作，或您不確定，請參閱[.Net Core 的 Red Hat 產品檔](https://access.redhat.com/documentation/net_core/)。

## <a name="supported-distributions"></a>支援的發行版本

下表是 RHEL 7 和 RHEL 8 上目前支援的 .NET Core 版本清單。 在[.Net Core 版本達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)或已不再支援 RHEL 版本之前，會持續支援這些版本。

- ✔️表示仍然支援 RHEL 或 .NET Core 的版本。
- A ❌ 表示該 rhel 版本不支援 rhel 或 .Net Core 的版本。
- 當 RHEL 版本和 .NET Core 版本都✔️時，就會支援該作業系統和 .NET 組合。

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5 Preview （僅限手動安裝） |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#rhel-8-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |
| ✔️ [7](#rhel-7-) | ✔️2。1        | ✔️3。1        | ✔️ 5.0 Preview |

已不再支援下列 .NET Core 版本。 這些下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

請參閱[.Net core 的 Red Hat 檔](https://access.redhat.com/documentation/net_core/)，以瞭解安裝其他版本的 .net core 所需的步驟。

## <a name="rhel-8-"></a>RHEL 8 ✔️

.NET Core 包含在 RHEL 8 的應用程式資料流程存放庫中。

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a>RHEL 7 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

下列命令會安裝 `scl-utils` 套件：

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>安裝 SDK

.NET Core SDK 可讓您使用 .NET Core 開發應用程式。 如果您安裝 .NET Core SDK，就不需要安裝對應的執行時間。 若要安裝 .NET Core SDK，請執行下列命令：

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

Red Hat 不建議永久啟用 `rh-dotnet31` ，因為它可能會影響其他程式。 例如， `rh-dotnet31` 包含 `libcurl` 不同于基底 RHEL 版本的版本。 這可能會導致未預期不同版本的程式發生問題 `libcurl` 。 如果您想要 `rh-dotnet` 永久啟用，請將下列程式程式碼新增至 _~/.bashrc_檔案。

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a>安裝執行階段

.NET Core 執行時間可讓您執行使用 .NET Core 所建立且未包含執行時間的應用程式。 下列命令會安裝 ASP.NET Core 執行時間，這是適用于 .NET Core 的最相容執行時間。 在您的終端機中，執行下列命令。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

Red Hat 不建議永久啟用 `rh-dotnet31-aspnetcore-runtime-3.1` ，因為它可能會影響其他程式。 例如， `rh-dotnet31-aspnetcore-runtime-3.1` 包含 `libcurl` 不同于基底 RHEL 版本的版本。 這可能會導致未預期不同版本的程式發生問題 `libcurl` 。 如果您想要 `rh-dotnet31-aspnetcore-runtime-3.1` 永久啟用，請將下列程式程式碼新增至 _~/.bashrc_檔案。

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間： `rh-dotnet31-aspnetcore-runtime-3.1` 使用上述命令取代 `rh-dotnet31-dotnet-runtime-3.1` 。

## <a name="snap"></a>抓取

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>相依性

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>後續步驟

- [教學課程：使用 Visual Studio Code 建立具有 .NET Core SDK 的主控台應用程式](../tutorials/with-visual-studio-code.md)
