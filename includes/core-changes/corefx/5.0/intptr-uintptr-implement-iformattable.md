---
ms.openlocfilehash: 3d29848e12d496d2d53c204e00ef8604831495e1
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024691"
---
### <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="7690d-101">IntPtr 和 UIntPtr 執行 IFormattable</span><span class="sxs-lookup"><span data-stu-id="7690d-101">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="7690d-102"><xref:System.IntPtr><xref:System.UIntPtr>現在會執行 <xref:System.IFormattable> 。</span><span class="sxs-lookup"><span data-stu-id="7690d-102"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="7690d-103">檢查支援的函式 <xref:System.IFormattable> 現在可能會針對這些類型傳回不同的結果，因為它們可能會傳入格式規範和文化特性。</span><span class="sxs-lookup"><span data-stu-id="7690d-103">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7690d-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="7690d-104">Change description</span></span>

<span data-ttu-id="7690d-105">在舊版的 .NET 中， <xref:System.IntPtr> 和 <xref:System.UIntPtr> 不會執行 <xref:System.IFormattable> 。</span><span class="sxs-lookup"><span data-stu-id="7690d-105">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="7690d-106">檢查的函式 <xref:System.IFormattable> 可能會切換回只呼叫 <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> 或 <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> ，這表示不會遵守格式規範和文化特性。</span><span class="sxs-lookup"><span data-stu-id="7690d-106">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="7690d-107">在 .NET 5.0 和更新版本中， <xref:System.IntPtr> 和會 <xref:System.UIntPtr> 執行 <xref:System.IFormattable> 。</span><span class="sxs-lookup"><span data-stu-id="7690d-107">In .NET 5.0 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="7690d-108">檢查支援的函式 <xref:System.IFormattable> 現在可能會針對這些類型傳回不同的結果，因為它們可能會傳入格式規範和文化特性。</span><span class="sxs-lookup"><span data-stu-id="7690d-108">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="7690d-109">這種變更會影響插入字串之類 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> 的案例，還有其他專案。</span><span class="sxs-lookup"><span data-stu-id="7690d-109">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7690d-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="7690d-110">Reason for change</span></span>

<span data-ttu-id="7690d-111"><xref:System.IntPtr>和 <xref:System.UIntPtr> 現在具有 c # 中透過和關鍵字的語言支援 `nint` `nuint` 。</span><span class="sxs-lookup"><span data-stu-id="7690d-111"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="7690d-112">支援的類型已更新，可提供接近同位 (，可能) 具有其他基本型別所公開的功能，例如 <xref:System.Int32?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="7690d-112">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7690d-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="7690d-113">Version introduced</span></span>

<span data-ttu-id="7690d-114">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="7690d-114">5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7690d-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7690d-115">Recommended action</span></span>

<span data-ttu-id="7690d-116">如果您不想要在顯示這些類型的值時使用格式規範或自訂文化特性，您可以呼叫的和多載 <xref:System.IntPtr.ToString?displayProperty=nameWithType> <xref:System.UIntPtr.ToString?displayProperty=nameWithType> `ToString()` 。</span><span class="sxs-lookup"><span data-stu-id="7690d-116">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

#### <a name="category"></a><span data-ttu-id="7690d-117">類別</span><span class="sxs-lookup"><span data-stu-id="7690d-117">Category</span></span>

<span data-ttu-id="7690d-118">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="7690d-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7690d-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7690d-119">Affected APIs</span></span>

<span data-ttu-id="7690d-120">無法透過 API 分析來偵測。</span><span class="sxs-lookup"><span data-stu-id="7690d-120">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
