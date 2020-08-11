---
title: global.json 概觀
description: 了解如何使用 global.json 檔案來設定執行.NET Core CLI 命令時的 NET Core SDK 版本。
ms.topic: how-to
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: a9558090b1ef48f376334fbc826f6265a58908da
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062791"
---
# <a name="globaljson-overview"></a>global.json 概觀

**本文適用于：** ✔️ .net CORE 2.0 SDK 和更新版本

*global.json* 檔案可讓您定義執行.NET Core CLI 命令時所使用的 .NET Core SDK 版本。 選取 .NET Core SDK 與指定專案所針對的執行階段沒有關係。 .NET Core SDK 版本指出所使用的 .NET Core CLI 版本。

一般來說，您會想要使用最新版的 SDK 工具，因此不需要*global.js*檔案。 在某些先進的案例中，您可能會想要控制 SDK 工具的版本，這篇文章會說明如何執行這項操作。

如需改為指定執行階段的詳細資訊，請參閱[目標架構](../../standard/frameworks.md)。

.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找 *global.json* 檔案。

## <a name="globaljson-schema"></a>global.json 結構描述

### <a name="sdk"></a>sdk

輸入： `object`

指定要選取 .NET Core SDK 的相關資訊。

#### <a name="version"></a>version

- 輸入： `string`

- 自： .NET Core 1.0 SDK 起提供。

要使用的 .NET Core SDK 版本。

此欄位：

- 不支援萬用字元，也就是必須指定完整的版本號碼。
- 不支援版本範圍。

#### <a name="allowprerelease"></a>allowPrerelease

- 輸入： `boolean`

- 自： .NET Core 3.0 SDK 起提供。

指出當選取要使用的 SDK 版本時，SDK 解析程式是否應考慮發行前版本。

如果您未明確設定此值，則預設值取決於您是否從 Visual Studio 執行：

