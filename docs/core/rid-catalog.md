---
title: .NET 執行時間識別碼 (RID) 目錄
description: 深入瞭解執行時間識別碼 (RID) 以及如何在 .NET 中使用 Rid。
ms.date: 01/28/2021
ms.openlocfilehash: e5e1c4712965211b25a02b14a7cf2c91d74d8306
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216001"
---
# <a name="net-rid-catalog"></a>.NET RID 目錄

RID 是執行時間 *識別碼* 的縮寫。 RID 值是用來識別應用程式執行所在的目標平台。
.NET 套件會使用它們來代表 NuGet 套件中的平台特定資產。 下列值是 RID 的範例：`linux-x64`、`ubuntu.14.04-x64`、`win7-x64` 或 `osx.10.12-x64`。
針對具有原生相依性的套件，RID 也可指定能在哪些平台上還原套件。

單一 RID 可在您專案檔的 `<RuntimeIdentifier>` 元素中設定。 可以在專案檔的 `<RuntimeIdentifiers>` 元素中，將多個 RID 定義為以分號分隔的清單。 您也可以使用 `--runtime` 下列 [.net CLI 命令](./tools/index.md)透過選項來使用它們：

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

代表具體作業系統的 RID 通常遵循 `[os].[version]-[architecture]-[additional qualifiers]` 這個模式，其中：

- `[os]` 是作業/平台系統 Moniker。 例如： `ubuntu` 。

- `[version]` 是作業系統版本，使用以點分隔 (`.`) 的版本號碼表示。 例如： `15.10` 。

  - 版本 **不應為** 行銷版本，因為行銷版本通常代表作業系統的多個個別版本，且具有不同平台 API 介面區。

- `[architecture]` 處理器架構。 例如：`x86`、`x64`、`arm` 或 `arm64`。

- `[additional qualifiers]` 進一步區分不同平台。 例如：`aot`。

## <a name="rid-graph"></a>RID 圖表

RID 圖表或執行階段後援圖形是與彼此相容的 RID 清單。 RID 是在 [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) 套件中定義。 您可以在儲存機制中的檔案 [*runtime.js*](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json) 中，看到支援的 RID 和 RID 圖形清單 `dotnet/runtime` 。 在此檔案中，您可以看到所有 RID (基底項目除外) 都包含 `"#import"` 陳述式。 這些陳述式指出相容的 RID。

當 NuGet 還原套件時，它會嘗試尋找與所指定執行階段完全相符的項目。
若找不到完全相符的項目，NuGet 會返回到圖形，直到它根據 RID 圖形找到最接近的相容系統。

下列範例是 `osx.10.12-x64` RID 的實際項目：

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

上述 RID 指定 `osx.10.12-x64` 匯入 `osx.10.11-x64`。 因此，當 NuGet 還原套件時，它會嘗試在套件中尋找與 `osx.10.12-x64` 完全相符的項目。 例如，若 NuGet 找不到特定執行階段，它可以還原指定 `osx.10.11-x64` 執行階段的套件。

下列範例顯示也在 *runtime.json* 檔案中定義的稍大 RID 圖形：

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

所有的 RID 最終將對應至根 `any` RID。

處理 RID 時，您必須謹記一些考量：

- 請勿嘗試剖析 Rid 以取出元件部分。
- 不要以程式設計方式建置 RID。
- 使用已針對平台定義的 RID。
- RID 必須是特定的，因此不要假設實際 RID 值會怎樣。

## <a name="using-rids"></a>使用 RID

若要使用 RID，必須先了解有哪些 RID 存在。 新的值會定期新增至平台。
如需最新的完整版本，請[](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json)參閱存放庫中的 `dotnet/runtime` 檔案runtime.js。

可移植 Rid 是新增至 RID 圖形的值，不會系結至特定版本或 OS 散發套件。 這些是慣用的選擇，特別是在處理多個 Linux 散發版本時，因為大部分的散發 Rid 都對應到可移植 Rid。

下列清單顯示用於每個 OS 的一小部分最常見 RID。

## <a name="windows-rids"></a>Windows RID

僅列出常見值。 如需最新的完整版本，請[](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json)參閱存放庫中的 `dotnet/runtime` 檔案runtime.js。

- 可攜式
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- Windows 7/Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8.1/Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10/Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

如需詳細資訊，請參閱 .Net 相依性 [和需求](./install/windows.md#dependencies)。

## <a name="linux-rids"></a>Linux RID

僅列出常見值。 如需最新的完整版本，請[](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json)參閱存放庫中的 `dotnet/runtime` 檔案runtime.js。 如果下方未列出裝置執行的發行版本，裝置可能可以使用其中一個可攜式 RID。 例如，如果 Raspberry Pi 裝置執行未列出的 Linux 發行版本，則可以 `linux-arm` 為目標。

- 可攜式
  - `linux-x64` (大部分的桌面散發套件，例如 CentOS、Debian、Fedora、Ubuntu 和衍生) 
  - `linux-musl-x64` (使用 [musl](https://wiki.musl-libc.org/projects-using-musl.html) 的輕量發行版本，如 Alpine Linux)
  - `linux-arm` 在 ARM 上執行的 (Linux 散發套件，例如 Raspberry Pi 模型 2 +) 上的 Raspbian
  - `linux-arm64` 在 Raspberry Pi 模型 3 +) 上執行于64位 ARM 上的 (Linux 散發套件（如 Ubuntu Server 64 位）
- Red Hat Enterprise Linux
  - `rhel-x64` (RHEL 6 版以上已由 `linux-x64` 取代)
  - `rhel.6-x64`
- Tizen
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

如需詳細資訊，請參閱 .Net 相依性 [和需求](./install/linux.md)。

## <a name="macos-rids"></a>macOS RID

macOS RID 使用較舊的 "OSX" 商標。 僅列出常見值。 如需最新的完整版本，請[](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/pkg/runtime.json)參閱存放庫中的 `dotnet/runtime` 檔案runtime.js。

- 可攜式
  - `osx-x64` (最低 OS 版本為 macOS 10.12 Sierra)
- macOS 10.10  Yosemite
  - `osx.10.10-x64`
- macOS 10.11 El Capitan
  - `osx.10.11-x64`
- macOS 10.12 Sierra
  - `osx.10.12-x64`
- macOS 10.13 High Sierra
  - `osx.10.13-x64`
- macOS 10.14 Mojave
  - `osx.10.14-x64`
- macOS 10.15 Catalina
  - `osx.10.15-x64`
- macOS 11.01 Big Sur
  - `osx.11.0-x64`
  - `osx.11.0-arm64`

如需詳細資訊，請參閱 .Net 相依性 [和需求](./install/macos.md#dependencies)。

## <a name="see-also"></a>另請參閱

- [執行階段識別碼](https://github.com/dotnet/runtime/blob/master/src/libraries/Microsoft.NETCore.Platforms/readme.md)
