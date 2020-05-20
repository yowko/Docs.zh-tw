---
title: 全球化的重大變更
description: 列出 .NET Core 中全球化的重大變更。
ms.date: 04/07/2020
ms.openlocfilehash: 0c3367cb3515c6f473f53be6062b54f2e836b8c5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702275"
---
# <a name="globalization-breaking-changes"></a>全球化的重大變更

下列重大變更記載于此頁面：

| 重大變更 | 引進的版本 |
| - | :-: |
| [全球化 Api 在 Windows 上使用 ICU 程式庫](#globalization-apis-use-icu-libraries-on-windows) | 5.0 |
| [System.globalization.stringinfo> 和 TextElementEnumerator 現在符合 UAX29 標準](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | 5.0 |
| ["C" 地區設定對應到不變的地區設定](#c-locale-maps-to-the-invariant-locale) | 3.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
