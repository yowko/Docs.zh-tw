---
title: 重大變更： Unix 上 UNC 路徑的 Uri 識別
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中 Uri 類別現在會辨識開頭為兩個正斜線的字串，做為 Unix 上的 UNC 路徑。
ms.date: 11/01/2020
ms.openlocfilehash: 0d5d9cd8dd869f24e94d15724e5e16eaddf6ed47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760457"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a>Unix 上 UNC 路徑的 Uri 識別

<xref:System.Uri>類別現在會辨識開頭為兩個正斜線的字串 (`//`) 為 Unix 作業系統上 (UNC) 路徑的通用命名慣例。 這種變更讓這類字串在所有平臺上都是一致的。

## <a name="change-description"></a>變更描述

在舊版的 .NET 中， <xref:System.Uri> 類別會辨識開頭為兩個正斜線（例如，）的字串， `//contoso` 做為 Unix 作業系統的絕對檔案路徑。 不過，在 Windows 上，這類字串會被辨識為 UNC 路徑。

從 .NET 5.0 開始， <xref:System.Uri> 類別會辨識開頭為兩個正斜線的字串，做為所有平臺（包括 Unix）上的 UNC 路徑。 此外，屬性會根據 UNC 語義而行為：

- <xref:System.Uri.IsUnc?displayProperty=nameWithType> 會傳回 `true`。
- 路徑中的反斜線會以正斜線取代。 例如，`//first\second` 會成為 `//first/second`。
- <xref:System.Uri.LocalPath?displayProperty=nameWithType> 不以百分比編碼的字元。 例如， `//first/\uFFF0` *不* 會轉換成 `//first/%EF%BF%B0` 。

## <a name="version-introduced"></a>引進的版本

5.0

## <a name="recommended-action"></a>建議的動作

開發人員不需要採取任何動作。

## <a name="affected-apis"></a>受影響的 API

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
