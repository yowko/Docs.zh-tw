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
# <a name="globalization-breaking-changes"></a><span data-ttu-id="daae6-103">全球化的重大變更</span><span class="sxs-lookup"><span data-stu-id="daae6-103">Globalization breaking changes</span></span>

<span data-ttu-id="daae6-104">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="daae6-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="daae6-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="daae6-105">Breaking change</span></span> | <span data-ttu-id="daae6-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="daae6-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="daae6-107">全球化 Api 在 Windows 上使用 ICU 程式庫</span><span class="sxs-lookup"><span data-stu-id="daae6-107">Globalization APIs use ICU libraries on Windows</span></span>](#globalization-apis-use-icu-libraries-on-windows) | <span data-ttu-id="daae6-108">5.0</span><span class="sxs-lookup"><span data-stu-id="daae6-108">5.0</span></span> |
| [<span data-ttu-id="daae6-109">System.globalization.stringinfo> 和 TextElementEnumerator 現在符合 UAX29 標準</span><span class="sxs-lookup"><span data-stu-id="daae6-109">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | <span data-ttu-id="daae6-110">5.0</span><span class="sxs-lookup"><span data-stu-id="daae6-110">5.0</span></span> |
| [<span data-ttu-id="daae6-111">"C" 地區設定對應到不變的地區設定</span><span class="sxs-lookup"><span data-stu-id="daae6-111">"C" locale maps to the invariant locale</span></span>](#c-locale-maps-to-the-invariant-locale) | <span data-ttu-id="daae6-112">3.0</span><span class="sxs-lookup"><span data-stu-id="daae6-112">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="daae6-113">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="daae6-113">.NET 5.0</span></span>

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="daae6-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="daae6-114">.NET Core 3.0</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
