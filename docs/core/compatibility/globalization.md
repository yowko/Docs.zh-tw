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
# <a name="globalization-breaking-changes"></a><span data-ttu-id="af733-103">全球化重大變更</span><span class="sxs-lookup"><span data-stu-id="af733-103">Globalization breaking changes</span></span>

<span data-ttu-id="af733-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="af733-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="af733-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="af733-105">Breaking change</span></span> | <span data-ttu-id="af733-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="af733-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="af733-107">某些拉丁字元的 Unicode 類別已變更</span><span class="sxs-lookup"><span data-stu-id="af733-107">Unicode category changed for some Latin-1 characters</span></span>](#unicode-category-changed-for-some-latin-1-characters) | <span data-ttu-id="af733-108">5.0</span><span class="sxs-lookup"><span data-stu-id="af733-108">5.0</span></span> |
| [<span data-ttu-id="af733-109">全球化 Api 在 Windows 上使用 ICU 程式庫</span><span class="sxs-lookup"><span data-stu-id="af733-109">Globalization APIs use ICU libraries on Windows</span></span>](#globalization-apis-use-icu-libraries-on-windows) | <span data-ttu-id="af733-110">5.0</span><span class="sxs-lookup"><span data-stu-id="af733-110">5.0</span></span> |
| [<span data-ttu-id="af733-111">System.globalization.stringinfo> 和 TextElementEnumerator 現在已 UAX29 相容</span><span class="sxs-lookup"><span data-stu-id="af733-111">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | <span data-ttu-id="af733-112">5.0</span><span class="sxs-lookup"><span data-stu-id="af733-112">5.0</span></span> |
| [<span data-ttu-id="af733-113">"C" 地區設定對應至不變的地區設定</span><span class="sxs-lookup"><span data-stu-id="af733-113">"C" locale maps to the invariant locale</span></span>](#c-locale-maps-to-the-invariant-locale) | <span data-ttu-id="af733-114">3.0</span><span class="sxs-lookup"><span data-stu-id="af733-114">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="af733-115">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="af733-115">.NET 5.0</span></span>

[!INCLUDE [unicode-categories-for-latin1-chars](../../../includes/core-changes/globalization/5.0/unicode-categories-for-latin1-chars.md)]

***

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="af733-116">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="af733-116">.NET Core 3.0</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
