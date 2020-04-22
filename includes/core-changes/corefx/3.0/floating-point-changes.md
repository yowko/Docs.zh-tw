---
ms.openlocfilehash: 22dbb1e982f83687a9e0eb288ed72c78c676db77
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021682"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="0553c-101">變更浮點格式與分析行為</span><span class="sxs-lookup"><span data-stu-id="0553c-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="0553c-102">浮點解析和格式設定行為(按<xref:System.Double>和<xref:System.Single>類型)現在符合 IEEE。</span><span class="sxs-lookup"><span data-stu-id="0553c-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0553c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="0553c-103">Change description</span></span>

<span data-ttu-id="0553c-104">在 .NET Core 2.2<xref:System.Double.ToString%2A?displayProperty=nameWithType><xref:System.Single.ToString%2A?displayProperty=nameWithType>和早期<xref:System.Double.Parse%2A?displayProperty=nameWithType>版本<xref:System.Double.TryParse%2A?displayProperty=nameWithType>中<xref:System.Single.Parse%2A?displayProperty=nameWithType>,使用<xref:System.Single.TryParse%2A?displayProperty=nameWithType>和進行 格式化 ,以及使用 、和進行解析,不符合 IEEE。</span><span class="sxs-lookup"><span data-stu-id="0553c-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="0553c-105">因此,無法保證值將隨行任何支援的標準或自定義格式字串。</span><span class="sxs-lookup"><span data-stu-id="0553c-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="0553c-106">對於某些輸入,嘗試分析格式化的值可能會失敗,而對於其他輸入,解析的值不等於原始值。</span><span class="sxs-lookup"><span data-stu-id="0553c-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="0553c-107">從 .NET Core 3.0 開始,解析和格式化操作符合 IEEE 754 標準。</span><span class="sxs-lookup"><span data-stu-id="0553c-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="0553c-108">這可確保 .NET 中的浮點類型的行為與 IEEE 相容語言(如 C#)的行為匹配。</span><span class="sxs-lookup"><span data-stu-id="0553c-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="0553c-109">有關詳細資訊,請參閱[.NET Core 3.0 部落格文章中的浮點解析和格式改進](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)。</span><span class="sxs-lookup"><span data-stu-id="0553c-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0553c-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="0553c-110">Version introduced</span></span>

<span data-ttu-id="0553c-111">3.0</span><span class="sxs-lookup"><span data-stu-id="0553c-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0553c-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0553c-112">Recommended action</span></span>

<span data-ttu-id="0553c-113">[.NET Core 3.0 博客文章中的浮點解析和格式改進](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)的"對現有代碼的潛在影響"部分建議,如果觀察到行為更改與 .NET Core 2.2 應用程式相比,則更改代碼。</span><span class="sxs-lookup"><span data-stu-id="0553c-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="0553c-114">如果某些結果以前不正確,則可能無法使用解決方法。</span><span class="sxs-lookup"><span data-stu-id="0553c-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="0553c-115">類別</span><span class="sxs-lookup"><span data-stu-id="0553c-115">Category</span></span>

<span data-ttu-id="0553c-116">核心 .NET 函式庫</span><span class="sxs-lookup"><span data-stu-id="0553c-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0553c-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0553c-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
