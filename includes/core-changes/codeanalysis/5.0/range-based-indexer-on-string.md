---
ms.openlocfilehash: 4e937f56f6315ce2abf76dd56989f4d2c4059f22
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598065"
---
### <a name="ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a><span data-ttu-id="57708-101">CA1831：針對字串使用 AsSpan 而非以範圍為基礎的索引子</span><span class="sxs-lookup"><span data-stu-id="57708-101">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>

<span data-ttu-id="57708-102">預設會啟用 .NET 程式碼分析器規則 [CA1831](/visualstudio/code-quality/ca1831) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="57708-102">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="57708-103">它會產生任何程式碼的組建警告 <xref:System.Range> ，其中使用以字串為基礎的索引子，但未預期複製。</span><span class="sxs-lookup"><span data-stu-id="57708-103">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

#### <a name="change-description"></a><span data-ttu-id="57708-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="57708-104">Change description</span></span>

<span data-ttu-id="57708-105">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="57708-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="57708-106">預設會啟用這些規則中的數個，包括 [CA1831](/visualstudio/code-quality/ca1831)。</span><span class="sxs-lookup"><span data-stu-id="57708-106">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="57708-107">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="57708-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="57708-108">[規則 CA1831] 會尋找在 <xref:System.Range> 字串上使用以 a 為基礎之索引子的實例，但不會提供任何複本。</span><span class="sxs-lookup"><span data-stu-id="57708-108">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="57708-109">如果 <xref:System.Range> 以直接在字串上使用的索引子來產生隱含轉換，則會建立字串所要求部分的不必要複本。</span><span class="sxs-lookup"><span data-stu-id="57708-109">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="57708-110">例如：</span><span class="sxs-lookup"><span data-stu-id="57708-110">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="57708-111">CA1831 建議您 <xref:System.Range> 改為在字串 *範圍* 上使用以型索引子為基礎的索引子。</span><span class="sxs-lookup"><span data-stu-id="57708-111">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="57708-112">例如：</span><span class="sxs-lookup"><span data-stu-id="57708-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

#### <a name="version-introduced"></a><span data-ttu-id="57708-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="57708-113">Version introduced</span></span>

<span data-ttu-id="57708-114">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="57708-114">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="57708-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="57708-115">Recommended action</span></span>

- <span data-ttu-id="57708-116">若要修正您的程式碼，並避免不必要的配置，請 <xref:System.MemoryExtensions.AsSpan(System.String)> <xref:System.MemoryExtensions.AsMemory(System.String)> 在使用 <xref:System.Range> 型索引子之前呼叫或。</span><span class="sxs-lookup"><span data-stu-id="57708-116">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="57708-117">例如：</span><span class="sxs-lookup"><span data-stu-id="57708-117">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="57708-118">如果您不想變更您的程式碼，您可以將規則的嚴重性設定為或，以停用此規則 `suggestion` `none` 。</span><span class="sxs-lookup"><span data-stu-id="57708-118">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="57708-119">如需詳細資訊，請參閱 [設定程式碼分析規則](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md)。</span><span class="sxs-lookup"><span data-stu-id="57708-119">For more information, see [Configure code analysis rules](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span></span>

- <span data-ttu-id="57708-120">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="57708-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="57708-121">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="57708-121">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="57708-122">類別</span><span class="sxs-lookup"><span data-stu-id="57708-122">Category</span></span>

<span data-ttu-id="57708-123">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="57708-123">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="57708-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="57708-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Range`

-->
