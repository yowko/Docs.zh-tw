---
title: 卸載工具
description: 介紹 .NET Core 卸載工具，這是可讓您以 .NET Core Sdk 和執行時間進行受控制清除的引導式工具。
author: sfoslund
ms.date: 05/27/2020
ms.openlocfilehash: ed43b4ec8437ae0ccaf5f1234758dda9f16bd51e
ms.sourcegitcommit: 4f5f1855849cb02c3b610c7006ac21d7429f3348
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98235348"
---
# <a name="net-core-uninstall-tool"></a>.NET Core 解除安裝工具

[.Net Core 卸載工具](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) 可讓您從系統移除 .net Core sdk 和執行時間。 選項的集合可以用來指定您要卸載的版本。

此工具支援 Windows 和 macOS。 目前不支援 Linux。

在 Windows 中，此工具只能卸載使用下列其中一個安裝程式所安裝的 Sdk 和執行時間：

- .NET Core SDK 與執行時間安裝程式。
- Visual Studio 2019 16.3 版之前的版本 Visual Studio 安裝程式。

在 macOS 上，工具只能卸載位於 */usr/local/share/dotnet* 資料夾中的 sdk 和執行時間。

由於有這些限制，因此工具可能無法卸載電腦上的所有 .NET Core Sdk 和執行時間。 您可以使用 `dotnet --info` 命令來尋找已安裝的所有 .Net Core sdk 和執行時間，包括這項工具無法移除的 sdk 和執行時間。 此 `dotnet-core-uninstall list` 命令會顯示哪些 sdk 可以使用工具來卸載。 1.2 和更新版本可以卸載5.0 版或更早版本的 Sdk 和執行時間，而舊版工具可以卸載3.1 和更早版本。

## <a name="install-the-tool"></a>安裝工具

