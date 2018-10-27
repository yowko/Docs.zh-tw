---
title: .NET Core 版本控制
description: 了解 .NET Core 的版本控制運作方式。
author: bleroy
ms.author: mairaw
ms.date: 07/26/2018
ms.openlocfilehash: 9f77709abf59d5346bf5e3c6f512cfabbf9e50de
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50047432"
---
# <a name="net-core-versioning"></a>.NET Core 版本控制

.NET Core 參考 .NET Core Runtime 與 .NET Core SDK，它包含開發應用程式所需的工具。 .NET Core SDK 是設計來搭配任何舊版 .NET Core Runtime 使用的。 此文章說明執行階段與 SDK 版本策略。 您可以在介紹 [.NET Standard](../../standard/net-standard.md#net-implementation-support) 的文章中找到 .NET Standard 版本號碼的解釋。

.NET Core 執行階段與 .NET Core SDK 加入不同費率的新功能：一般而言，.NET Core SDK 提供更新工具的速度比 .NET Core 執行階段變更您在生產環境中使用的執行階段的速度快。 不幸的是，此問題在過去幾年已造成數個版本控制策略。 您可以在 [.NET Core 版本控制](version-history.md)一文中了解歷史記錄。

## <a name="versioning-details"></a>版本控制的詳細資料

".NET Core 2.1" 指的是 .NET Core 執行階段版本號碼。 .NET Core 執行階段有版本控制的主要/次要/修補方法，可允許[語意式版本控制](#semantic-versioning)。

.NET Core SDK 不遵循語意式版本控制。 .NET Core SDK 發行速度比較快，而且其版本必須同時傳達對應的執行階段與 SDK 的自有次要與修補發行版本。 .NET Core SDK 版本的前兩個位置鎖定至隨著它發行的 .NET Core 執行階段。 SDK 的每個版本都可以針對此執行階段或任何較低的版本建立應用程式。

SDK 版本號碼的第三個位置同時傳達次要與修補號碼。 次要版本會被乘以 100。 次要版本 1、修補版本 2 將以 102 表示。 最後兩位數代表修補號碼。 例如，.NET Core 2.2 的發行可能會建立如下表的發行版本：

| 變更                | .NET Core 執行階段 | .NET Core SDK (*) |
|-----------------------|-------------------|-------------------|
| 初始版本       | 2.2.0             | 2.2.100           |
| SDK 修補程式             | 2.2.0             | 2.2.101           |
| 執行階段與 SDK 修補程式 | 2.2.1             | 2.2.102           |
| SDK 功能變更    | 2.2.1             | 2.2.200           |

(\*) 此圖表使用未來的 2.2 .NET Core 執行階段做為範例，因為歷史成品表示 .NET Core 2.1 的第一個 SDK 是 2.1.300。 如需詳細資訊，請參閱 [.NET Core 版本控制的歷史](version-history.md)。

注意：

* 若 SDK 在執行階段功能更新之前有 10 個功能更新，版本號碼會滾入 1000 系列，且具有 2.2.1000 做為 2.2.900 之後的未來發行版本。 此情況不應該發生。
* 不會發生沒有功能發行版本的 99 修補發行版本。 若發行版本接近此號碼，它會強制功能發行版本。

您可以在 [dotnet/designs](https://github.com/dotnet/designs/pull/29) 存放庫 \(英文\) 中查看此初始提案的詳細資訊。

## <a name="semantic-versioning"></a>語意版本控制

.NET Core *執行階段* 大致上遵循[語意式版本控制 (SemVer)](https://semver.org/)並採用 `MAJOR.MINOR.PATCH` 版本控制，使用版本號碼的不同部分來描述變更的程度和類型。

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

選擇性的 `PRERELEASE` 和 `BUILDNUMBER` 組件絕對不會是受支援版本的一部分，並只會存在於每日組建、來自來源目標的本機組建，以及未支援的預覽版本上。

### <a name="understand-runtime-version-number-changes"></a>了解執行階段版本號碼變更

`MAJOR` 的遞增時機為：

* 產品或新產品方向發生重大便更。
* 接受中斷性變更。 接受中斷性變更的標準較高。
* 不再支援舊版本。
* 採用現有相依性的較新 `MAJOR` 版本。

`MINOR` 的遞增時機為：

* 新增公用 API 介面區。
* 新增新的行為。
* 採用現有相依性的較新 `MINOR` 版本。
* 引入新的相依性。

`PATCH` 的遞增時機為：

* 已修正 Bug。
* 新增對較新平台的支援。
* 採用現有相依性的較新 `PATCH` 版本。
* 任何其他不符合其中一個先前案例的變更。

當有多項變更時，因個別變更而影響的最高項目就會遞增，而下列項目會重設為零。 例如，當 `MAJOR` 遞增時，`MINOR` 和 `PATCH` 會重設為零。 當 `MINOR` 遞增時，`PATCH` 會重設為零而 `MAJOR` 保持不變。

## <a name="version-numbers-in-file-names"></a>檔案名稱中的版本號碼

針對 .NET Core 下載的檔案具有版本，例如 `dotnet-sdk-2.1.300-win10-x64.exe`。

### <a name="preview-versions"></a>預覽版本

預覽版本將 `-preview[number]-([build]|"final")` 附加至版本。 例如，`2.0.0-preview1-final`。

### <a name="servicing-versions"></a>服務版本

版本發行之後，版本分支通常會停止產生每日組建，改為開始產生服務組建。 服務版本會將 `-servicing-[number]` 附加至版本。 例如，`2.0.1-servicing-006924`。

## <a name="relationship-to-net-standard-versions"></a>與 .NET Standard 版本的關聯性

.NET Standard 是由 .NET 參考組件所組成。 每個平台都有多個特定實作。 參考組件包含 .NET API 的定義，這是給定 .NET Standard 版本的一部分。 每個實作都履行特定平台上的 .NET Standard 合約。 您可以在《.NET 指南》中的[.NET Standard](../../standard/net-standard.md) 一文深入了解 .NET Standard。

.NET Standard 參考組件使用a `MAJOR.MINOR` 版本控制配置。 `PATCH` 對 .NET Standard 而言不實用，因為它只公開 API 規格 (無實作)，而且根據定義，對 API 所做的任何變更都會代表未來集合中的變更，亦即新的 `MINOR` 版本。

可能可以更新每個平台上的實作，通常是做為平台發行版本的一部分，因此對在該平台上使用 .NET Standard 的開發人員而言並非顯而易見。

.NET Core 的每個版本都實作 .NET Standard. 的版本。 實作 .NET Standard 的版本意指支援舊版 .NET Standard。 .NET Standard 與 .NET Core 版本彼此獨立。 .NET Core 2.0 實作 .NET Standard 2.0 只是巧合。 .NET Core 2.1 也實作 .NET Standard 2.0。 .NET Core 將支援未來推出的 .NET Standard 版本。

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | 最高到 1.6     |
| 2.0       | 最高到 2.0     |
| 2.1       | 最高到 2.0     |

## <a name="see-also"></a>另請參閱

* [目標架構](../../standard/frameworks.md)  
* [.NET Core 發佈封裝](../build/distribution-packaging.md)  
* [.NET Core 支援週期資料表](https://www.microsoft.com/net/core/support)  
* [.NET Core 2+ Version Binding](https://github.com/dotnet/designs/issues/3) (.NET Core 2+ 版本繫結)  
* [.NET Core 的 Docker 映像](https://hub.docker.com/r/microsoft/dotnet/) \(英文\)
