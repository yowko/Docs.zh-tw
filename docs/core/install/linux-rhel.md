---
title: 在 RHEL 上安裝 .NET-.NET
description: 示範在 RHEL 上安裝 .NET SDK 和 .NET 執行時間的各種方式。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 0b6138185bfd3e2f50c1b31e82779165715a5b6e
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851636"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a>在 RHEL 上安裝 .NET SDK 或 .NET 執行時間

RHEL 支援 .NET。 本文說明如何在 RHEL 上安裝 .NET。

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>註冊您的 Red Hat 訂用帳戶

若要在 RHEL 上從 Red Hat 安裝 .NET，您必須先使用 Red Hat 訂用帳戶管理員進行註冊。 如果未在您的系統上完成此操作，或如果您不確定，請參閱 [.net 的 Red Hat 產品檔](https://access.redhat.com/documentation/net/5.0/)。

## <a name="supported-distributions"></a>支援的發行版本

下表是 RHEL 7 和 RHEL 8 上目前支援的 .NET 版本清單。 除非 .Net 的版本 [達到終止支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 或已不再支援 RHEL 版本，否則仍支援這些版本。

- ✔️表示仍支援 RHEL 或 .NET 的版本。
- ❌表示該 rhel 版本不支援 rhel 或 .net 的版本。
- 當版本的 RHEL 和 .NET 版本都✔️時，支援該作業系統和 .NET 組合。

| RHEL                     | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#rhel-8-)        | ✔️2。1        | ✔️3。1        | ✔️5。0 |
| ✔️ [7](#rhel-7--net-50) | ✔️2。1        | ✔️ [3.1](#rhel-7--net-core-31)        | ✔️ [5.0](#rhel-7--net-50) |

不再支援下列 .NET 版本。 這些內容的下載仍會保持發佈：

- 3.0
- 2.2
- 2.0

## <a name="remove-preview-versions"></a>移除預覽版本

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a>如何安裝其他版本

請參閱 [.net 的 Red Hat 檔](https://access.redhat.com/documentation/net/5.0/) ，以瞭解安裝其他 .net 版本所需的步驟。

## <a name="rhel-8-"></a>RHEL 8 ✔️

.NET 包含在 RHEL 8 的應用程式資料流程存放庫中。

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a>RHEL 7 ✔️ .NET 5。0

下列命令會安裝 `scl-utils` 套件：

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>安裝 SDK

.NET SDK 可讓您使用 .NET 開發應用程式。 如果您安裝 .NET SDK，就不需要安裝對應的執行時間。 若要安裝 .NET SDK，請執行下列命令：

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

Red Hat 不建議永久啟用 `rh-dotnet50` ，因為它可能會影響其他程式。 如果您想要 `rh-dotnet` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a>安裝執行階段

.NET 執行時間可讓您執行以 .NET 建立的應用程式，而這些應用程式不包含執行時間。 下列命令會安裝 ASP.NET Core 執行時間，這是 .NET Core 最相容的執行時間。 在您的終端機中執行下列命令。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50 bash
```

Red Hat 不建議永久啟用 `rh-dotnet50` ，因為它可能會影響其他程式。 如果您想要 `rh-dotnet50` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。

```bash
source scl_source enable rh-dotnet50
```

除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET 執行時間： `rh-dotnet50-aspnetcore-runtime-5.0` 在上述命令中將取代為 `rh-dotnet50-dotnet-runtime-5.0` 。

## <a name="rhel-7--net-core-31"></a>RHEL 7 ✔️ .NET Core 3。1

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

Red Hat 不建議永久啟用 `rh-dotnet31` ，因為它可能會影響其他程式。 例如， `rh-dotnet31` 包含 `libcurl` 與基底 RHEL 版本不同的版本。 這可能會導致不預期不同版本的程式發生問題 `libcurl` 。 如果您想要 `rh-dotnet` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a>安裝執行階段

.NET Core 執行時間可讓您執行未包含執行時間的 .NET Core 所建立的應用程式。 下列命令會安裝 ASP.NET Core 執行時間，這是 .NET Core 最相容的執行時間。 在您的終端機中執行下列命令。

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

Red Hat 不建議永久啟用 `rh-dotnet31` ，因為它可能會影響其他程式。 例如， `rh-dotnet31` 包含 `libcurl` 與基底 RHEL 版本不同的版本。 這可能會導致不預期不同版本的程式發生問題 `libcurl` 。 如果您想要 `rh-dotnet31` 永久啟用，請將下列這一行新增至 _~/.bashrc_ 檔案。

```bash
source scl_source enable rh-dotnet31
```

除了 ASP.NET Core 執行時間之外，您還可以安裝不包含 ASP.NET Core 支援的 .NET Core 執行時間： `rh-dotnet31-aspnetcore-runtime-3.1` 在上述命令中將取代為 `rh-dotnet31-dotnet-runtime-3.1` 。

## <a name="snap"></a>單元

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>相依性

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a>腳本式安裝

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>手動安裝

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>後續步驟

- [教學課程：使用 .NET SDK 建立主控台應用程式 Visual Studio Code](../tutorials/with-visual-studio-code.md)