您可以從 [工具的 [版本] 頁面](https://aka.ms/dotnet-core-uninstall-tool) 下載 .Net Core 卸載工具，並在 [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub 存放庫中尋找原始程式碼。

> [!NOTE]
> 此工具需要提高許可權，才能卸載 .NET Core Sdk 和執行時間。 因此，它應該安裝在受寫入保護的目錄中，例如 Windows 上的 *C:\Program* 檔案或 macOS 上的 */usr/local/bin* 。 另請參閱更 [高的 dotnet 命令存取權](../tools/elevated-access.md)。 如需詳細資訊，請參閱 [詳細的安裝指示](https://aka.ms/dotnet-core-uninstall-tool)。

## <a name="run-the-tool"></a>執行工具

下列步驟顯示執行卸載工具的建議方法：

- [步驟 1-顯示已安裝的 .NET Core Sdk 和執行時間](#step-1---display-installed-net-core-sdks-and-runtimes)
- [步驟 2-執行試執行](#step-2---do-a-dry-run)
- [步驟 3-卸載 .NET Core Sdk 和執行時間](#step-3---uninstall-net-core-sdks-and-runtimes)
- [步驟 4-刪除 NuGet fallback 資料夾 (選用) ](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>步驟 1-顯示已安裝的 .NET Core Sdk 和執行時間

此 `dotnet-core-uninstall list` 命令會列出已安裝的 .Net Core sdk 和執行時間，可使用此工具移除。 Visual Studio 可能需要某些 Sdk 和執行時間，而且會顯示這些 Sdk 和執行時間，並說明為何不建議將其卸載。

> [!NOTE]
> `dotnet-core-uninstall list`在大部分情況下，命令的輸出不會符合的輸出中已安裝版本的清單 `dotnet --info` 。 具體而言，此工具不會顯示 zip 檔案所安裝或受 Visual Studio 管理的版本 (Visual Studio 2019 16.3 或更新版本) 安裝的任何版本。 檢查版本是否受 Visual Studio 管理的其中一種方式是在中加以查看 `Add or Remove Programs` ，其中 Visual Studio 的 managed 版本會標示為其顯示名稱。

**dotnet-核心-卸載清單**

#### <a name="synopsis"></a>概要

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>選項

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  列出所有可以使用此工具卸載的 ASP.NET Core 執行時間。

* **`--hosting-bundle`**

  列出可以使用此工具卸載的所有 .NET Core 裝載套件組合。

* **`--runtime`**

  列出可以使用此工具卸載的所有 .NET Core 執行時間。

* **`--sdk`**

  列出可以使用此工具卸載的所有 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細程度層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`--x64`**

  列出可以使用此工具卸載的所有 x64 .NET Core Sdk 和執行時間。

* **`--x86`**

  列出可以使用此工具卸載的所有 x86 .NET Core Sdk 和執行時間。

## <a name="macos"></a>[macOS](#tab/macos)

* **`--runtime`**

  列出可以使用此工具卸載的所有 .NET Core 執行時間。

* **`--sdk`**

  列出可以使用此工具卸載的所有 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細程度層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。
  
---

#### <a name="examples"></a>範例

* 列出可以使用此工具移除的所有 .NET Core Sdk 和執行時間：

  ```console
  dotnet-core-uninstall list
  ```

* 列出所有 x64 .NET Core Sdk 和執行時間：

  ```console
  dotnet-core-uninstall list --x64
  ```

* 列出所有 x86 .NET Core Sdk：

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>步驟 2-執行試執行

`dotnet-core-uninstall dry-run`和 `dotnet-core-uninstall whatif` 命令會顯示 .Net Core sdk 和執行時間，這些 sdk 和執行時間會根據提供的選項而移除，而不需執行卸載。 這些命令是同義字。

**dotnet-核心-卸載試執行和 dotnet 核心-卸載 whatif**

#### <a name="synopsis"></a>概要

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>引數

* **`VERSION`**

  要卸載的指定版本。 您可以列出多個版本，並以空格分隔。 也支援回應檔。

  > [!TIP]
  > 回應檔是在命令列上放置所有版本的替代方法。
  > 它們是文字檔，通常 \* 會使用 .rsp 副檔名，而且每個版本都會列在個別的行上。
  > 若要指定引數的回應檔 `VERSION` ，請使用 \@ 緊接在回應檔名稱後面的字元。

#### <a name="options"></a>選項

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  移除所有 .NET Core Sdk 和執行時間。

* **`--all-below <VERSION>[ <VERSION>...]`**

  只會移除版本小於指定版本的 .NET Core Sdk 和執行時間。 指定的版本仍會保持安裝。

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  除了指定的版本之外，移除所有 .NET Core Sdk 和執行時間。

* **`--all-but-latest`**

  移除最高版本以外的 .NET Core Sdk 和執行時間。

* **`--all-lower-patches`**

  移除較高修補程式所取代的 .NET Core Sdk 和執行時間。 此選項可保護上的 global.js。

* **`--all-previews`**

  移除標記為預覽版的 .NET Core Sdk 和執行時間。

* **`--all-previews-but-latest`**

  移除標記為預覽版的 .NET Core Sdk 和執行時間，但最高預覽版除外。

* **`--aspnet-runtime`**

  只移除 ASP.NET Core 執行時間。

* **`--hosting-bundle`**

  只會移除 .NET Core 執行時間和裝載套件組合。

* **`--major-minor <MAJOR_MINOR>`**

  移除符合指定版本的 .NET Core Sdk 和執行時間 `major.minor` 。

* **`--runtime`**

  僅移除 .NET Core 執行時間。

* **`--sdk`**

  僅移除 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細程度層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`--x64`**

  必須搭配 `--sdk` 、和使用， `--runtime` `--aspnet-runtime` 才能移除 x64 sdk 或執行時間。

* **`--x86`**

  必須搭配 `--sdk` 、和使用， `--runtime` `--aspnet-runtime` 才能移除 x86 sdk 或執行時間。

* **`--force`** 強制移除 Visual Studio 可能使用的版本。

注意：

1. 只需要、、和的其中一個 `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` 。
2. `--all`、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` 和 `[<VERSION>...]` 是專屬的。
3. 如果 `--x64` `--x86` 指定或未指定，則會移除 x64 和 x86。

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  移除所有 .NET Core Sdk 和執行時間。

* **`--all-below <VERSION>[ <VERSION>...]`**

  移除低於指定版本的 .NET Core Sdk 和執行時間。 指定的版本將會保留。

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  移除 .NET Core Sdk 和執行時間，但指定的版本除外。

* **`--all-but-latest`**

  移除最高版本以外的 .NET Core Sdk 和執行時間。

* **`--all-lower-patches`**

  移除較高修補程式所取代的 .NET Core Sdk 和執行時間。 此選項可保護上的 global.js。

* **`--all-previews`**

  移除標記為預覽版的 .NET Core Sdk 和執行時間。

* **`--all-previews-but-latest`**

  移除標記為預覽版的 .NET Core Sdk 和執行時間，但最高預覽版除外。

* **`--major-minor <MAJOR_MINOR>`**

  移除符合指定版本的 .NET Core Sdk 和執行時間 `major.minor` 。

* **`--runtime`**

  僅移除 .NET Core 執行時間。

* **`--sdk`**

  僅移除 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細程度層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。
  
* **`--force`** 強制移除 Visual Studio 或 Sdk 可能使用的版本。

注意：

1. 只有其中一個 `--sdk` `--runtime` 是必要的。
2. `--all`、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` 和 `[<VERSION>...]` 是專屬的。

---

#### <a name="examples"></a>範例

> [!NOTE]
> 根據預設，Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間不會包含在 `dotnet-core-uninstall dry-run` 輸出中。 在下列範例中，某些指定的 Sdk 和執行時間可能不會包含在輸出中，視機器的狀態而定。 若要包含所有 Sdk 和執行時間，請將它們明確地列為引數，或使用 `--force` 選項。

* 移除已被較高修補程式取代的所有 .NET Core 執行時間的試執行：

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* 正在將所有 .NET Core Sdk 的版本移除，以進行移除 `2.2.301` ：

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>步驟 3-卸載 .NET Core Sdk 和執行時間

`dotnet-core-uninstall remove` 卸載選項組合指定的 .NET Core Sdk 和執行時間。 1.2 和更新版本可以卸載5.0 版或更早版本的 Sdk 和執行時間，而舊版工具可以卸載3.1 和更早版本。

因為此工具具有破壞性行為， **強烈** 建議您在執行 [移除] 命令之前執行試執行。 試執行會顯示當您使用命令時，將會移除哪些 .NET Core Sdk 和執行時間 `remove` 。 請參閱 [我是否應該移除版本？](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) 以瞭解可安全移除哪些 sdk 和執行時間。

> [!CAUTION]
> 請記住下列注意事項：
>
>- 這項工具可以卸載電腦上的檔案所需的 .NET Core SDK 版本 `global.json` 。 您可以從 [ [下載 .Net core](https://dotnet.microsoft.com/download/dotnet-core) ] 頁面重新安裝 .Net core sdk。
>- 這項工具可以卸載電腦上 framework 相依應用程式所需的 .NET Core 執行時間版本。 您可以從 [ [下載 .Net core](https://dotnet.microsoft.com/download/dotnet-core) ] 頁面重新安裝 .net core 執行時間。
>- 這項工具可以卸載 Visual Studio 依賴的 .NET Core SDK 和執行階段版本。 如果您中斷 Visual Studio 安裝，請在 Visual Studio 安裝程式中執行 [修復]，以回到工作狀態。

根據預設，所有命令都會保留 Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間。 您可以將這些 Sdk 和執行時間明確地列為引數或使用選項，以卸載這些 Sdk 和執行時間 `--force` 。

此工具需要提高許可權，才能卸載 .NET Core Sdk 和執行時間。 在 Windows 上和使用 macOS 上的系統管理員命令提示字元中執行此工具 `sudo` 。 `dry-run`和 `whatif` 命令不需要提高許可權。

**dotnet-核心-卸載移除**

#### <a name="synopsis"></a>概要

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>引數

* **`VERSION`**

  要卸載的指定版本。 您可以列出多個版本，並以空格分隔。 也支援回應檔。

  > [!TIP]
  > 回應檔是在命令列上放置所有版本的替代方法。
  > 它們是文字檔，通常 \* 會使用 .rsp 副檔名，而且每個版本都會列在個別的行上。
  > 若要指定引數的回應檔 `VERSION` ，請使用 \@ 緊接在回應檔名稱後面的字元。

#### <a name="options"></a>選項

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  移除所有 .NET Core Sdk 和執行時間。

* **`--all-below <VERSION>[ <VERSION>...]`**

  只會移除版本小於指定版本的 .NET Core Sdk 和執行時間。 指定的版本仍會保持安裝。

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  除了指定的版本之外，移除所有 .NET Core Sdk 和執行時間。

* **`--all-but-latest`**

  移除最高版本以外的 .NET Core Sdk 和執行時間。

* **`--all-lower-patches`**

  移除較高修補程式所取代的 .NET Core Sdk 和執行時間。 此選項可保護上的 global.js。

* **`--all-previews`**

  移除標記為預覽版的 .NET Core Sdk 和執行時間。

* **`--all-previews-but-latest`**

  移除標記為預覽版的 .NET Core Sdk 和執行時間，但最高預覽版除外。

* **`--aspnet-runtime`**

  只移除 ASP.NET Core 執行時間。

* **`--hosting-bundle`**

  只會移除 .NET Core 裝載套件組合。

* **`--major-minor <MAJOR_MINOR>`**

  移除符合指定版本的 .NET Core Sdk 和執行時間 `major.minor` 。

* **`--runtime`**

  僅移除 .NET Core 執行時間。

* **`--sdk`**

  僅移除 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細程度層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`--x64`**

  必須搭配 `--sdk` 、和使用， `--runtime` `--aspnet-runtime` 才能移除 x64 sdk 或執行時間。

* **`--x86`**

  必須搭配 `--sdk` 、和使用， `--runtime` `--aspnet-runtime` 才能移除 x86 sdk 或執行時間。

* **`-y, --yes`** 執行命令，而不需要進行 [是] 或 [否] 確認。

* **`--force`** 強制移除 Visual Studio 可能使用的版本。

注意：

1. 只需要、、和的其中一個 `--sdk` `--runtime` `--aspnet-runtime` `--hosting-bundle` 。
2. `--all`、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` 和 `[<VERSION>...]` 是專屬的。
3. 如果 `--x64` `--x86` 指定或未指定，則會移除 x64 和 x86。

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  移除所有 .NET Core Sdk 和執行時間。

* **`--all-below <VERSION>[ <VERSION>...]`**

  移除低於指定版本的 .NET Core Sdk 和執行時間。 指定的版本將會保留。

* **`--all-but <VERSIONS>[ <VERSION>...]`**

  移除 .NET Core Sdk 和執行時間，但指定的版本除外。

* **`--all-but-latest`**

  移除最高版本以外的 .NET Core Sdk 和執行時間。

* **`--all-lower-patches`**

  移除較高修補程式所取代的 .NET Core Sdk 和執行時間。 此選項可保護上的 global.js。

* **`--all-previews`**

  移除標記為預覽版的 .NET Core Sdk 和執行時間。

* **`--all-previews-but-latest`**

  移除標記為預覽版的 .NET Core Sdk 和執行時間，但最高預覽版除外。

* **`--major-minor <MAJOR_MINOR>`**

  移除符合指定版本的 .NET Core Sdk 和執行時間 `major.minor` 。

* **`--runtime`**

  僅移除 .NET Core 執行時間。

* **`--sdk`**

  僅移除 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細程度層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`-y, --yes`** 執行命令，而不需要進行 Y/N 確認。
  
* **`--force`** 強制移除 Visual Studio 或 Sdk 可能使用的版本。

注意：

1. 只有其中一個 `--sdk` `--runtime` 是必要的。
2. `--all`、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` 和 `[<VERSION>...]` 是專屬的。

---

#### <a name="examples"></a>範例

> [!NOTE]
> 根據預設，會保留 Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間。 在下列範例中，某些指定的 Sdk 和執行時間可能會保留，視機器的狀態而定。 若要移除所有 Sdk 和執行時間，請將它們明確地列為引數，或使用 `--force` 選項。

* 移除版本以外的所有 .NET Core 執行時間， `3.0.0-preview6-27804-01` 而不需要確認 Y/N：

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* 移除所有 .NET Core 1.1 Sdk，而不需要進行 Y/n 確認：

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* 移除沒有主控台輸出的 .NET Core 1.1.11 SDK：

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* 移除此工具可以安全移除的所有 .NET Core Sdk：

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* 移除此工具可以移除的所有 .NET Core Sdk，包括 Visual Studio (不建議) 所需的 Sdk：

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* 移除回應檔案中指定的所有 .NET Core Sdk `versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  *版本* 的內容如下所示：
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>步驟 4-刪除 NuGet fallback 資料夾 (選用) 

在某些情況下，您不再需要， `NuGetFallbackFolder` 而且可能想要刪除它。 如需刪除此資料夾的詳細資訊，請參閱 [移除 NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)。

## <a name="uninstall-the-tool"></a>卸載工具

## <a name="windows"></a>[Windows](#tab/windows)

1. 開啟 [新增或移除程式]。
2. 搜尋 `Microsoft .NET Core SDK Uninstall Tool`。
3. 選取 [解除安裝]。

## <a name="macos"></a>[macOS](#tab/macos)

從其安裝所在的目錄中刪除下載的 *dotnet-core-uninstall gz* 檔案。 如果您將此檔案的內容解壓縮到另一個目錄中，也請務必刪除該內容。

---
