---
title: global.json 概觀
description: 了解如何使用 global.json 檔案來設定執行.NET Core CLI 命令時的 NET Core SDK 版本。
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 70257566e1ff30f5c97212a5e0e3c308c27738b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77625991"
---
# <a name="globaljson-overview"></a>global.json 概觀

**本文適用于：✔️** .NET Core 2.0 SDK 和更高版本

*global.json* 檔案可讓您定義執行.NET Core CLI 命令時所使用的 .NET Core SDK 版本。 選取 .NET Core SDK 與指定專案所針對的執行階段沒有關係。 .NET 核心 SDK 版本指示使用了 .NET 核心 CLI 的哪些版本。

通常，您希望使用最新版本的 SDK 工具，因此不需要*全域.json*檔。 在某些高級方案中，您可能希望控制 SDK 工具的版本，本文將介紹如何執行此操作。

如需改為指定執行階段的詳細資訊，請參閱[目標架構](../../standard/frameworks.md)。

.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找 *global.json* 檔案。

## <a name="globaljson-schema"></a>global.json 結構描述

### <a name="sdk"></a>sdk

輸入： `object`

指定要選取 .NET Core SDK 的相關資訊。

#### <a name="version"></a>version

- 輸入： `string`

- 自： .NET 核心 1.0 SDK。

要使用的 .NET Core SDK 版本。

此欄位：

- 沒有萬用字元支援，也就是說，必須指定完整版本號。
- 不支援版本範圍。

#### <a name="allowprerelease"></a>允許預釋放

- 輸入： `boolean`

- 自： .NET 核心 3.0 SDK。

指示 SDK 解析器在選擇要使用的 SDK 版本時是否應考慮預發佈版本。

如果未顯式設置此值，則預設值取決於您是否從 Visual Studio 運行：

- 如果您**不在**Visual Studio 中，則預設值為`true`。
- 如果您在 Visual Studio 中，它將使用請求的預發佈狀態。 也就是說，如果您使用的是 Visual Studio 的預覽版，或者設置了 **.NET 核心 SDK 選項的"使用預覽**"（在 **"工具** > **選項** > **環境** > **預覽功能**"下`true`），則預設值為 ;否則， `false`.

#### <a name="rollforward"></a>滾動前進

- 輸入： `string`

- 自： .NET 核心 3.0 SDK。

