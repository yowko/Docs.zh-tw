---
ms.openlocfilehash: ce4f09908b1025e8e5a0380c9bf035c6b0db479a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182028"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="ab970-101">浮點格式設定和剖析行為已變更</span><span class="sxs-lookup"><span data-stu-id="ab970-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="ab970-102">浮點剖析和格式化行為（依<xref:System.Double>和類型）現在是與<xref:System.Single> IEEE 相容。</span><span class="sxs-lookup"><span data-stu-id="ab970-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ab970-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ab970-103">Change description</span></span>

<span data-ttu-id="ab970-104">在 .net Core 2.2 和更早版本中， <xref:System.Double.ToString%2A?displayProperty=nameWithType>使用<xref:System.Single.ToString%2A?displayProperty=nameWithType>和進行的格式<xref:System.Double.Parse%2A?displayProperty=nameWithType>設定和<xref:System.Single.Parse%2A?displayProperty=nameWithType>以、 <xref:System.Single.TryParse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType>、和進行剖析並不符合 IEEE 規範。</span><span class="sxs-lookup"><span data-stu-id="ab970-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="ab970-105">因此，無法保證值會與任何支援的標準或自訂格式字串往返。</span><span class="sxs-lookup"><span data-stu-id="ab970-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="ab970-106">對於某些輸入，剖析格式化值的嘗試可能會失敗，而針對其他專案，則剖析的值不等於原始值。</span><span class="sxs-lookup"><span data-stu-id="ab970-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="ab970-107">從 .NET Core 3.0 開始，剖析和格式化作業與 IEEE 754 相容。</span><span class="sxs-lookup"><span data-stu-id="ab970-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="ab970-108">這可確保 .NET 中浮點類型的行為符合與 IEEE 相容的語言（例如） C#。</span><span class="sxs-lookup"><span data-stu-id="ab970-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="ab970-109">如需詳細資訊，請參閱[.Net Core 3.0 中的浮點剖析和格式改進](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)文章。</span><span class="sxs-lookup"><span data-stu-id="ab970-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ab970-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ab970-110">Version introduced</span></span>

<span data-ttu-id="ab970-111">3.0</span><span class="sxs-lookup"><span data-stu-id="ab970-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ab970-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ab970-112">Recommended action</span></span>

<span data-ttu-id="ab970-113">[.Net core 3.0 中的浮點剖析和格式改善](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)的「對現有程式碼的潛在影響」一節會建議您對程式碼所做的變更，如果您發現與 .net Core 2.2 應用程式相較之下的行為變更，這牽涉到使用不同的標準或自訂格式字串來強制執行所需的行為。</span><span class="sxs-lookup"><span data-stu-id="ab970-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="ab970-114">某些結果若先前不正確，可能不會有因應措施。</span><span class="sxs-lookup"><span data-stu-id="ab970-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="ab970-115">分類</span><span class="sxs-lookup"><span data-stu-id="ab970-115">Category</span></span>

<span data-ttu-id="ab970-116">CoreFx</span><span class="sxs-lookup"><span data-stu-id="ab970-116">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ab970-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ab970-117">Affected APIs</span></span>

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
