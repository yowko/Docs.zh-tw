---
title: 重大變更： IntPtr 和 UIntPtr 執行 >iformattable
description: 深入瞭解 IntPtr 和 UIntPtr 現在執行 >iformattable 的核心 .NET 程式庫中的 .NET 5.0 重大變更。
ms.date: 11/01/2020
ms.openlocfilehash: 0684652cdc2b8cf1d237074263bf0809082b0dcd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760762"
---
# <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="7d27f-103">IntPtr 和 UIntPtr 實 >iformattable</span><span class="sxs-lookup"><span data-stu-id="7d27f-103">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="7d27f-104"><xref:System.IntPtr><xref:System.UIntPtr>現在就執行了 <xref:System.IFormattable> 。</span><span class="sxs-lookup"><span data-stu-id="7d27f-104"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="7d27f-105">檢查支援的函式 <xref:System.IFormattable> 現在可能會針對這些類型傳回不同的結果，因為它們可能會傳入格式規範和文化特性。</span><span class="sxs-lookup"><span data-stu-id="7d27f-105">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

## <a name="change-description"></a><span data-ttu-id="7d27f-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="7d27f-106">Change description</span></span>

<span data-ttu-id="7d27f-107">在舊版的 .NET 中， <xref:System.IntPtr> 則 <xref:System.UIntPtr> 不會執行 <xref:System.IFormattable> 。</span><span class="sxs-lookup"><span data-stu-id="7d27f-107">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="7d27f-108">檢查的函式 <xref:System.IFormattable> 可能會改為只呼叫 <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> 或 <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> ，這表示不遵守格式規範和文化特性。</span><span class="sxs-lookup"><span data-stu-id="7d27f-108">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="7d27f-109">在 .NET 5.0 和更新版本中， <xref:System.IntPtr> 並 <xref:System.UIntPtr> 執行 <xref:System.IFormattable> 。</span><span class="sxs-lookup"><span data-stu-id="7d27f-109">In .NET 5.0 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="7d27f-110">檢查支援的函式 <xref:System.IFormattable> 現在可能會針對這些類型傳回不同的結果，因為它們可能會傳入格式規範和文化特性。</span><span class="sxs-lookup"><span data-stu-id="7d27f-110">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="7d27f-111">此變更會影響插入字串之類的案例 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> ，以及其他案例。</span><span class="sxs-lookup"><span data-stu-id="7d27f-111">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7d27f-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="7d27f-112">Reason for change</span></span>

<span data-ttu-id="7d27f-113"><xref:System.IntPtr><xref:System.UIntPtr>現在透過和關鍵字在 c # 中提供語言支援 `nint` `nuint` 。</span><span class="sxs-lookup"><span data-stu-id="7d27f-113"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="7d27f-114">支援型別已更新，可提供接近同位 (，盡可能以其他基本類型（例如）公開的功能) <xref:System.Int32?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7d27f-114">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7d27f-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="7d27f-115">Version introduced</span></span>

<span data-ttu-id="7d27f-116">5.0</span><span class="sxs-lookup"><span data-stu-id="7d27f-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7d27f-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7d27f-117">Recommended action</span></span>

<span data-ttu-id="7d27f-118">如果您不想要在顯示這些類型的值時使用格式規範或自訂文化特性，您可以呼叫的和多載 <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> `ToString()` 。</span><span class="sxs-lookup"><span data-stu-id="7d27f-118">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7d27f-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7d27f-119">Affected APIs</span></span>

<span data-ttu-id="7d27f-120">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="7d27f-120">Not detectable via API analysis.</span></span>

<!--

### Category

Core .NET libraries

### Affected APIs

Not detectable via API analysis.

-->
