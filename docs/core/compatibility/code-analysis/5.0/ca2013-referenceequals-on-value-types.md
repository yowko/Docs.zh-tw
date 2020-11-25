---
title: 重大變更： CA2013：不使用具有實數值型別的 ReferenceEquals
description: 瞭解 .NET 5.0 中因為啟用程式碼分析規則 CA2013 所造成的重大變更。
ms.date: 09/03/2020
ms.openlocfilehash: ca2b845427eff547b996b577394c6859e30f50bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760428"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="9c805-103">警告 CA2013：不使用具有實數值型別的 ReferenceEquals</span><span class="sxs-lookup"><span data-stu-id="9c805-103">Warning CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="9c805-104">預設會啟用 .NET 程式碼分析器規則 [CA2013](/visualstudio/code-quality/ca2013) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="9c805-104">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="9c805-105">它會針對 <xref:System.Object.ReferenceEquals(System.Object,System.Object)> 用來比較一或多個數值型別是否相等的任何程式碼產生組建警告。</span><span class="sxs-lookup"><span data-stu-id="9c805-105">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

## <a name="change-description"></a><span data-ttu-id="9c805-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="9c805-106">Change description</span></span>

<span data-ttu-id="9c805-107">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../fundamentals/code-analysis/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9c805-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="9c805-108">預設會啟用這些規則中的數個，包括 [CA2013](/visualstudio/code-quality/ca2013)。</span><span class="sxs-lookup"><span data-stu-id="9c805-108">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="9c805-109">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="9c805-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="9c805-110">[規則 CA2013] <xref:System.Object.ReferenceEquals(System.Object,System.Object)> 會尋找用來比較一或多個數值型別是否相等的實例。</span><span class="sxs-lookup"><span data-stu-id="9c805-110">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="9c805-111">以這種方式比較相等的數值型別可能會導致不正確的結果，因為這些值會在比較之前先進行過迭。</span><span class="sxs-lookup"><span data-stu-id="9c805-111">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="9c805-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)>`false`即使比較的值代表實值型別的實例，也會傳回。</span><span class="sxs-lookup"><span data-stu-id="9c805-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9c805-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9c805-113">Version introduced</span></span>

<span data-ttu-id="9c805-114">5.0</span><span class="sxs-lookup"><span data-stu-id="9c805-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9c805-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9c805-115">Recommended action</span></span>

- <span data-ttu-id="9c805-116">將程式碼變更為使用適當的等號比較運算子，例如 `==` 。</span><span class="sxs-lookup"><span data-stu-id="9c805-116">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="9c805-117">您不應該隱藏這個警告。</span><span class="sxs-lookup"><span data-stu-id="9c805-117">You should not suppress this warning.</span></span>

- <span data-ttu-id="9c805-118">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="9c805-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="9c805-119">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="9c805-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9c805-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9c805-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->