選擇 SDK 版本時使用的滾前策略，在缺少特定 SDK 版本時作為回退策略，也可以用作使用更高版本的指令。 必須[version](#version)使用`rollForward`值指定版本，除非您將其設置為`latestMajor`。

要瞭解可用的策略及其行為，請考慮以下格式`x.y.znn`為 SDK 版本的定義：

- `x`是主要版本。
- `y`是次要版本。
- `z`是要素帶。
- `nn`是補丁版本。

下表顯示了金鑰的可能`rollForward`值：

| 值         | 行為 |
| ------------- | ---------- |
| `patch`       | 使用指定的版本。 <br> 如果未找到，則向前滾動到最新的修補程式級別。 <br> 如果未找到，則失敗。 <br><br> 此值是 SDK 早期版本中的舊行為。 |
| `feature`     | 對指定的主波段、次要波段和功能波段使用最新的修補程式級別。 <br> 如果未找到，則向前滾動到同一主/次要中的下一個較高要素波段，並為該要素波段使用最新的修補程式級別。 <br> 如果未找到，則失敗。 |
| `minor`       | 對指定的主波段、次要波段和功能波段使用最新的修補程式級別。 <br> 如果未找到，則在同一主/次要版本中向前滾動到下一個更高的要素波段，並為該功能波段使用最新的修補程式級別。 <br> 如果未找到，則向前滾動到同一主區中的下一個較高的次要和功能波段，並為此要素波段使用最新的修補程式級別。 <br> 如果未找到，則失敗。 |
| `major`       | 對指定的主波段、次要波段和功能波段使用最新的修補程式級別。 <br> 如果未找到，則在同一主/次要版本中向前滾動到下一個更高的要素波段，並為該功能波段使用最新的修補程式級別。 <br> 如果未找到，則向前滾動到同一主區中的下一個較高的次要和功能波段，並為此要素波段使用最新的修補程式級別。 <br> 如果未找到，則向前滾動到下一個更高的主、次要和功能波段，並使用該功能波段的最新修補程式級別。 <br> 如果未找到，則失敗。 |
| `latestPatch` | 使用與修補程式級別匹配請求的主要、次要和功能帶且大於或等於指定值的最新已安裝修補程式級別。 <br> 如果未找到，則失敗。 |
| `latestFeature` | 使用與請求的主要和次要要素帶匹配的最高安裝功能帶和修補程式級別，要素帶大於或等於指定值。 <br> 如果未找到，則失敗。 |
| `latestMinor` | 使用與請求的主要要素與大於或等於指定值的次要匹配的最高安裝次要、功能帶和修補程式級別。 <br> 如果未找到，則失敗。 |
| `latestMajor` | 使用安裝量最高的 .NET Core SDK，其主版本大於或等於指定值。 <br> 如果未找到，則失敗。 |
| `disable`     | 不會向前滾動。 需要完全符合。 |

## <a name="examples"></a>範例

下面的示例演示如何不使用預發行版本本：

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

下面的示例演示如何使用安裝的大於或等於指定版本的最高版本：

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

下面的示例演示如何使用指定的精確版本：

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

下面的示例演示如何使用特定版本安裝的最高修補程式版本（在表單中，3.1.1xx）：

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json 和.NET Core CLI

瞭解電腦上安裝了哪些 SDK 版本以在*global.json*檔中設置一個 SDK 版本會很有説明。 有關如何執行此操作的詳細資訊，請參閱[如何檢查 .NET Core 是否已安裝](../install/how-to-detect-installed-versions.md#check-sdk-versions)。

要在電腦上安裝其他 .NET 核心 SDK 版本，請訪問[下載 .NET 核心](https://dotnet.microsoft.com/download/dotnet-core)頁面。

執行 [dotnet new](dotnet-new.md) 命令，可在目前的目錄中建立新的 *global.json* 檔案，與下面的範例類似：

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>比對規則

> [!NOTE]
> 匹配規則由`dotnet.exe`進入點控制，該進入點在所有已安裝的 .NET Core 安裝運行時中很常見。 當您並排安裝多個運行時時，將使用 .NET Core 運行時最新安裝版本的匹配規則。

## <a name="net-core-3x"></a>[.NET Core 3.x](#tab/netcore3x)

從 .NET Core 3.0 開始，在確定要使用的 SDK 版本時，適用以下規則：

- 如果未找到*global.json*檔，或者*global.json*未指定 SDK 版本或`allowPrerelease`值，則使用安裝最高的 SDK 版本（等效于`rollForward`設置為`latestMajor`）。 是否考慮預發佈 SDK 版本取決於如何`dotnet`調用。
  - 如果您**不在**Visual Studio 中，則會考慮預發佈版本。
  - 如果您在 Visual Studio 中，它將使用請求的預發佈狀態。 也就是說，如果您使用的是 Visual Studio 的預覽版，或者設置了 **.NET 核心 SDK 選項的"使用預覽**"（在 **"工具** > **選項** > **環境** > **預覽功能**"下），則考慮預發佈版本;否則，僅考慮發佈版本。
- 如果發現*global.json*檔不指定 SDK 版本，但它指定值`allowPrerelease`，則使用安裝最高的 SDK 版本（等效于設置為`rollForward``latestMajor`）。 最新的 SDK 版本是否可以發佈或預發佈取決於 的值`allowPrerelease`。 `true`指示考慮預發行版本本;`false`表示只考慮發佈版本。
- 如果找到*global.json*檔並指定 SDK 版本：

  - 如果未`rollFoward`設置任何值，則用作`latestPatch`預設`rollForward`策略。 否則，請在["滾動前進"](#rollforward)部分中檢查每個值及其行為。
  - 是否考慮預發佈版本以及未設置時的`allowPrerelease`預設行為在["允許預發佈](#allowprerelease)"部分仲介紹。

## <a name="net-core-2x"></a>[.NET Core 2.x](#tab/netcore2x)

在 .NET Core 2.x SDK 中，在確定要使用的 SDK 版本時，適用以下規則：

- 如果找不到 *global.json* 檔案或 *global.json* 沒有指定 SDK 版本，則會使用最新安裝的 SDK 版本。 最新的 SDK 版本可以是發佈版本或預發佈 - 最高版本號獲勝。
- 如果 *global.json* 未指定 SDK 版本：
  - 如果在電腦上找到了指定的 SDK 版本，則會使用這個版本。
  - 如果在電腦上找不到指定的 SDK 版本，則會使用該版本的最新已安裝 SDK **修補程式版本**。 最新安裝的 SDK**修補程式版本**可以是發佈版本或預發佈 - 最高版本號獲勝。 對於 .NET Core 2.1 和更新版本，在 SDK 選取項目中，低於指定的**修補程式版本**的**修補程式版本**會被忽略。
  - 如果找不到指定的 SDK 版本和適當的 SDK **修補程式版本**，則會擲回錯誤。

SDK 版本由以下部分組成：

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

.NET Core SDK **功能版本**是由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的第一個數字 (`x`) 表示。 一般而言，.NET Core SDK 的發行週期比 .NET Core 快。

**修補程式版本**由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的最後兩個數字 (`yz`) 定義。 例如，如果指定 `2.1.300` 做為 SDK 版本，SDK 選取項目最高會找到 `2.1.399`，但是 `2.1.400` 不視為 `2.1.300` 的修補版本。

.NET Core SDK 版本 `2.1.100` 到 `2.1.201` 是在版本號碼轉換期間發行，它們並沒有正確地處理 `xyz` 標記法。 強烈建議如果您在 *global.json* 檔案中指定這些版本，則必須確保目標電腦上有這些指定的版本。

---

## <a name="troubleshoot-build-warnings"></a>排除生成警告

* 以下警告指示您的專案是使用 .NET Core SDK 的預發佈版本編譯的：

  > 您正在使用.NET Core SDK 的預覽版本。 您可以在目前的專案中透過 global.json 檔案定義 SDK 版本。 更多在<https://go.microsoft.com/fwlink/?linkid=869452>。

  .NET Core SDK 版本一向承諾提供高品質的產品。 但是，如果您不想使用預發佈版本，請檢查可在允許[預發佈](#allowprerelease)部分中使用 .NET Core 3.0 SDK 或更高版本的不同策略。 對於從未安裝過 .NET Core 3.0 或更高運行時或 SDK 的電腦，您需要創建*全域.json*檔並指定要使用的確切版本。

* 以下警告指示您的專案以 EF Core 1.0 或 1.1 為目標，後者與 .NET Core 2.1 SDK 和更高版本不相容：

  > 啟動專案 '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'。 這個版本的 Entity Framework Core.NET 命令列工具僅支援 2.0 版或更新版本。 有關使用舊版本的工具的資訊，請參閱<https://go.microsoft.com/fwlink/?linkid=871254>。

  從 .NET Core 2.1 SDK (2.1.300 版) 開始，`dotnet ef` 命令會包含在 SDK 中。 要編譯專案，請在電腦上安裝 .NET Core 2.0 SDK（版本 2.1.201）或更早版本，並使用*global.json*檔定義所需的 SDK 版本。 如需 `dotnet ef` 命令的詳細資訊，請參閱 [EF Core .NET 命令列工具](/ef/core/miscellaneous/cli/dotnet)。

## <a name="see-also"></a>另請參閱

- [解析專案 SDK 的方式](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
