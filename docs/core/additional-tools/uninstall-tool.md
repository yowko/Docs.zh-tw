---
title: 卸載工具
description: .NET 核心卸載工具的概述，該工具是一種引導式工具，可控制清理 .NET 核心 SDK 和運行時。
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: bd20cba133cbb754dcca48e48b76a391a9efacba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847012"
---
# <a name="net-core-uninstall-tool"></a>.NET Core 解除安裝工具

[.NET 核心卸載工具](https://aka.ms/dotnet-core-uninstall-tool)（`dotnet-core-uninstall`） 允許您從系統中刪除 .NET 核心 SDK 和運行時。 選項組合可用於指定要卸載的版本。

該工具支援 Windows 和 macOS。 目前不支援 Linux。

在 Windows 上，該工具只能卸載使用以下安裝程式之一安裝的 SDK 和運行時：

- .NET 核心 SDK 和運行時安裝程式。
- Visual Studio 安裝程式的版本早于 Visual Studio 2019 版本 16.3。

在 macOS 上，該工具只能卸載*位於 /usr/local/share/dotnet*資料夾中的 SDK 和運行時。

由於這些限制，該工具可能無法在電腦上卸載所有 .NET Core SDK 和運行時。 可以使用 該`dotnet --info`命令查找已安裝的所有 .NET 核心 SDK 和運行時，包括此工具無法刪除的 SDK 和運行時。 該`dotnet-core-uninstall list`命令顯示可以使用該工具卸載哪些 SDK。

## <a name="install-the-tool"></a>安裝工具

您可以[在此處](https://aka.ms/dotnet-core-uninstall-tool)下載 .NET 核心卸載工具，並在[dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub 存儲庫中找到原始程式碼。

> [!NOTE]
> 該工具需要提升才能卸載 .NET 核心 SDK 和運行時。 因此，它應安裝在受寫入保護的目錄中，如 Windows 上的*C：*程式檔*或 macOS 上的 */usr/local/bin。* 另請參閱[點網命令的提升訪問](../tools/elevated-access.md)。 有關詳細資訊，請參閱[詳細的安裝說明](https://aka.ms/dotnet-core-uninstall-tool)。

## <a name="run-the-tool"></a>執行工具

以下步驟顯示了運行卸載工具的建議方法：

- [步驟 1 - 顯示已安裝的 .NET 核心 SDK 和運行時](#step-1---display-installed-net-core-sdks-and-runtimes)
- [第 2 步 - 進行幹跑](#step-2---do-a-dry-run)
- [步驟 3 - 卸載 .NET 核心 SDK 和運行時](#step-3---uninstall-net-core-sdks-and-runtimes)
- [步驟 4 - 刪除 NuGet 回退資料夾（可選）](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>步驟 1 - 顯示已安裝的 .NET 核心 SDK 和運行時

該`dotnet-core-uninstall list`命令列出了可使用此工具刪除的已安裝的 .NET Core SDK 和運行時。 Visual Studio 可能需要某些 SDK 和運行時，並且顯示它們時會記下為什麼不建議卸載它們。

**點網核心卸載清單**

#### <a name="synopsis"></a>概要

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>選項。

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  列出可以使用此工具卸載的所有ASP.NET核心運行時。

* **`--hosting-bundle`**

  列出可以使用此工具卸載的所有 .NET Core 運行時和託管包。

* **`--runtime`**

  列出可以使用此工具卸載的所有 .NET 核心運行時。

* **`--sdk`**

  列出可以使用此工具卸載的所有 .NET 核心 SDK。

* **`-v, --verbosity <LEVEL>`**

  設置詳細程度級別。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`--x64`**

  列出可以使用此工具卸載的所有 x64 .NET 核心 SDK 和運行時。

* **`--x86`**

  列出可以使用此工具卸載的所有 x86 .NET 核心 SDK 和運行時。

## <a name="macos"></a>[macOS](#tab/macos)

* **`--runtime`**

  列出可以使用此工具卸載的所有 .NET 核心運行時。

* **`--sdk`**

  列出可以使用此工具卸載的所有 .NET 核心 SDK。

* **`-v, --verbosity <LEVEL>`**

  設置詳細程度級別。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。
  
---

#### <a name="examples"></a>範例

* 列出可以使用此工具刪除的所有 .NET 核心 SDK 和運行時：

  ```console
  dotnet-core-uninstall list
  ```

* 列出所有 x64 .NET 核心 SDK 和運行時：

  ```console
  dotnet-core-uninstall list --x64
  ```

* 列出所有 x86 .NET 核心 SDK：

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>第 2 步 - 進行幹跑

`dotnet-core-uninstall dry-run`和`dotnet-core-uninstall whatif`命令顯示 .NET Core SDK 和運行時，將根據提供的選項在不執行卸載的情況下刪除這些選項。 這些命令是同義字。

**點網-核心卸載幹運行和點網核心卸載什麼**

#### <a name="synopsis"></a>概要

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>引數

* **`VERSION`**

  要卸載的指定版本。 您可以逐個列出多個版本，由空格分隔。 還支援回應檔。

  > [!TIP]
  > 回應檔是將所有版本放在命令列上的替代方法。
  > 它們是文字檔，通常帶有\*.rsp 副檔名，每個版本都列在單獨的行上。
  > 要為`VERSION`參數指定回應檔，請使用該\@字元，緊跟回應檔案名。

#### <a name="options"></a>選項。

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  刪除所有 .NET 核心 SDK 和運行時。

* **`--all-below <VERSION>`**

  僅刪除版本小於指定版本的 .NET Core SDK 和運行時。 指定的版本將保持安裝狀態。

* **`--all-but <VERSIONS>`**

  刪除所有 .NET 核心 SDK 和運行時，但指定的版本除外。

* **`--all-but-latest`**

  刪除 .NET 核心 SDK 和運行時，但一個最高版本除外。

* **`--all-lower-patches`**

  刪除 .NET 核心 SDK，運行時被較高的修補程式取代。 此選項保護全域.json。

* **`--all-previews`**

  刪除 .NET 核心 SDK 和標記為預覽的運行時。

* **`--all-previews-but-latest`**

  刪除 .NET 核心 SDK 和標記為預覽的運行時，但一個最高預覽除外。

* **`--aspnet-runtime`**

  僅刪除ASP.NET核心運行時。

* **`--hosting-bundle`**

  僅刪除 .NET 核心運行時和託管捆綁包。

* **`--major-minor <MAJOR_MINOR>`**

  刪除 .NET 核心 SDK 和與指定`major.minor`版本匹配的運行時。

* **`--runtime`**

  僅刪除 .NET 核心運行時。

* **`--sdk`**

  僅刪除 .NET 核心 SDK。

* **`-v, --verbosity <LEVEL>`**

  設置詳細程度級別。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`--x64`**

  必須與 一`--sdk`起使用`--runtime`，並`--aspnet-runtime`刪除 x64 SDK 或運行時。

* **`--x86`**

  必須與 和`--sdk``--runtime`一起使用`--aspnet-runtime`，並刪除 x86 SDK 或運行時。

* **`--force`** 強制刪除視覺工作室可能使用的版本。

注意：

1. 是 、 `--sdk` `--runtime`和`--aspnet-runtime``--hosting-bundle`的一個。
2. `--all`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]`
3. 如果`--x64`或`--x86`未指定，則將刪除 x64 和 x86。

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  刪除所有 .NET 核心 SDK 和運行時。

* **`--all-below <VERSION>`**

  刪除 .NET 核心 SDK 和低於指定版本的運行時。 指定的版本將保留。

* **`--all-but <VERSIONS>`**

  刪除 .NET 核心 SDK 和運行時，但指定的版本除外。

* **`--all-but-latest`**

  刪除 .NET 核心 SDK 和運行時，但一個最高版本除外。

* **`--all-lower-patches`**

  刪除 .NET 核心 SDK，運行時被較高的修補程式取代。 此選項保護全域.json。

* **`--all-previews`**

  刪除 .NET 核心 SDK 和標記為預覽的運行時。

* **`--all-previews-but-latest`**

  刪除 .NET 核心 SDK 和標記為預覽的運行時，但一個最高預覽除外。

* **`--major-minor <MAJOR_MINOR>`**

  刪除 .NET 核心 SDK 和與指定`major.minor`版本匹配的運行時。

* **`--runtime`**

  僅刪除 .NET 核心運行時。

* **`--sdk`**

  僅刪除 .NET 核心 SDK。

* **`-v, --verbosity <LEVEL>`**

  設置詳細程度級別。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。
  
* **`--force`** 強制刪除視覺工作室或 SDK 可能使用的版本。

注意：

1. 正好是`--sdk`和`--runtime`，
2. `--all`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]`

---

#### <a name="examples"></a>範例

> [!NOTE]
> 預設情況下，輸出中`dotnet-core-uninstall dry-run`不包括 Visual Studio 或其他 SDK 可能需要的 .NET 核心 SDK 和運行時。 在以下示例中，某些指定的 SDK 和運行時可能不包含在輸出中，具體取決於電腦的狀態。 要包括所有 SDK 和運行時，請將其顯式列為參數或使用 選項`--force`。

* 刪除已被更高修補程式取代的所有 .NET Core 運行時的幹運行：

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* 刪除版本`2.2.301`以下的所有 .NET 核心 SDK 的幹運行：

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>步驟 3 - 卸載 .NET 核心 SDK 和運行時

`dotnet-core-uninstall remove`卸載 .NET 核心 SDK 和執行時間，這些 SDK 由選項組合指定。 該工具不能用於卸載版本 5.0 或以上版本的 SDK 和運行時。

由於此工具具有破壞性行為，因此**強烈建議**您在運行刪除命令之前進行幹運行。 幹運行將顯示使用`remove`命令時將刪除什麼 .NET Core SDK 和運行時。 請參閱[是否應刪除版本？](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)以瞭解哪些 SDK 和運行時可以安全刪除。

> [!CAUTION]
> 請記住下列注意事項：
>
>- 此工具可以卸載電腦上的`global.json`檔所需的 .NET Core SDK 版本。 可以從[下載 .NET 核心](https://dotnet.microsoft.com/download/dotnet-core)頁面重新安裝 .NET 核心 SDK。
>- 此工具可以卸載電腦上依賴于框架的應用程式所需的 .NET Core 執行階段版本。 可以從[下載 .NET 核心](https://dotnet.microsoft.com/download/dotnet-core)頁面重新安裝 .NET 核心運行時。
>- 此工具可以卸載 Visual Studio 所依賴的 .NET 核心 SDK 和執行階段版本。 如果中斷 Visual Studio 安裝，請在 Visual Studio 安裝程式中運行"修復"以返回工作狀態。

預設情況下，所有命令都保留 Visual Studio 或其他 SDK 可能需要的 .NET 核心 SDK 和運行時。 可以通過顯式將它們列為參數或使用 選項`--force`來卸載這些 SDK 和運行時。

該工具需要提升才能卸載 .NET 核心 SDK 和運行時。 在 Windows 上和 macOS`sudo`上以管理員命令提示符運行該工具。 `dry-run`和`whatif`命令不需要高程。

**點網核心卸載刪除**

#### <a name="synopsis"></a>概要

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>引數

* **`VERSION`**

  要卸載的指定版本。 您可以逐個列出多個版本，由空格分隔。 還支援回應檔。

  > [!TIP]
  > 回應檔是將所有版本放在命令列上的替代方法。
  > 它們是文字檔，通常帶有\*.rsp 副檔名，每個版本都列在單獨的行上。
  > 要為`VERSION`參數指定回應檔，請使用該\@字元，緊跟回應檔案名。

#### <a name="options"></a>選項。

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  刪除所有 .NET 核心 SDK 和運行時。

* **`--all-below <VERSION>`**

  僅刪除版本小於指定版本的 .NET Core SDK 和運行時。 指定的版本將保持安裝狀態。

* **`--all-but <VERSIONS>`**

  刪除所有 .NET 核心 SDK 和運行時，但指定的版本除外。

* **`--all-but-latest`**

  刪除 .NET 核心 SDK 和運行時，但一個最高版本除外。

* **`--all-lower-patches`**

  刪除 .NET 核心 SDK，運行時被較高的修補程式取代。 此選項保護全域.json。

* **`--all-previews`**

  刪除 .NET 核心 SDK 和標記為預覽的運行時。

* **`--all-previews-but-latest`**

  刪除 .NET 核心 SDK 和標記為預覽的運行時，但一個最高預覽除外。

* **`--aspnet-runtime`**

  僅刪除ASP.NET核心運行時。

* **`--hosting-bundle`**

  僅刪除 .NET 核心運行時和託管捆綁包。

* **`--major-minor <MAJOR_MINOR>`**

  刪除 .NET 核心 SDK 和與指定`major.minor`版本匹配的運行時。

* **`--runtime`**

  僅刪除 .NET 核心運行時。

* **`--sdk`**

  僅刪除 .NET 核心 SDK。

* **`-v, --verbosity <LEVEL>`**

  設置詳細程度級別。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`--x64`**

  必須與 一`--sdk`起使用`--runtime`，並`--aspnet-runtime`刪除 x64 SDK 或運行時。

* **`--x86`**

  必須與 和`--sdk``--runtime`一起使用`--aspnet-runtime`，並刪除 x86 SDK 或運行時。

* **`-y, --yes`** 執行命令，無需確認或確認。

* **`--force`** 強制刪除視覺工作室可能使用的版本。

注意：

1. 是 、 `--sdk` `--runtime`和`--aspnet-runtime``--hosting-bundle`的一個。
2. `--all`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]`
3. 如果`--x64`或`--x86`未指定，則將刪除 x64 和 x86。

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  刪除所有 .NET 核心 SDK 和運行時。

* **`--all-below <VERSION>`**

  刪除 .NET 核心 SDK 和低於指定版本的運行時。 指定的版本將保留。

* **`--all-but <VERSIONS>`**

  刪除 .NET 核心 SDK 和運行時，但指定的版本除外。

* **`--all-but-latest`**

  刪除 .NET 核心 SDK 和運行時，但一個最高版本除外。

* **`--all-lower-patches`**

  刪除 .NET 核心 SDK，運行時被較高的修補程式取代。 此選項保護全域.json。

* **`--all-previews`**

  刪除 .NET 核心 SDK 和標記為預覽的運行時。

* **`--all-previews-but-latest`**

  刪除 .NET 核心 SDK 和標記為預覽的運行時，但一個最高預覽除外。

* **`--major-minor <MAJOR_MINOR>`**

  刪除 .NET 核心 SDK 和與指定`major.minor`版本匹配的運行時。

* **`--runtime`**

  僅刪除 .NET 核心運行時。

* **`--sdk`**

  僅刪除 .NET 核心 SDK。

* **`-v, --verbosity <LEVEL>`**

  設置詳細程度級別。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`-y, --yes`** 執行命令，無需 Y/N 確認。
  
* **`--force`** 強制刪除視覺工作室或 SDK 可能使用的版本。

注意：

1. 正好是`--sdk`和`--runtime`，
2. `--all`、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、、 `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches` `--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]`

---

#### <a name="examples"></a>範例

> [!NOTE]
> 預設情況下，保留 Visual Studio 或其他 SDK 可能需要的 .NET 核心 SDK 和運行時。 在以下示例中，某些指定的 SDK 和運行時可能會保留，具體取決於電腦的狀態。 要刪除所有 SDK 和運行時，請將其顯式列為參數或使用 選項`--force`。

* 刪除除版本`3.0.0-preview6-27804-01`外的所有 .NET 核心運行時，無需 Y/N 確認：

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* 刪除所有 .NET 核心 1.1 SDK，無需 Y/n 確認：

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* 刪除 .NET 核心 1.1.11 SDK，無需主控台輸出：

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* 刪除此工具可以安全地刪除的所有 .NET 核心 SDK：

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* 刪除此工具可以刪除的所有 .NET 核心 SDK，包括 Visual Studio 可能需要的 SDK（不推薦）：

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* 刪除回應檔中指定的所有 .NET 核心 SDK`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  *版本.rsp*的內容如下：
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>步驟 4 - 刪除 NuGet 回退資料夾（可選）

在某些情況下，您不再需要 ，`NuGetFallbackFolder`並且可能希望將其刪除。 有關刪除此資料夾的詳細資訊，請參閱[刪除 NuGet 回資料夾](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)。

## <a name="uninstall-the-tool"></a>卸載工具

## <a name="windows"></a>[Windows](#tab/windows)

1. 開啟 [新增或移除程式]****。
2. 搜尋 `Microsoft .NET Core SDK Uninstall Tool`。
3. 選取 [解除安裝]****。

## <a name="macos"></a>[macOS](#tab/macos)

從安裝該檔的目錄中刪除下載的*dotnet-core 卸載.tar.gz*檔。 如果將此檔的內容解壓縮到另一個目錄中，請確保也刪除該內容。

---
