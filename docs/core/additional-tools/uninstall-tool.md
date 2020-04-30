---
title: 卸載工具
description: 概述 .NET Core 卸載工具，這是一個引導式工具，可讓您控制 .NET Core Sdk 和執行時間的清理。
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 45cf0841391d02636770e98666e2897d2598fab4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595711"
---
# <a name="net-core-uninstall-tool"></a>.NET Core 解除安裝工具

[.Net core 卸載工具](https://aka.ms/dotnet-core-uninstall-tool)（`dotnet-core-uninstall`）可讓您從系統中移除 .net Core sdk 和執行時間。 有一組選項可用來指定您要卸載的版本。

此工具支援 Windows 和 macOS。 目前不支援 Linux。

在 Windows 上，此工具只能使用下列其中一個安裝程式來卸載已安裝的 Sdk 和執行時間：

- .NET Core SDK 和執行時間安裝程式。
- Visual Studio 安裝程式的版本早于 Visual Studio 2019 16.3 版。

在 macOS 上，此工具只能卸載位於 */usr/local/share/dotnet*資料夾中的 sdk 和執行時間。

基於這些限制，此工具可能無法卸載您電腦上的所有 .NET Core Sdk 和執行時間。 您可以使用`dotnet --info`命令來尋找已安裝的所有 .Net Core sdk 和執行時間，包括此工具無法移除的 sdk 和執行時間。 `dotnet-core-uninstall list`命令會顯示哪些 sdk 可以使用工具卸載。

## <a name="install-the-tool"></a>安裝工具

您可以從[這裡](https://aka.ms/dotnet-core-uninstall-tool)下載 .Net Core 卸載工具，並在[dotnet/cli-實驗室](https://github.com/dotnet/cli-lab)GitHub 存放庫中找到原始程式碼。

> [!NOTE]
> 此工具需要提高許可權，才能卸載 .NET Core Sdk 和執行時間。 因此，它應該安裝在受寫入保護的目錄中，例如 Windows 上的*C:\Program*檔案或 macOS 上的 */usr/local/bin* 。 另請參閱[dotnet 命令的更高存取權](../tools/elevated-access.md)。 如需詳細資訊，請參閱[詳細的安裝指示](https://aka.ms/dotnet-core-uninstall-tool)。

## <a name="run-the-tool"></a>執行工具

下列步驟顯示執行卸載工具的建議方法：

- [步驟 1-顯示已安裝的 .NET Core Sdk 和執行時間](#step-1---display-installed-net-core-sdks-and-runtimes)
- [步驟 2-進行試執行](#step-2---do-a-dry-run)
- [步驟 3-卸載 .NET Core Sdk 和執行時間](#step-3---uninstall-net-core-sdks-and-runtimes)
- [步驟 4-刪除 NuGet fallback 資料夾（選擇性）](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>步驟 1-顯示已安裝的 .NET Core Sdk 和執行時間

此`dotnet-core-uninstall list`命令會列出已安裝的 .Net Core sdk 和可使用此工具移除的執行時間。 Visual Studio 可能需要一些 Sdk 和執行時間，而且會顯示不建議將它們卸載的原因。

> [!NOTE]
> 在大部分情況下`dotnet-core-uninstall list` ，命令的輸出不會符合輸出中已安裝的版本清單。 `dotnet --info` 具體而言，此工具不會顯示 zip 檔案所安裝或受 Visual Studio 管理的版本（任何以 Visual Studio 2019 16.3 或更新版本安裝的版本）。 檢查版本是否由 Visual Studio 管理的其中一種方式是在中`Add or Remove Programs`加以查看，其中 Visual Studio 的受控版本會在其顯示名稱中標示為。

**dotnet-核心-卸載清單**

#### <a name="synopsis"></a>概要

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>選項。

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  列出所有可使用此工具卸載的 ASP.NET Core 執行時間。

* **`--hosting-bundle`**

  列出所有可使用此工具卸載的 .NET Core 執行時間和裝載套件組合。

* **`--runtime`**

  列出所有可使用此工具卸載的 .NET Core 執行時間。

* **`--sdk`**

  列出所有可使用此工具卸載的 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`--x64`**

  列出所有可使用此工具卸載的 x64 .NET Core Sdk 和執行時間。

* **`--x86`**

  列出所有可使用此工具卸載的 x86 .NET Core Sdk 和執行時間。

## <a name="macos"></a>[macOS](#tab/macos)

* **`--runtime`**

  列出所有可使用此工具卸載的 .NET Core 執行時間。

* **`--sdk`**

  列出所有可使用此工具卸載的 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。
  
---

#### <a name="examples"></a>範例

* 列出所有可使用此工具移除的 .NET Core Sdk 和執行時間：

  ```console
  dotnet-core-uninstall list
  ```

* 列出所有 x64 .NET Core Sdk 和執行時間：

  ```console
  dotnet-core-uninstall list --x64
  ```

* 列出所有的 x86 .NET Core Sdk：

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>步驟 2-進行試執行

`dotnet-core-uninstall dry-run`和`dotnet-core-uninstall whatif`命令會顯示 .net Core sdk 和執行時間，將會根據所提供的選項而移除，而不需執行卸載。 這些命令是同義字。

**dotnet-核心-卸載試執行和 dotnet-核心-卸載 whatif**

#### <a name="synopsis"></a>概要

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>引數

* **`VERSION`**

  要卸載的指定版本。 您可以逐一列出數個版本，並以空格分隔。 也支援回應檔案。

  > [!TIP]
  > 回應檔案是將所有版本放在命令列上的替代方案。
  > 它們是文字檔，通常\*副檔名為 .rsp，而每個版本都會列在個別的一行上。
  > 若要指定`VERSION`引數的回應檔，請使用\@緊接在回應檔名稱後面的字元。

#### <a name="options"></a>選項。

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  移除所有 .NET Core Sdk 和執行時間。

* **`--all-below <VERSION>`**

  只移除版本小於指定版本的 .NET Core Sdk 和執行時間。 指定的版本仍會安裝。

* **`--all-but <VERSIONS>`**

  除了指定的版本之外，移除所有 .NET Core Sdk 和執行時間。

* **`--all-but-latest`**

  移除 .NET Core Sdk 和執行時間，但不含最高版本。

* **`--all-lower-patches`**

  移除由較高修補程式取代的 .NET Core Sdk 和執行時間。 此選項可保護 global. json。

* **`--all-previews`**

  移除標示為預覽的 .NET Core Sdk 和執行時間。

* **`--all-previews-but-latest`**

  移除標記為預覽的 .NET Core Sdk 和執行時間，但最高預覽版本除外。

* **`--aspnet-runtime`**

  只移除 ASP.NET Core 執行時間。

* **`--hosting-bundle`**

  只會移除 .NET Core 執行時間和裝載套件組合。

* **`--major-minor <MAJOR_MINOR>`**

  移除符合指定`major.minor`版本的 .Net Core sdk 和執行時間。

* **`--runtime`**

  只會移除 .NET Core 執行時間。

* **`--sdk`**

  僅移除 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`--x64`**

  必須搭配`--sdk`、和`--runtime` `--aspnet-runtime`使用，才能移除 x64 sdk 或執行時間。

* **`--x86`**

  必須搭配`--sdk`、和`--runtime` `--aspnet-runtime`使用，才能移除 x86 sdk 或執行時間。

* **`--force`** 強制移除 Visual Studio 可能使用的版本。

注意：

1. 只需要`--sdk`、 `--runtime`、 `--aspnet-runtime`和`--hosting-bundle`其中一個。
2. `--all`、 `--all-below`、 `--all-but`、 `--all-but-latest`、 `--all-lower-patches`、 `--all-previews` `--all-previews-but-latest`、、和`[<VERSION>...]`是獨佔的。 `--major-minor`
3. 如果`--x64`未`--x86`指定或，則會移除 x64 和 x86。

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  移除所有 .NET Core Sdk 和執行時間。

* **`--all-below <VERSION>`**

  移除指定版本底下的 .NET Core Sdk 和執行時間。 指定的版本將會保留。

* **`--all-but <VERSIONS>`**

  除了指定的版本之外，移除 .NET Core Sdk 和執行時間。

* **`--all-but-latest`**

  移除 .NET Core Sdk 和執行時間，但不含最高版本。

* **`--all-lower-patches`**

  移除由較高修補程式取代的 .NET Core Sdk 和執行時間。 此選項可保護 global. json。

* **`--all-previews`**

  移除標示為預覽的 .NET Core Sdk 和執行時間。

* **`--all-previews-but-latest`**

  移除標記為預覽的 .NET Core Sdk 和執行時間，但最高預覽版本除外。

* **`--major-minor <MAJOR_MINOR>`**

  移除符合指定`major.minor`版本的 .Net Core sdk 和執行時間。

* **`--runtime`**

  只會移除 .NET Core 執行時間。

* **`--sdk`**

  僅移除 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。
  
* **`--force`** 強制移除 Visual Studio 或 Sdk 可能使用的版本。

注意：

1. 只有其中一個`--sdk`和`--runtime`是必要的。
2. `--all`、 `--all-below`、 `--all-but`、 `--all-but-latest`、 `--all-lower-patches`、 `--all-previews` `--all-previews-but-latest`、、和`[<VERSION>...]`是獨佔的。 `--major-minor`

---

#### <a name="examples"></a>範例

> [!NOTE]
> 根據預設，Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間不會包含在輸出`dotnet-core-uninstall dry-run`中。 在下列範例中，某些指定的 Sdk 和執行時間可能不會包含在輸出中，視電腦的狀態而定。 若要包含所有 Sdk 和執行時間，請將它們明確列出為`--force`引數或使用選項。

* 試執行移除所有已被較高修補程式取代的 .NET Core 執行時間：

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* 在版本`2.2.301`下方移除所有 .Net Core sdk 的試執行：

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>步驟 3-卸載 .NET Core Sdk 和執行時間

`dotnet-core-uninstall remove`卸載選項組合所指定的 .NET Core Sdk 和執行時間。 此工具無法用來卸載版本5.0 或更高版本的 Sdk 和執行時間。

由於此工具具有破壞性的行為，因此**強烈**建議您在執行 [移除] 命令之前先進行試執行。 試執行會顯示當您使用`remove`命令時，將會移除哪些 .Net Core sdk 和執行時間。 請參閱[我應該移除版本嗎？](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version)以瞭解哪些 sdk 和執行時間可以安全地移除。

> [!CAUTION]
> 請記住下列注意事項：
>
>- 這項工具可以卸載電腦上的檔案所需`global.json`的 .NET Core SDK 版本。 您可以從[下載 .Net core](https://dotnet.microsoft.com/download/dotnet-core)頁面重新安裝 .Net core sdk。
>- 這項工具可以卸載電腦上架構相依應用程式所需的 .NET Core 執行階段版本。 您可以從 [[下載 .Net core](https://dotnet.microsoft.com/download/dotnet-core) ] 頁面重新安裝 .net core 執行時間。
>- 這項工具可以卸載 Visual Studio 依賴之 .NET Core SDK 和執行時間的版本。 如果您中斷 Visual Studio 安裝，請在 Visual Studio 安裝程式中執行 [修復]，以回到作用中狀態。

根據預設，所有命令都會保留 Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間。 這些 Sdk 和執行時間可以藉由將它們明確地列為引數或使用`--force`選項來進行卸載。

此工具需要提高許可權，才能卸載 .NET Core Sdk 和執行時間。 在 Windows 上的系統管理員命令提示字元中，以及`sudo`在 macOS 上執行工具。 `dry-run`和`whatif`命令不需要提高許可權。

**dotnet-核心-卸載移除**

#### <a name="synopsis"></a>概要

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>引數

* **`VERSION`**

  要卸載的指定版本。 您可以逐一列出數個版本，並以空格分隔。 也支援回應檔案。

  > [!TIP]
  > 回應檔案是將所有版本放在命令列上的替代方案。
  > 它們是文字檔，通常\*副檔名為 .rsp，而每個版本都會列在個別的一行上。
  > 若要指定`VERSION`引數的回應檔，請使用\@緊接在回應檔名稱後面的字元。

#### <a name="options"></a>選項。

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  移除所有 .NET Core Sdk 和執行時間。

* **`--all-below <VERSION>`**

  只移除版本小於指定版本的 .NET Core Sdk 和執行時間。 指定的版本仍會安裝。

* **`--all-but <VERSIONS>`**

  除了指定的版本之外，移除所有 .NET Core Sdk 和執行時間。

* **`--all-but-latest`**

  移除 .NET Core Sdk 和執行時間，但不含最高版本。

* **`--all-lower-patches`**

  移除由較高修補程式取代的 .NET Core Sdk 和執行時間。 此選項可保護 global. json。

* **`--all-previews`**

  移除標示為預覽的 .NET Core Sdk 和執行時間。

* **`--all-previews-but-latest`**

  移除標記為預覽的 .NET Core Sdk 和執行時間，但最高預覽版本除外。

* **`--aspnet-runtime`**

  只移除 ASP.NET Core 執行時間。

* **`--hosting-bundle`**

  只會移除 .NET Core 執行時間和裝載套件組合。

* **`--major-minor <MAJOR_MINOR>`**

  移除符合指定`major.minor`版本的 .Net Core sdk 和執行時間。

* **`--runtime`**

  只會移除 .NET Core 執行時間。

* **`--sdk`**

  僅移除 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`--x64`**

  必須搭配`--sdk`、和`--runtime` `--aspnet-runtime`使用，才能移除 x64 sdk 或執行時間。

* **`--x86`**

  必須搭配`--sdk`、和`--runtime` `--aspnet-runtime`使用，才能移除 x86 sdk 或執行時間。

* **`-y, --yes`** 執行命令，而不需要有 [是] 或 [否] 確認。

* **`--force`** 強制移除 Visual Studio 可能使用的版本。

注意：

1. 只需要`--sdk`、 `--runtime`、 `--aspnet-runtime`和`--hosting-bundle`其中一個。
2. `--all`、 `--all-below`、 `--all-but`、 `--all-but-latest`、 `--all-lower-patches`、 `--all-previews` `--all-previews-but-latest`、、和`[<VERSION>...]`是獨佔的。 `--major-minor`
3. 如果`--x64`未`--x86`指定或，則會移除 x64 和 x86。

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  移除所有 .NET Core Sdk 和執行時間。

* **`--all-below <VERSION>`**

  移除指定版本底下的 .NET Core Sdk 和執行時間。 指定的版本將會保留。

* **`--all-but <VERSIONS>`**

  除了指定的版本之外，移除 .NET Core Sdk 和執行時間。

* **`--all-but-latest`**

  移除 .NET Core Sdk 和執行時間，但不含最高版本。

* **`--all-lower-patches`**

  移除由較高修補程式取代的 .NET Core Sdk 和執行時間。 此選項可保護 global. json。

* **`--all-previews`**

  移除標示為預覽的 .NET Core Sdk 和執行時間。

* **`--all-previews-but-latest`**

  移除標記為預覽的 .NET Core Sdk 和執行時間，但最高預覽版本除外。

* **`--major-minor <MAJOR_MINOR>`**

  移除符合指定`major.minor`版本的 .Net Core sdk 和執行時間。

* **`--runtime`**

  只會移除 .NET Core 執行時間。

* **`--sdk`**

  僅移除 .NET Core Sdk。

* **`-v, --verbosity <LEVEL>`**

  設定詳細資訊層級。 允許的值為 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 預設值是 `normal`。

* **`-y, --yes`** 執行命令，而不需要 Y/N 確認。
  
* **`--force`** 強制移除 Visual Studio 或 Sdk 可能使用的版本。

注意：

1. 只有其中一個`--sdk`和`--runtime`是必要的。
2. `--all`、 `--all-below`、 `--all-but`、 `--all-but-latest`、 `--all-lower-patches`、 `--all-previews` `--all-previews-but-latest`、、和`[<VERSION>...]`是獨佔的。 `--major-minor`

---

#### <a name="examples"></a>範例

> [!NOTE]
> 根據預設，Visual Studio 或其他 Sdk 可能需要的 .NET Core Sdk 和執行時間會保留下來。 在下列範例中，某些指定的 Sdk 和執行時間可能會保留，視電腦的狀態而定。 若要移除所有 Sdk 和執行時間，請將它們明確列出為`--force`引數或使用選項。

* 移除版本`3.0.0-preview6-27804-01`除外的所有 .net Core 執行時間，而不需要進行 Y/N 確認：

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

* 移除此工具可安全移除的所有 .NET Core Sdk：

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* 移除此工具可移除的所有 .NET Core Sdk，包括 Visual Studio 可能需要的 Sdk （不建議）：

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* 移除回應檔中指定的所有 .NET Core Sdk`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  *版本 .rsp*的內容如下所示：
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>步驟 4-刪除 NuGet fallback 資料夾（選擇性）

在某些情況下，您不再需要， `NuGetFallbackFolder`而且可能想要將它刪除。 如需刪除此資料夾的詳細資訊，請參閱[移除 NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder)。

## <a name="uninstall-the-tool"></a>卸載工具

## <a name="windows"></a>[Windows](#tab/windows)

1. 開啟 [新增或移除程式]****。
2. 搜尋 `Microsoft .NET Core SDK Uninstall Tool`。
3. 選取 [解除安裝]****。

## <a name="macos"></a>[macOS](#tab/macos)

從安裝的目錄中刪除已下載的*dotnet-core-uninstall gz*檔案。 如果您將此檔案的內容解壓縮至另一個目錄，請務必一併刪除該內容。

---
