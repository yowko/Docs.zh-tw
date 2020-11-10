---
ms.openlocfilehash: 0ba77a6a6ac0e2d29036635ea3cdb9ba9a9da10e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440170"
---
### <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a><span data-ttu-id="43ca8-101">LastIndexOf 已改善空白搜尋字串的處理</span><span class="sxs-lookup"><span data-stu-id="43ca8-101">LastIndexOf has improved handling of empty search strings</span></span>

<span data-ttu-id="43ca8-102"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> 而相關的 Api 現在會在搜尋長度為零的 (或較大的字串中) 長度相等的子字串時，傳回正確的值。</span><span class="sxs-lookup"><span data-stu-id="43ca8-102"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs now return correct values when searching for a zero-length (or zero-length equivalent) substring within a larger string.</span></span>

#### <a name="change-description"></a><span data-ttu-id="43ca8-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="43ca8-103">Change description</span></span>

<span data-ttu-id="43ca8-104">在 .NET Framework 和 .NET Core 1.0-3.1 中， <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> 當呼叫端搜尋零長度的子字串時，相關的 api 可能會傳回不正確的值。</span><span class="sxs-lookup"><span data-stu-id="43ca8-104">In .NET Framework and .NET Core 1.0 - 3.1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs might return an incorrect value when the caller searches for a zero-length substring.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

<span data-ttu-id="43ca8-105">從 .NET 5.0 開始，這些 Api 會傳回的正確值 `LastIndexOf` 。</span><span class="sxs-lookup"><span data-stu-id="43ca8-105">Starting with .NET 5.0, these APIs return the correct value for `LastIndexOf`.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

<span data-ttu-id="43ca8-106">在這些範例中， `5` 是正確的答案，因為 `"Hello".Substring(5)` 和 `"Hello".AsSpan().Slice(5)` 兩者都會產生空字串，其完整等於所搜尋的空白子字串。</span><span class="sxs-lookup"><span data-stu-id="43ca8-106">In these examples, `5` is the correct answer because `"Hello".Substring(5)` and `"Hello".AsSpan().Slice(5)` both produce an empty string, which is trivially equal to the empty substring that is sought.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="43ca8-107">變更的原因</span><span class="sxs-lookup"><span data-stu-id="43ca8-107">Reason for change</span></span>

<span data-ttu-id="43ca8-108">這項變更是在 .NET 5 的字串處理方面的整體 bug 修正工作的一部分。</span><span class="sxs-lookup"><span data-stu-id="43ca8-108">This change was part of an overall bug fixing effort around string handling for .NET 5.</span></span> <span data-ttu-id="43ca8-109">它也可協助統一 Windows 與非 Windows 平臺之間的行為。</span><span class="sxs-lookup"><span data-stu-id="43ca8-109">It also helps unify our behavior between Windows and non-Windows platforms.</span></span> <span data-ttu-id="43ca8-110">如需詳細資訊，請參閱 [dotnet/runtime # 13383](https://github.com/dotnet/runtime/issues/13383) 和 [dotnet/runtime # #13382](https://github.com/dotnet/runtime/issues/13382)。</span><span class="sxs-lookup"><span data-stu-id="43ca8-110">For more information, see [dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) and [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="43ca8-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="43ca8-111">Version introduced</span></span>

<span data-ttu-id="43ca8-112">5.0</span><span class="sxs-lookup"><span data-stu-id="43ca8-112">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="43ca8-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="43ca8-113">Recommended action</span></span>

<span data-ttu-id="43ca8-114">您不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="43ca8-114">You don't need to take any action.</span></span> <span data-ttu-id="43ca8-115">.NET 5.0 執行時間會自動提供新的行為。</span><span class="sxs-lookup"><span data-stu-id="43ca8-115">The .NET 5.0 runtime provides the new behaviors automatically.</span></span>

<span data-ttu-id="43ca8-116">沒有相容性參數可以還原舊行為。</span><span class="sxs-lookup"><span data-stu-id="43ca8-116">There is no compatibility switch to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="43ca8-117">類別</span><span class="sxs-lookup"><span data-stu-id="43ca8-117">Category</span></span>

<span data-ttu-id="43ca8-118">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="43ca8-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="43ca8-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="43ca8-119">Affected APIs</span></span>

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->
