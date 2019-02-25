---
title: 字元集和封送處理 - .NET
description: 了解 CharSet 的不同值如何變更 .NET 將您的資料封送處理為機器碼的方式。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 2ff6c485906db481cb5236f83e885ba9fd46450b
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "56411360"
---
# <a name="charsets-and-marshalling"></a><span data-ttu-id="d03b6-103">字元集和封送處理</span><span class="sxs-lookup"><span data-stu-id="d03b6-103">Charsets and marshalling</span></span>

<span data-ttu-id="d03b6-104">`char` 值、`string` 物件與 `System.Text.StringBuilder` 物件的封送處理方式取決於 P/Invoke 或結構上之 `CharSet` 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="d03b6-104">The way `char` values, `string` objects, and `System.Text.StringBuilder` objects are marshalled depends on the value of the `CharSet` field on either the P/Invoke or structure.</span></span> <span data-ttu-id="d03b6-105">您可以透過在宣告您的 P/Invoke 時設定 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> 欄位，以設定 P/Invoke 的 `CharSet`。</span><span class="sxs-lookup"><span data-stu-id="d03b6-105">You can set the `CharSet` of a P/Invoke by setting the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field when declaring your P/Invoke.</span></span> <span data-ttu-id="d03b6-106">若要為結構設定 `CharSet`，請在您的結構宣告上設定 <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> 欄位。</span><span class="sxs-lookup"><span data-stu-id="d03b6-106">To set the `CharSet` for a structure, set the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field on your struct declaration.</span></span> <span data-ttu-id="d03b6-107">當這些屬性欄位未設定時，語言編譯器可決定要使用的 `CharSet`。</span><span class="sxs-lookup"><span data-stu-id="d03b6-107">When these attribute fields are not set, it is up to the language compiler to determine which `CharSet` to use.</span></span> <span data-ttu-id="d03b6-108">C# 預設使用 <xref:System.Runtime.InteropServices.CharSet.Ansi> 字元集。</span><span class="sxs-lookup"><span data-stu-id="d03b6-108">C# uses the <xref:System.Runtime.InteropServices.CharSet.Ansi> charset by default.</span></span>

<span data-ttu-id="d03b6-109">下表說明每個字元集與使用該字元集進行封送處理時，如何代表字元集或字串：</span><span class="sxs-lookup"><span data-stu-id="d03b6-109">The following table shows a mapping between each charset and how a character or string is represented when marshalled with that charset:</span></span>

| <span data-ttu-id="d03b6-110">字元集</span><span class="sxs-lookup"><span data-stu-id="d03b6-110">CharSet</span></span> | <span data-ttu-id="d03b6-111">Windows</span><span class="sxs-lookup"><span data-stu-id="d03b6-111">Windows</span></span> | <span data-ttu-id="d03b6-112">Unix</span><span class="sxs-lookup"><span data-stu-id="d03b6-112">Unix</span></span> | <span data-ttu-id="d03b6-113">Unix 為 Mono</span><span class="sxs-lookup"><span data-stu-id="d03b6-113">Mono on Unix</span></span> |
|---------|---------|-------|-------|
| <span data-ttu-id="d03b6-114">Ansi</span><span class="sxs-lookup"><span data-stu-id="d03b6-114">Ansi</span></span>    | <span data-ttu-id="d03b6-115">`char` (ANSI)</span><span class="sxs-lookup"><span data-stu-id="d03b6-115">`char` (ANSI)</span></span>  | <span data-ttu-id="d03b6-116">`char` (macOS 上為 ANSI，Linux 上為 UTF-8)</span><span class="sxs-lookup"><span data-stu-id="d03b6-116">`char` (ANSI on macOS, UTF-8 on Linux)</span></span> | <span data-ttu-id="d03b6-117">`char` (UTF-8)</span><span class="sxs-lookup"><span data-stu-id="d03b6-117">`char` (UTF-8)</span></span> |
| <span data-ttu-id="d03b6-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="d03b6-118">Unicode</span></span> | <span data-ttu-id="d03b6-119">`wchar_t` (UTF-16)</span><span class="sxs-lookup"><span data-stu-id="d03b6-119">`wchar_t` (UTF-16)</span></span> | <span data-ttu-id="d03b6-120">`char16_t` (UTF-16)</span><span class="sxs-lookup"><span data-stu-id="d03b6-120">`char16_t` (UTF-16)</span></span> | <span data-ttu-id="d03b6-121">`char16_t` (UTF-16)</span><span class="sxs-lookup"><span data-stu-id="d03b6-121">`char16_t` (UTF-16)</span></span> |
| <span data-ttu-id="d03b6-122">自動</span><span class="sxs-lookup"><span data-stu-id="d03b6-122">Auto</span></span> | <span data-ttu-id="d03b6-123">`wchar_t` (UTF-16)</span><span class="sxs-lookup"><span data-stu-id="d03b6-123">`wchar_t` (UTF-16)</span></span> | <span data-ttu-id="d03b6-124">`char16_t` (UTF-16)</span><span class="sxs-lookup"><span data-stu-id="d03b6-124">`char16_t` (UTF-16)</span></span> | <span data-ttu-id="d03b6-125">`char` (UTF-8)</span><span class="sxs-lookup"><span data-stu-id="d03b6-125">`char` (UTF-8)</span></span> |

<span data-ttu-id="d03b6-126">選擇您的字元集時，請確定您知道您原生代表的代表應該是什麼樣子。</span><span class="sxs-lookup"><span data-stu-id="d03b6-126">Make sure you know what representation your native representation expects when picking your charset.</span></span>
