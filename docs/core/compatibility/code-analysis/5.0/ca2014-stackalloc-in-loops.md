---
title: 重大變更： CA2014：不要在迴圈中使用 stackalloc
description: 瞭解 .NET 5.0 中因為啟用程式碼分析規則 CA2014 所造成的重大變更。
ms.date: 09/03/2020
ms.openlocfilehash: 7ad6203c0edd930bbbe43cdb8df0413cba833d8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760427"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="76362-103">警告 CA2014：不要在迴圈中使用 stackalloc</span><span class="sxs-lookup"><span data-stu-id="76362-103">Warning CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="76362-104">預設會啟用 .NET 程式碼分析器規則 [CA2014](/visualstudio/code-quality/ca2014) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="76362-104">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="76362-105">它會針對在迴圈內使用 [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) 運算式的任何 c # 程式碼產生組建警告。</span><span class="sxs-lookup"><span data-stu-id="76362-105">It produces a build warning for any C# code where a [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

## <a name="change-description"></a><span data-ttu-id="76362-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="76362-106">Change description</span></span>

<span data-ttu-id="76362-107">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../fundamentals/code-analysis/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="76362-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="76362-108">預設會啟用這些規則中的數個，包括 [CA2014](/visualstudio/code-quality/ca2014)。</span><span class="sxs-lookup"><span data-stu-id="76362-108">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="76362-109">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="76362-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="76362-110">規則 CA2014 會尋找在迴圈內使用 [stackalloc 運算式](../../../../csharp/language-reference/operators/stackalloc.md) 的 c # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="76362-110">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="76362-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) 會從目前的堆疊框架配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="76362-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="76362-112">在目前的方法呼叫傳回之前，不會釋放記憶體，這可能會導致堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="76362-112">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="76362-113">由於您無法攔截堆疊溢位例外狀況，因此應用程式會在發生堆疊溢位時終止。</span><span class="sxs-lookup"><span data-stu-id="76362-113">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="76362-114">引進的版本</span><span class="sxs-lookup"><span data-stu-id="76362-114">Version introduced</span></span>

<span data-ttu-id="76362-115">5.0</span><span class="sxs-lookup"><span data-stu-id="76362-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="76362-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="76362-116">Recommended action</span></span>

- <span data-ttu-id="76362-117">避免在迴圈內使用 [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) 。</span><span class="sxs-lookup"><span data-stu-id="76362-117">Avoid using [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="76362-118">在迴圈之外配置記憶體區塊，並在迴圈內重複使用它。</span><span class="sxs-lookup"><span data-stu-id="76362-118">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="76362-119">如需詳細資訊，請參閱 [CA2014](/visualstudio/code-quality/ca2014)。</span><span class="sxs-lookup"><span data-stu-id="76362-119">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="76362-120">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="76362-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="76362-121">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="76362-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="76362-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="76362-122">Affected APIs</span></span>

<span data-ttu-id="76362-123">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="76362-123">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