- 如果您**不**是 Visual Studio，預設值是 `true` 。
- 如果您處於 Visual Studio，則會使用所要求的發行前版本狀態。 也就是說，如果您使用 Visual Studio 的預覽版本，或在 [**工具**] [選項] [環境] [預覽功能]) 底下設定 [**使用 .NET Core SDK** (選項的預覽]  >  **Options**  >  **Environment**  >  **Preview Features** ，則預設值為 `true` ; 否則為 `false` 。

#### <a name="rollforward"></a>向前復原

- 輸入： `string`

- 自： .NET Core 3.0 SDK 起提供。

選取 SDK 版本時要使用的向前復原原則，可以在特定 SDK 版本遺失時做為回溯，或做為使用較高版本的指示詞。 [version](#version) `rollForward` 除非您要將其設定為，否則必須使用值來指定版本 `latestMajor` 。

若要瞭解可用的原則及其行為，請考慮下列格式的 SDK 版本定義 `x.y.znn` ：

- `x`是主要版本。
- `y`是次要版本。
- `z`是功能區。
- `nn`是修補程式版本。

下表顯示索引鍵的可能值 `rollForward` ：

| 值         | 行為 |
| ------------- | ---------- |
| `patch`       | 使用指定的版本。 <br> 如果找不到，則會向前復原到最新的修補程式等級。 <br> 如果找不到，則會失敗。 <br><br> 這個值是舊版 SDK 的舊行為。 |
| `feature`     | 會針對指定的主要、次要和功能區使用最新的修補程式等級。 <br> 如果找不到，則會向前復原至相同主要/次要內的下一個較高功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，則會失敗。 |
| `minor`       | 會針對指定的主要、次要和功能區使用最新的修補程式等級。 <br> 如果找不到，則會向前復原至相同主要/次要版本內的下一個較高功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，則會向前復原至相同主要的下一個較高次要和功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，則會失敗。 |
| `major`       | 會針對指定的主要、次要和功能區使用最新的修補程式等級。 <br> 如果找不到，則會向前復原至相同主要/次要版本內的下一個較高功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，則會向前復原至相同主要的下一個較高次要和功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，則會向前復原至下一個較高的主要、次要和功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，則會失敗。 |
| `latestPatch` | 會使用符合所要求之主要、次要和功能區的最新已安裝修補程式等級，且其修補程式等級大於或等於指定的值。 <br> 如果找不到，則會失敗。 |
| `latestFeature` | 使用的最高安裝功能區和修補程式等級，符合所要求的主要和次要，以及大於或等於指定值的功能區。 <br> 如果找不到，則會失敗。 |
| `latestMinor` | 會使用最高安裝的次要、功能區，以及符合所要求主要的次要、大於或等於指定值的修補程式等級。 <br> 如果找不到，則會失敗。 |
| `latestMajor` | 使用已安裝的最高 .NET Core SDK，其主要大於或等於指定的值。 <br> 如果找不到，則會失敗。 |
| `disable`     | 不向前復原。 需要完全相符。 |

### <a name="msbuild-sdks"></a>msbuild-sdk

輸入： `object`

可讓您在一個位置控制專案 SDK 版本，而不是在每個個別專案中。 如需詳細資訊，請參閱[專案 sdk 的解析方式](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)。

## <a name="examples"></a>範例

下列範例顯示如何不使用發行前版本：

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

下列範例顯示如何使用安裝的最高版本（大於或等於指定的版本）。 所顯示的 JSON 不允許任何早于2.2.200 的 SDK 版本，並允許2.2.200 或任何較新版本，包括3.0.xxx 和3.1.xxx。

```json
{
  "sdk": {
    "version": "2.2.200",
    "rollForward": "latestMajor"
  }
}
```

下列範例顯示如何使用正確的指定版本：

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

下列範例示範如何使用安裝在特定主要和次要版本的最新功能區和修補程式版本。 所顯示的 JSON 不允許任何早于3.1.102 的 SDK 版本，並允許3.1.102 或任何較新的3.1.xxx 版本，例如3.1.103 或3.1.200。

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

下列範例顯示如何使用已安裝的特定版本最高的修補程式版本。 所顯示的 JSON 不允許任何早于3.1.102 的 SDK 版本，並允許3.1.102 或任何較新的 3.1.1 xx 版本，例如3.1.103 或3.1.199。

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json 和.NET Core CLI

瞭解哪些 SDK 版本已安裝在您的電腦上，以在檔案的*global.js*中設定一個，會很有説明。 如需如何執行此動作的詳細資訊，請參閱[如何檢查是否已安裝 .Net Core](../install/how-to-detect-installed-versions.md#check-sdk-versions)。

若要在您的電腦上安裝其他 .NET Core SDK 版本，請造訪[下載 .Net Core](https://dotnet.microsoft.com/download/dotnet-core)頁面。

執行 [dotnet new](dotnet-new.md) 命令，可在目前的目錄中建立新的 *global.json* 檔案，與下面的範例類似：

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>比對規則

> [!NOTE]
> 比對規則是由進入點所控管 `dotnet.exe` ，這在所有已安裝的 .Net Core 安裝執行時間中都是通用的。 當您有多個並行安裝的執行時間時，會使用 .NET Core 執行時間最新安裝版本的比對規則。

## <a name="net-core-3x"></a>[.NET Core 3.x](#tab/netcore3x)

從 .NET Core 3.0 開始，判斷要使用的 SDK 版本時，適用下列規則：

- 如果找不到檔案的*global.js* ，或*上的global.js*未指定 SDK 版本或 `allowPrerelease` 值，則會使用最高的已安裝 SDK 版本 (相當於設定 `rollForward` 為 [) ] `latestMajor` 。 是否要考慮發行前版本 SDK，取決於叫用的方式 `dotnet` 。
  - 如果您**不**是 Visual Studio，則會考慮發行前版本。
  - 如果您處於 Visual Studio，則會使用所要求的發行前版本狀態。 也就是說，如果您使用 Visual Studio 的預覽版本，或在 [**工具**] [選項] [環境] [預覽) 功能] 下設定 [**使用 .NET Core SDK**選項的預覽] ( >  **Options**  >  **Environment**  >  **Preview Features** ，則會考慮發行前版本，否則只會考慮發行版本。
- 如果找到的*global.js*檔案未指定 SDK 版本，但指定了 `allowPrerelease` 值，則會使用最高安裝的 sdk 版本， (相當於將設定 `rollForward` 為 [) ] `latestMajor` 。 最新的 SDK 版本是否可以發行或發行前版本，取決於的值 `allowPrerelease` 。 `true`表示已考慮發行前版本;`false`指出只會考慮發行版本。
- 如果找到檔案*上的global.js* ，而且它指定 SDK 版本：

  - 如果未 `rollFoward` 設定任何值，則會使用 `latestPatch` 做為預設 `rollForward` 原則。 否則，請檢查[向前復原](#rollforward)區段中的每個值及其行為。
  - 是否考慮發行前版本，以及未設定時的預設行為，請 `allowPrerelease` 參閱[allowPrerelease](#allowprerelease)一節。

## <a name="net-core-2x"></a>[.NET Core 2.x](#tab/netcore2x)

在 .NET Core 2.x SDK 中，當您決定要使用的 SDK 版本時，適用下列規則：

- 如果找不到 *global.json* 檔案或 *global.json* 沒有指定 SDK 版本，則會使用最新安裝的 SDK 版本。 最新的 SDK 版本可以是發行版本或發行前版本，最高的版本號碼獲勝。
- 如果 *global.json* 未指定 SDK 版本：
  - 如果在電腦上找到了指定的 SDK 版本，則會使用這個版本。
  - 如果在電腦上找不到指定的 SDK 版本，則會使用該版本的最新已安裝 SDK **修補程式版本**。 最新安裝的 SDK**修補程式版本**可以是發行版本或發行前版本（最高版本號碼獲勝）。 對於 .NET Core 2.1 和更新版本，在 SDK 選取項目中，低於指定的**修補程式版本**的**修補程式版本**會被忽略。
  - 如果找不到指定的 SDK 版本和適當的 SDK **修補程式版本**，則會擲回錯誤。

SDK 版本是由下列元件所組成：

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

.NET Core SDK **功能版本**是由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的第一個數字 (`x`) 表示。 一般而言，.NET Core SDK 的發行週期比 .NET Core 快。

**修補程式版本**由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的最後兩個數字 (`yz`) 定義。 例如，如果指定 `2.1.300` 做為 SDK 版本，SDK 選取項目最高會找到 `2.1.399`，但是 `2.1.400` 不視為 `2.1.300` 的修補版本。

.NET Core SDK 版本 `2.1.100` 到 `2.1.201` 是在版本號碼轉換期間發行，它們並沒有正確地處理 `xyz` 標記法。 強烈建議如果您在 *global.json* 檔案中指定這些版本，則必須確保目標電腦上有這些指定的版本。

---

## <a name="troubleshoot-build-warnings"></a>針對組建警告進行疑難排解

* 下列警告指出您的專案是使用 .NET Core SDK 的搶鮮版來編譯：

  > 您正在使用.NET Core SDK 的預覽版本。 您可以在目前的專案中透過 global.json 檔案定義 SDK 版本。 詳細資訊位於 <https://go.microsoft.com/fwlink/?linkid=869452> 。

  .NET Core SDK 版本一向承諾提供高品質的產品。 不過，如果您不想要使用發行前版本，請在[allowPrerelease](#allowprerelease)區段中查看可與 .net CORE 3.0 SDK 或更新版本搭配使用的不同策略。 對於從未安裝 .NET Core 3.0 或更新版本的電腦，您必須*在檔案上建立global.js* ，並指定您要使用的確切版本。

* 下列警告指出您的專案目標為 EF Core 1.0 或1.1，這與 .NET Core 2.1 SDK 和更新版本不相容：

  > 啟動專案 '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'。 這個版本的 Entity Framework Core.NET 命令列工具僅支援 2.0 版或更新版本。 如需使用舊版工具的詳細資訊，請參閱 <https://go.microsoft.com/fwlink/?linkid=871254> 。

  從 .NET Core 2.1 SDK (2.1.300 版) 開始，`dotnet ef` 命令會包含在 SDK 中。 若要編譯您的專案，請在您的電腦上安裝 .NET Core 2.0 SDK (版本 2.1.201) 或舊版，並使用*global.json* file 來定義所需的 SDK 版本。 如需 `dotnet ef` 命令的詳細資訊，請參閱 [EF Core .NET 命令列工具](/ef/core/miscellaneous/cli/dotnet)。

## <a name="see-also"></a>另請參閱

- [解析專案 SDK 的方式](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
