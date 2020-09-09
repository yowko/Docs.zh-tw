---
ms.openlocfilehash: b01424c63d6e7956127bf889c53422b60ba2f219
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598073"
---
### <a name="ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="e7a4d-101">CA2013：請勿使用具有值類型的 ReferenceEquals</span><span class="sxs-lookup"><span data-stu-id="e7a4d-101">CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="e7a4d-102">預設會啟用 .NET 程式碼分析器規則 [CA2013](/visualstudio/code-quality/ca2013) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-102">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="e7a4d-103">它會針對 <xref:System.Object.ReferenceEquals(System.Object,System.Object)> 用來比較一或多個數值型別是否相等的任何程式碼產生組建警告。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-103">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e7a4d-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="e7a4d-104">Change description</span></span>

<span data-ttu-id="e7a4d-105">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="e7a4d-106">預設會啟用這些規則中的數個，包括 [CA2013](/visualstudio/code-quality/ca2013)。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-106">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="e7a4d-107">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="e7a4d-108">[規則 CA2013] <xref:System.Object.ReferenceEquals(System.Object,System.Object)> 會尋找用來比較一或多個數值型別是否相等的實例。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-108">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="e7a4d-109">以這種方式比較相等的數值型別可能會導致不正確的結果，因為這些值會在比較之前先進行過迭。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-109">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="e7a4d-110"><xref:System.Object.ReferenceEquals(System.Object,System.Object)>`false`即使比較的值代表實值型別的實例，也會傳回。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-110"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e7a4d-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e7a4d-111">Version introduced</span></span>

<span data-ttu-id="e7a4d-112">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="e7a4d-112">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e7a4d-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e7a4d-113">Recommended action</span></span>

- <span data-ttu-id="e7a4d-114">將程式碼變更為使用適當的等號比較運算子，例如 `==` 。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-114">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="e7a4d-115">您不應該隱藏這個警告。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-115">You should not suppress this warning.</span></span>

- <span data-ttu-id="e7a4d-116">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-116">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="e7a4d-117">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="e7a4d-117">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="e7a4d-118">類別</span><span class="sxs-lookup"><span data-stu-id="e7a4d-118">Category</span></span>

<span data-ttu-id="e7a4d-119">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="e7a4d-119">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7a4d-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e7a4d-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

-->
