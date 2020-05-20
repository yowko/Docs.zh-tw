---
ms.openlocfilehash: 49041ce906ab0bb8b9482b79c44302465c4ca788
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702286"
---
### <a name="globalization-apis-use-icu-libraries-on-windows"></a>全球化 Api 在 Windows 上使用 ICU 程式庫

.NET 5.0 和更新版本在 Windows 10 2019 更新或更新版本上執行時，會使用[Unicode （ICU）](http://site.icu-project.org/home)程式庫的國際元件來取得全球化功能。

#### <a name="change-description"></a>變更描述

之前，.NET 程式庫使用了全球化功能的[國家語言支援（NLS）](/windows/win32/intl/national-language-support) api。 例如，NLS 函數是用來取得文化特性資料，例如日期和時間格式模式、比較字串，以及在適當的文化特性中執行字串大小寫。

從 .NET 5.0 開始，如果應用程式在 Windows 10 2019 更新或更新版本上執行，則 .NET 程式庫會使用[ICU](http://site.icu-project.org/home)全球化 api。 Windows 10 5 月2019更新和更新版本隨附于 ICU 原生程式庫。 如果 .NET 執行時間無法載入 ICU，它會改為使用 NLS。

這是基於兩個原因而引進的變更：

- 應用程式在平臺上具有相同的全球化行為，包括 Linux、macOS 和 Windows。
- 應用程式可以使用自訂的 ICU 程式庫來控制全球化行為。

#### <a name="version-introduced"></a>引進的版本

.NET 5.0 Preview 4

#### <a name="recommended-action"></a>建議的動作

開發人員不需要採取任何動作。 不過，如果您想要繼續使用 NLS 全球化 Api，您可以設定[執行時間參數](../../../../docs/core/run-time-config/globalization.md#nls)來還原為該行為。

#### <a name="category"></a>類別

全球化

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- 命名空間中的大部分類型 <xref:System.Globalization?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Span%601`
- `T:System.String`
- `N:System.Globalization`

-->
