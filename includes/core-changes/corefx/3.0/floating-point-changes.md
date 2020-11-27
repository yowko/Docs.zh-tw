---
ms.openlocfilehash: 719f336e1b38597674d6ee8f0c5429dd965054b1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032012"
---
### <a name="floating-point-formatting-and-parsing-behavior-changed"></a><span data-ttu-id="18c41-101">浮點數格式化和剖析行為已變更</span><span class="sxs-lookup"><span data-stu-id="18c41-101">Floating-point formatting and parsing behavior changed</span></span>

<span data-ttu-id="18c41-102">和類型)  (的浮點剖析和格式化 <xref:System.Double> 行為 <xref:System.Single> 現在符合 IEEE 標準。</span><span class="sxs-lookup"><span data-stu-id="18c41-102">Floating point parsing and formatting behavior (by the <xref:System.Double> and <xref:System.Single> types) are now IEEE-compliant.</span></span>

#### <a name="change-description"></a><span data-ttu-id="18c41-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="18c41-103">Change description</span></span>

<span data-ttu-id="18c41-104">在 .net Core 2.2 及更早版本中，使用和進行格式化， <xref:System.Double.ToString%2A?displayProperty=nameWithType> <xref:System.Single.ToString%2A?displayProperty=nameWithType> 並使用、、和進行剖析，並 <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> 不符合 IEEE 規範。</span><span class="sxs-lookup"><span data-stu-id="18c41-104">In .NET Core 2.2 and earlier versions, formatting with <xref:System.Double.ToString%2A?displayProperty=nameWithType> and <xref:System.Single.ToString%2A?displayProperty=nameWithType>, and parsing with <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, and <xref:System.Single.TryParse%2A?displayProperty=nameWithType> are not IEEE-compliant.</span></span> <span data-ttu-id="18c41-105">如此一來，就無法保證某個值會往返任何支援的標準或自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="18c41-105">As a result, it is impossible to guarantee that a value will roundtrip with any supported standard or custom format string.</span></span> <span data-ttu-id="18c41-106">針對某些輸入，嘗試剖析格式化的值可能會失敗，而針對其他輸入，剖析的值不等於原始值。</span><span class="sxs-lookup"><span data-stu-id="18c41-106">For some inputs, the attempt to parse a formatted value can fail, and for others, the parsed value doesn't equal the original value.</span></span>

<span data-ttu-id="18c41-107">從 .NET Core 3.0 開始，剖析和格式化作業符合 IEEE 754 規範。</span><span class="sxs-lookup"><span data-stu-id="18c41-107">Starting with .NET Core 3.0, parsing and formatting operations are IEEE 754-compliant.</span></span> <span data-ttu-id="18c41-108">這可確保 .NET 中的浮點類型行為符合符合 IEEE 標準的語言，例如 c #。</span><span class="sxs-lookup"><span data-stu-id="18c41-108">This ensures that the behavior of floating-point types in .NET matches that of IEEE-compliant languages such as C#.</span></span> <span data-ttu-id="18c41-109">如需詳細資訊，請參閱 [.Net Core 3.0 blog 文章中的浮點剖析和格式改進](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) 。</span><span class="sxs-lookup"><span data-stu-id="18c41-109">For more information, see the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="18c41-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="18c41-110">Version introduced</span></span>

<span data-ttu-id="18c41-111">3.0</span><span class="sxs-lookup"><span data-stu-id="18c41-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="18c41-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="18c41-112">Recommended action</span></span>

<span data-ttu-id="18c41-113">[.Net core 3.0 的浮點剖析和格式化增強功能](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)的「對現有程式碼的潛在影響」一節會建議您變更程式碼，如果您在與 .net core 2.2 應用程式相較之下觀察到行為有所改變，則需要使用不同的標準或自訂格式字串來強制執行所需的行為。</span><span class="sxs-lookup"><span data-stu-id="18c41-113">The "Potential impact to existing code" section of the [Floating-point parsing and formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post suggests changes to your code if you observe a change of behavior when compared to .NET Core 2.2 applications Generally, this involves using a different standard or custom format string to enforce the desired behavior.</span></span> <span data-ttu-id="18c41-114">如果先前的結果不正確，則可能無法解決此問題。</span><span class="sxs-lookup"><span data-stu-id="18c41-114">Some results may not have a workaround if they were previously incorrect.</span></span>

#### <a name="category"></a><span data-ttu-id="18c41-115">類別</span><span class="sxs-lookup"><span data-stu-id="18c41-115">Category</span></span>

<span data-ttu-id="18c41-116">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="18c41-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="18c41-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="18c41-117">Affected APIs</span></span>

- <xref:System.Double.ToString%2A?displayProperty=nameWithType>
- <xref:System.Single.ToString%2A?displayProperty=nameWithType>
- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `Overload:System.Double.ToString`
- `Overload:System.Single.ToString`
- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
