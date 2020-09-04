---
ms.openlocfilehash: a51160a8ab5a4b437e51db31def577f8d8f50182
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465562"
---
### <a name="ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="0f3f0-101">CA2014：請勿在迴圈中使用 stackalloc</span><span class="sxs-lookup"><span data-stu-id="0f3f0-101">CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="0f3f0-102">預設會啟用 .NET 程式碼分析器規則 [CA2014](/visualstudio/code-quality/ca2014) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-102">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="0f3f0-103">它會針對在迴圈內使用 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 運算式的任何 c # 程式碼產生組建警告。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-103">It produces a build warning for any C# code where a [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0f3f0-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="0f3f0-104">Change description</span></span>

<span data-ttu-id="0f3f0-105">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="0f3f0-106">預設會啟用這些規則中的數個，包括 [CA2014](/visualstudio/code-quality/ca2014)。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-106">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="0f3f0-107">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="0f3f0-108">規則 CA2014 會尋找在迴圈內使用 [stackalloc 運算式](../../../../docs/csharp/language-reference/operators/stackalloc.md) 的 c # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-108">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../docs/csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="0f3f0-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 會從目前的堆疊框架配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="0f3f0-110">在目前的方法呼叫傳回之前，不會釋放記憶體，這可能會導致堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-110">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="0f3f0-111">由於您無法攔截堆疊溢位例外狀況，因此應用程式會在發生堆疊溢位時終止。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-111">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0f3f0-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0f3f0-112">Version introduced</span></span>

<span data-ttu-id="0f3f0-113">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="0f3f0-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0f3f0-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0f3f0-114">Recommended action</span></span>

- <span data-ttu-id="0f3f0-115">避免在迴圈內使用 [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) 。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-115">Avoid using [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="0f3f0-116">在迴圈之外配置記憶體區塊，並在迴圈內重複使用它。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-116">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="0f3f0-117">如需詳細資訊，請參閱 [CA2014](/visualstudio/code-quality/ca2014)。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-117">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="0f3f0-118">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="0f3f0-119">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-119">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="0f3f0-120">類別</span><span class="sxs-lookup"><span data-stu-id="0f3f0-120">Category</span></span>

<span data-ttu-id="0f3f0-121">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="0f3f0-121">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f3f0-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0f3f0-122">Affected APIs</span></span>

<span data-ttu-id="0f3f0-123">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-123">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
