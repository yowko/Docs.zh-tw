---
title: global.json 概觀
description: 了解如何使用 global.json 檔案來設定執行.NET Core CLI 命令時的 NET Core SDK 版本。
ms.topic: how-to
ms.date: 05/01/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 7e372c75812e79f85bb8965895d5fef694d9af1a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872391"
---
# <a name="globaljson-overview"></a>global.json 概觀

本文**適用于：** ✔️ .net CORE 2.0 SDK 和更新版本

*global.json* 檔案可讓您定義執行.NET Core CLI 命令時所使用的 .NET Core SDK 版本。 選取 .NET Core SDK 與指定專案所針對的執行階段沒有關係。 .NET Core SDK 版本會指出所使用的 .NET Core CLI 版本。

一般而言，您會想要使用最新版的 SDK 工具，因此不需要 *global.js* 檔案。 在某些 advanced 案例中，您可能會想要控制 SDK 工具的版本，而本文將說明如何進行這項操作。

如需改為指定執行階段的詳細資訊，請參閱[目標架構](../../standard/frameworks.md)。

.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找 *global.json* 檔案。

## <a name="globaljson-schema"></a>global.json 結構描述

### <a name="sdk"></a>sdk

輸入： `object`

指定要選取 .NET Core SDK 的相關資訊。

#### <a name="version"></a>版本

- 輸入： `string`

- 提供自： .NET Core 1.0 SDK。

要使用的 .NET Core SDK 版本。

此欄位：

- 沒有萬用字元支援，也就是必須指定完整的版本號碼。
- 不支援版本範圍。

#### <a name="allowprerelease"></a>allowPrerelease

- 輸入： `boolean`

- 提供自： .NET Core 3.0 SDK。

指出當您選取要使用的 SDK 版本時，SDK 解析程式是否應考慮發行前版本。

如果您未明確設定此值，預設值將取決於您是否從 Visual Studio 執行：

