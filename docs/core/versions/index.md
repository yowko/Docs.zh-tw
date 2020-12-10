---
title: .NET 執行時間和 SDK 的版本設定方式
description: 本文說明如何將 .NET SDK 和執行時間的版本設定 (類似于語義版本設定) 。
ms.date: 12/07/2020
ms.openlocfilehash: 2fe0b162b52f1e4500ec87f7d5d92054cd569552
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009302"
---
# <a name="overview-of-how-net-is-versioned"></a>.NET 的版本設定總覽

[.Net 執行時間和 .NET SDK](../introduction.md#sdk-and-runtimes)會以不同的頻率新增新功能。 一般來說，SDK 的更新頻率會比執行時間更頻繁。 本文說明執行時間和 SDK 版本號碼。

## <a name="versioning-details"></a>版本控制的詳細資料

.NET 執行時間有一種主要/次要/修補方法，可進行遵循 [語義版本](#semantic-versioning)控制的版本控制。

.NET SDK 不遵循語義版本控制。 .NET SDK 的發行速度更快，而且其版本號碼必須傳達對齊的執行時間和 SDK 本身的次要和修補程式版本。

.NET SDK 版本號碼的前兩個位置會鎖定至它所發行的 .NET 執行時間。 SDK 的每個版本都可以針對此執行階段或任何較低的版本建立應用程式。

SDK 版本號碼的第三個位置同時傳達次要與修補號碼。 次要版本會被乘以 100。 次要版本 1、修補版本 2 將以 102 表示。 最後兩位數代表修補號碼。 例如，以下是執行時間和 SDK 版本號碼的可能順序：

| 變更                | .NET 執行階段      | .NET SDK (\*)      |
|-----------------------|-------------------|-------------------|
| 初始版本       | 2.2.0             | 2.2.100           |
| SDK 修補程式             | 2.2.0             | 2.2.101           |
| 執行階段與 SDK 修補程式 | 2.2.1             | 2.2.102           |
| SDK 功能變更    | 2.2.1             | 2.2.200           |

注意：

- 若 SDK 在執行階段功能更新之前有 10 個功能更新，版本號碼會滾入 1000 系列，且具有 2.2.1000 做為 2.2.900 之後的未來發行版本。 此情況不應該發生。
- 不會發生沒有功能發行版本的 99 修補發行版本。 若發行版本接近此號碼，它會強制功能發行版本。

您可以在 [dotnet/designs](https://github.com/dotnet/designs/pull/29) 存放庫 \(英文\) 中查看此初始提案的詳細資訊。

## <a name="semantic-versioning"></a>語意化版本控制系統

.NET *運行* 時間大致符合 [語義版本控制 (SemVer)](https://semver.org/)，採用 `MAJOR.MINOR.PATCH` 版本控制的不同部分來描述變更的程度和類型，以使用版本控制。

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

選擇性的 `PRERELEASE` 和 `BUILDNUMBER` 組件絕對不會是受支援版本的一部分，並只會存在於每日組建、來自來源目標的本機組建，以及未支援的預覽版本上。

### <a name="understand-runtime-version-number-changes"></a>了解執行階段版本號碼變更

`MAJOR` 的遞增時機為：

- 產品或新產品方向發生重大便更。
- 接受中斷性變更。 接受中斷性變更的標準較高。
- 不再支援舊版本。
- 採用現有相依性的較新 `MAJOR` 版本。

`MINOR` 的遞增時機為：

- 新增公用 API 介面區。
- 新增新的行為。
- 採用現有相依性的較新 `MINOR` 版本。
- 引入新的相依性。

`PATCH` 的遞增時機為：

- 已修正 Bug。
- 新增對較新平台的支援。
- 採用現有相依性的較新 `PATCH` 版本。
- 任何其他不符合其中一個先前案例的變更。

當有多項變更時，因個別變更而影響的最高項目就會遞增，而下列項目會重設為零。 例如，當 `MAJOR` 遞增時，`MINOR` 和 `PATCH` 會重設為零。 當 `MINOR` 遞增時，`PATCH` 會重設為零而 `MAJOR` 保持不變。

## <a name="version-numbers-in-file-names"></a>檔案名稱中的版本號碼

針對 .NET 下載的檔案會包含版本，例如 `dotnet-sdk-2.1.300-win10-x64.exe` 。

### <a name="preview-versions"></a>預覽版本

預覽版本已 `-preview[number]-([build]|"final")` 附加至版本號碼。 例如： `2.0.0-preview1-final` 。

### <a name="servicing-versions"></a>服務版本

版本發行之後，版本分支通常會停止產生每日組建，改為開始產生服務組建。 服務版本會將 `-servicing-[number]` 附加至版本。 例如： `2.0.1-servicing-006924` 。

## <a name="relationship-to-net-standard-versions"></a>與 .NET Standard 版本的關聯性

.NET Standard 是由 .NET 參考組件所組成。 每個平台都有多個特定實作。 參考組件包含 .NET API 的定義，這是給定 .NET Standard 版本的一部分。 每個實作都履行特定平台上的 .NET Standard 合約。

.NET Standard 參考組件使用a `MAJOR.MINOR` 版本控制配置。 `PATCH` 對 .NET Standard 而言不實用，因為它只公開 API 規格 (無實作)，而且根據定義，對 API 所做的任何變更都會代表未來集合中的變更，亦即新的 `MINOR` 版本。

可能可以更新每個平台上的實作，通常是做為平台發行版本的一部分，因此對在該平台上使用 .NET Standard 的開發人員而言並非顯而易見。

如需詳細資訊，請參閱 [.NET Standard](../../standard/net-standard.md)。

## <a name="see-also"></a>請參閱

- [目標架構](../../standard/frameworks.md)
- [.NET 散發封裝](../distribution-packaging.md)
- [.NET 支援週期的事實表](https://dotnet.microsoft.com/platform/support/policy)
- [適用于 .NET 的 Docker 映射](https://hub.docker.com/_/microsoft-dotnet/)
