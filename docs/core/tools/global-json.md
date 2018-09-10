---
title: global.json 概觀
description: 了解如何使用 global.json 檔案來設定執行.NET Core CLI 命令時的 NET Core SDK 版本。
author: mairaw
ms.author: mairaw
ms.date: 07/30/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 8241b3afb518acf237c7b6181085e19576e5ce2f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43778465"
---
# <a name="globaljson-overview"></a>global.json 概觀

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

*global.json* 檔案可讓您定義執行.NET Core CLI 命令時所使用的 .NET Core SDK 版本。 選取 .NET Core SDK 與指定專案所針對的執行階段沒有關係。 .NET Core SDK 版本會指出使用哪個版本的.NET Core CLI 工具。 一般情況下，您要使用最新版本的工具，所以不需要 *global.json* 檔案。

如需改為指定執行階段的詳細資訊，請參閱[目標架構](../../standard/frameworks.md)。

.NET Core CLI 工具會在目前工作目錄 (這不一定與專案目錄相同) 或它的其中一個上層目錄中尋找 *global.json* 檔案。

## <a name="globaljson-schema"></a>global.json 結構描述

### <a name="sdk"></a>SDK

類型：Object

指定要選取 .NET Core SDK 的相關資訊。

#### <a name="version"></a>版本

類型：String

要使用的 .NET Core SDK 版本。

請注意，此欄位：

- 不支援萬用字元，亦即，必須指定完整的版本號碼。
- 不支援版本範圍。

下列範例顯示 *global.json* 檔案的內容：

```json
{
  "sdk": {
    "version": "2.1.300"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.json 和.NET Core CLI

最好知道哪一個版本可供使用，以便在 *global.json* 檔案中設定一個。 您可以在 [.NET 下載](https://www.microsoft.com/net/download/all)網站找到 SDK 支援版本的完整清單。 從.NET Core SDK 2.1 開始，您可以執行下列命令來確認電腦上已安裝的 SDK 版本：

```console
dotnet --list-sdks
```

若要在電腦上安裝其他 .NET Core SDK 版本，請造訪 [.NET 下載](https://www.microsoft.com/net/download/all)網站。

執行 [dotnet new](dotnet-new.md) 命令，可在目前的目錄中建立新的 *global.json* 檔案，與下面的範例類似：

```console
dotnet new globaljson --sdk-version 2.1.300
```

## <a name="matching-rules"></a>比對規則

> [!NOTE]
> 比對規則由 apphost 規範，這是.NET Core 執行階段的一部分。
> 您有多個執行階段並列安裝時，會使用最新版本的主機。

從 .NET Core 2.0 開始，決定要使用哪個 SDK 版本時會使用下列規則：

- 如果找不到 *global.json* 檔案或 *global.json* 沒有指定 SDK 版本，則會使用最新安裝的 SDK 版本。 最新的 SDK 版本可以是發行版本或發行前版本，而最高版本號碼優先採用。
- 如果 *global.json* 未指定 SDK 版本：
  - 如果在電腦上找到了指定的 SDK 版本，則會使用這個版本。
  - 如果在電腦上找不到指定的 SDK 版本，則會使用該版本的最新已安裝 SDK **修補程式版本**。 最新已安裝的 SDK **修補程式版本**可以是發行版本或發行前版本，而最高版本號碼優先採用。 對於 .NET Core 2.1 和更新版本，在 SDK 選取項目中，低於指定的**修補程式版本**的**修補程式版本**會被忽略。
  - 如果找不到指定的 SDK 版本和適當的 SDK **修補程式版本**，則會擲回錯誤。

SDK 版本目前由下列部分組成：

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

.NET Core SDK **功能版本**是由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的第一個數字 (`x`) 表示。 一般而言，.NET Core SDK 的發行週期比 .NET Core 快。

**修補程式版本**由 SDK 2.1.100 和更新版本號碼最後部分 (`xyz`) 的最後兩個數字 (`yz`) 定義。 例如，如果指定 `2.1.300` 做為 SDK 版本，SDK 選取項目最高會找到 `2.1.399`，但是 `2.1.400` 不視為 `2.1.300` 的修補版本。

.NET Core SDK 版本 `2.1.100` 到 `2.1.201` 是在版本號碼轉換期間發行，它們並沒有正確地處理 `xyz` 標記法。 強烈建議如果您在 *global.json* 檔案中指定這些版本，則必須確保目標電腦上有這些指定的版本。

對於.NET Core SDK 1.x，如果您指定了某個版本但找不到它，則會使用最新安裝的 SDK 版本。 最新的 SDK 版本可以是發行版本或發行前版本，而最高版本號碼優先採用。

## <a name="troubleshooting-build-warnings"></a>為組建警告進行疑難排解

> [!WARNING]
> 您正在使用.NET Core SDK 的預覽版本。 您可以在目前的專案中透過 global.json 檔案定義 SDK 版本。 詳情請見 https://go.microsoft.com/fwlink/?linkid=869452

這則警告指出您的專案正使用.NET Core SDK 的預覽版本編譯，如[比對規則](#matching-rules)一節中的說明。 .NET Core SDK 版本一向承諾提供高品質的產品。 不過，如果您不想使用預覽版本，請新增 *global.json* 檔案到專案階層架構以指定要使用的 SDK 版本，並使用 `dotnet --list-sdks` 來確認電腦上已安裝該版本。 新版本發行時，若要使用新的版本，可移除 *global.json* 檔案或更新它以使用較新版本。

> [!WARNING]
> 啟動專案 '{startupProject}' targets framework '.NETCoreApp' version '{targetFrameworkVersion}'。 這個版本的 Entity Framework Core.NET 命令列工具僅支援 2.0 版或更新版本。 如需使用較舊版本工具的詳細資訊，請參閱 https://go.microsoft.com/fwlink/?linkid=871254 \(英文\)

開始使用 .NET Core SDK 2.1 (v. 2.1.300)，`dotnet ef` 命令包含在 SDK 中。 這則警告指出您的專案目標為 EF Core 1.0 或 1.1，與.NET Core SDK 2.1 和更新版本不相容。 若要編譯您的專案，請在電腦上安裝 .NET Core SDK 2.0 (v. 2.1.201) 及更早的版本，並使用 *global.json* 檔案定義所需的 SDK 版本。 如需 `dotnet ef` 命令的詳細資訊，請參閱 [EF Core .NET 命令列工具](/ef/core/miscellaneous/cli/dotnet)。

## <a name="see-also"></a>另請參閱

* [解析專案 SDK 的方式](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