- 如果您 **不** 是 Visual Studio，預設值為 `true` 。
- 如果您在 Visual Studio 中，它會使用所要求的發行前版本狀態。 亦即，如果您使用預覽版本的 Visual Studio，或在 [**工具**選項環境預覽) 功能] 下設定 .NET Core SDK (選項的 [**使用預覽**]  >  **Options**  >  **Environment**  >  **Preview Features** ，則預設值為 `true` ; 否則為 `false` 。

#### <a name="rollforward"></a>向前復原

- 輸入： `string`

- 提供自： .NET Core 3.0 SDK。

選取 SDK 版本時所要使用的向前復原原則，可在特定 SDK 版本遺失或作為指示詞使用較高版本時作為復原。 必須以值指定 [版本](#version) `rollForward` ，除非您將它設定為 `latestMajor` 。

若要瞭解可用的原則及其行為，請考慮下列格式的 SDK 版本定義 `x.y.znn` ：

- `x` 這是主要版本。
- `y` 這是次要版本。
- `z` 是功能區。
- `nn` 這是修補程式版本。

下表顯示索引鍵的可能值 `rollForward` ：

| 值         | 行為 |
| ------------- | ---------- |
| `patch`       | 使用指定的版本。 <br> 如果找不到，會向前復原到最新的修補程式等級。 <br> 如果找不到，會失敗。 <br><br> 此值是舊版 SDK 的舊版行為。 |
| `feature`     | 針對指定的主要、次要和功能區，使用最新的修補程式等級。 <br> 如果找不到，會向前復原到相同主要/次要內的下一個較高的功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，會失敗。 |
| `minor`       | 針對指定的主要、次要和功能區，使用最新的修補程式等級。 <br> 如果找不到，會向前復原到相同主要/次要版本內的下一個較高的功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，會向前復原到相同主要位置內的下一個較高次要和功能頻外，並使用該功能區的最新修補程式等級。 <br> 如果找不到，會失敗。 |
| `major`       | 針對指定的主要、次要和功能區，使用最新的修補程式等級。 <br> 如果找不到，會向前復原到相同主要/次要版本內的下一個較高的功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，會向前復原到相同主要位置內的下一個較高次要和功能頻外，並使用該功能區的最新修補程式等級。 <br> 如果找不到，會向前復原到下一個較高的主要、次要和功能區，並使用該功能區的最新修補程式等級。 <br> 如果找不到，會失敗。 |
| `latestPatch` | 使用最新安裝的修補程式等級，此層級符合要求的主要、次要和功能頻的修補程式等級，且大於或等於指定的值。 <br> 如果找不到，會失敗。 |
| `latestFeature` | 使用最高安裝的功能區和修補程式等級，其符合要求的主要和次要，以及大於或等於指定值的功能區和修補程式等級。 <br> 如果找不到，會失敗。 |
| `latestMinor` | 使用最高安裝的次要、功能區和修補程式層級，以符合所要求的主要次要、功能區，以及大於或等於指定值的修補程式等級。 <br> 如果找不到，會失敗。 |
| `latestMajor` | 使用已安裝的最高 .NET Core SDK，其版本大於或等於指定的值。 <br> 如果找不到，會失敗。 |
| `disable`     | 不向前復原。 需要完全相符。 |

### <a name="msbuild-sdks"></a>msbuild-sdk

輸入： `object`

可讓您在單一位置（而不是每個個別專案）控制專案 SDK 版本。 如需詳細資訊，請參閱 [如何解析專案 sdk](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)。

## <a name="examples"></a>範例

下列範例顯示如何使用發行前版本：

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

下列範例會示範如何使用安裝的最高版本，且該版本大於或等於指定的版本。 所顯示的 JSON 不允許任何早于2.2.200 的 SDK 版本，並且允許2.2.200 或任何較新的版本，包括3.0.xxx 和3.1.xxx。

```json
{
  "sdk": {
    "version": "2.2.200",
    "rollForward": "latestMajor"
  }
}
```

下列範例顯示如何使用確切指定的版本：

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

下列範例顯示如何使用安裝在特定主要和次要版本的最新功能區和修補程式版本。 所顯示的 JSON 不允許任何早于3.1.102 的 SDK 版本，並且允許3.1.102 或任何較新的3.1.xxx 版本，例如3.1.103 或3.1.200。

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestFeature"
  }
}
```

下列範例顯示如何使用安裝在特定版本的最高修補程式版本。 所顯示的 JSON 不允許任何早于3.1.102 的 SDK 版本，並且允許3.1.102 或任何較新的 3.1.1 xx 版本（例如3.1.103 或3.1.199）。

```json
{
  "sdk": {
    "version": "3.1.102",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json 和.NET Core CLI

瞭解您電腦上安裝的 SDK 版本，以在 *global.js* 檔案中設定一個 SDK 會很有説明。 如需如何進行這項操作的詳細資訊，請參閱 [如何檢查是否已安裝 .Net Core](../install/how-to-detect-installed-versions.md#check-sdk-versions)。

若要在您的電腦上安裝其他 .NET Core SDK 版本，請造訪 [下載 .Net Core](https://dotnet.microsoft.com/download/dotnet-core) 頁面。

執行 [dotnet new](dotnet-new.md) 命令，可在目前的目錄中建立新的 *global.json* 檔案，與下面的範例類似：

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>比對規則

> [!NOTE]
> 比對規則是由 `dotnet.exe` 進入點所控制，這在所有已安裝的 .Net Core 安裝的執行時間中都很常見。 當您並存安裝多個執行時間時，會使用最新安裝的 .NET Core 執行時間版本的比對規則。

## <a name="net-core-3x"></a>[.NET Core 3.x](#tab/netcore3x)

從 .NET Core 3.0 開始，判斷要使用的 SDK 版本時，適用下列規則：

- 如果找不到檔案 * 上的global.js* ，或 *global.js* 未指定 SDK 版本或 `allowPrerelease` 值，則會使用最高安裝的 sdk 版本 (等同于設定 `rollForward` 為 `latestMajor`) 。 是否考慮預先發行版本 SDK 版本取決於叫用的方式 `dotnet` 。
  - 如果您 **不** 是 Visual Studio，則會考慮發行前版本。
  - 如果您在 Visual Studio 中，它會使用所要求的發行前版本狀態。 亦即，如果您使用預覽版本的 Visual Studio，或在 [**工具**選項環境預覽) 功能] 下設定 .NET Core SDK (選項的 [**使用預覽**]  >  **Options**  >  **Environment**  >  **Preview Features** ，則會考慮發行前版本，否則只會考慮發行版本。
- 如果找到的 *global.js* 檔案未指定 SDK 版本，但卻指定了 `allowPrerelease` 值，則會使用最高安裝的 SDK 版本， (等同于設定 `rollForward` 為 `latestMajor`) 。 最新的 SDK 版本是否可以是發行版本或發行前版本，視的值而定 `allowPrerelease` 。 `true` 表示已考慮發行前版本; `false` 指出只考慮發行版本。
- 如果找到檔案 * 上的global.js* ，並指定 SDK 版本：

  - 如果未 `rollForward` 設定任何值，則會使用 `latestPatch` 做為預設 `rollForward` 原則。 否則，請檢查 [向前復原](#rollforward) 區段中的每個值和其行為。
  - AllowPrerelease 一節會說明是否考慮發行前版本，以及 `allowPrerelease` 未設定的預設行為。 [allowPrerelease](#allowprerelease)

## <a name="net-core-2x"></a>[.NET Core 2.x](#tab/netcore2x)

在 .NET Core 2.x SDK 中，判斷要使用的 SDK 版本時，適用下列規則：

- 如果找不到 *global.json* 檔案或 *global.json* 沒有指定 SDK 版本，則會使用最新安裝的 SDK 版本。 最新的 SDK 版本可以是發行版本或發行前版本-最高的版本號碼獲勝。
- 如果 *global.json* 未指定 SDK 版本：
  - 如果在電腦上找到了指定的 SDK 版本，則會使用這個版本。
  - 如果在電腦上找不到指定的 SDK 版本，則會使用該版本的最新已安裝 SDK **修補程式版本**。 最新安裝的 SDK **修補程式版本** 可以是發行版本或發行前版本-最高的版本號碼獲勝。 對於 .NET Core 2.1 和更新版本，在 SDK 選取項目中，低於指定的**修補程式版本**的**修補程式版本**會被忽略。
  - 如果找不到指定的 SDK 版本和適當的 SDK **修補程式版本**，則會擲回錯誤。

SDK 版本是由下列元件所組成：

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

.NET Core SDK **功能版本**是由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的第一個數字 (`x`) 表示。 一般而言，.NET Core SDK 的發行週期比 .NET Core 快。

**修補程式版本**由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的最後兩個數字 (`yz`) 定義。 例如，如果指定 `2.1.300` 做為 SDK 版本，SDK 選取項目最高會找到 `2.1.399`，但是 `2.1.400` 不視為 `2.1.300` 的修補版本。

.NET Core SDK 版本 `2.1.100` 到 `2.1.201` 是在版本號碼轉換期間發行，它們並沒有正確地處理 `xyz` 標記法。 強烈建議如果您在 *global.json* 檔案中指定這些版本，則必須確保目標電腦上有這些指定的版本。

---

## <a name="troubleshoot-build-warnings"></a>針對組建警告進行疑難排解

* 下列警告指出您的專案是使用發行前版本的 .NET Core SDK 進行編譯：

  > 您正在使用.NET Core SDK 的預覽版本。 您可以在目前的專案中透過 global.json 檔案定義 SDK 版本。 詳細資訊請參閱 <https://go.microsoft.com/fwlink/?linkid=869452> 。

  .NET Core SDK 版本一向承諾提供高品質的產品。 但是，如果您不想要使用發行前版本，請在 [allowPrerelease](#allowprerelease) 區段中，檢查您可以與 .net CORE 3.0 SDK 或更新版本搭配使用的不同策略。 針對尚未安裝 .NET Core 3.0 或更高版本執行時間或 SDK 的電腦，您必須 * 在檔案上建立global.js* ，並指定您想要使用的確切版本。

* 下列警告指出您的專案目標 EF Core 1.0 或1.1，與 .NET Core 2.1 SDK 和更新版本不相容：

  > 啟動專案 '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'。 這個版本的 Entity Framework Core.NET 命令列工具僅支援 2.0 版或更新版本。 如需使用舊版工具的詳細資訊，請參閱 <https://go.microsoft.com/fwlink/?linkid=871254> 。

  從 .NET Core 2.1 SDK (2.1.300 版) 開始，`dotnet ef` 命令會包含在 SDK 中。 若要編譯您的專案，請在您的電腦上安裝 .NET Core 2.0 SDK (版本 2.1.201) 或更早版本，並使用 *global.json* file 定義所需的 SDK 版本。 如需 `dotnet ef` 命令的詳細資訊，請參閱 [EF Core .NET 命令列工具](/ef/core/miscellaneous/cli/dotnet)。

## <a name="see-also"></a>另請參閱

- [解析專案 SDK 的方式](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
