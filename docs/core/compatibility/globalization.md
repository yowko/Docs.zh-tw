---
title: 全球化重大變更
description: 列出 .NET Core 內的全球化重大變更。
ms.date: 04/07/2020
ms.openlocfilehash: 93990d89204df1b2d7498e1d748378fae05598c3
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065057"
---
# <a name="globalization-breaking-changes"></a>全球化重大變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | :-: |
| [某些拉丁字元的 Unicode 類別已變更](#unicode-category-changed-for-some-latin-1-characters) | 5.0 |
| [全球化 Api 在 Windows 上使用 ICU 程式庫](#globalization-apis-use-icu-libraries-on-windows) | 5.0 |
| [System.globalization.stringinfo> 和 TextElementEnumerator 現在已 UAX29 相容](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | 5.0 |
| ["C" 地區設定對應至不變的地區設定](#c-locale-maps-to-the-invariant-locale) | 3.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [unicode-categories-for-latin1-chars](../../../includes/core-changes/globalization/5.0/unicode-categories-for-latin1-chars.md)]

***

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
