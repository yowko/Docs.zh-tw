---
ms.openlocfilehash: b697bbf6844759de8babd4245667e7b333884ff8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538916"
---
### <a name="ca2200-rethrow-to-preserve-stack-details"></a><span data-ttu-id="01f99-101">CA2200:必須重新擲回以保存堆疊詳細資料</span><span class="sxs-lookup"><span data-stu-id="01f99-101">CA2200: Rethrow to preserve stack details</span></span>

<span data-ttu-id="01f99-102">預設會啟用 .NET 程式碼分析器規則 [CA2200](/visualstudio/code-quality/ca2200) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="01f99-102">.NET code analyzer rule [CA2200](/visualstudio/code-quality/ca2200) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="01f99-103">它會針對重新擲回例外狀況的任何區塊產生組建警告 `catch` ，並在語句中明確指定例外狀況 `throw` 。</span><span class="sxs-lookup"><span data-stu-id="01f99-103">It produces a build warning for any `catch` blocks that rethrow an exception and the exception is explicitly specified in the `throw` statement.</span></span>

#### <a name="change-description"></a><span data-ttu-id="01f99-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="01f99-104">Change description</span></span>

<span data-ttu-id="01f99-105">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="01f99-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="01f99-106">預設會啟用這些規則中的數個，包括 [CA2200](/visualstudio/code-quality/ca2200)。</span><span class="sxs-lookup"><span data-stu-id="01f99-106">Several of these rules are enabled, by default, including [CA2200](/visualstudio/code-quality/ca2200).</span></span> <span data-ttu-id="01f99-107">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="01f99-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="01f99-108">規則 CA2200 會將擲回例外狀況的程式碼加上旗標，並在語句中指定例外狀況變數 `throw` 。</span><span class="sxs-lookup"><span data-stu-id="01f99-108">Rule CA2200 flags code where exceptions are rethrown and the exception variable is specified in the `throw` statement.</span></span> <span data-ttu-id="01f99-109">擲回例外狀況時，它所攜帶的部分資訊就是堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="01f99-109">When an exception is thrown, part of the information it carries is the stack trace.</span></span> <span data-ttu-id="01f99-110">堆疊追蹤是方法呼叫階層的清單，其開頭為擲回例外狀況的方法，並以捕捉例外狀況的方法結束。</span><span class="sxs-lookup"><span data-stu-id="01f99-110">The stack trace is a list of the method call hierarchy that starts with the method that throws the exception and ends with the method that catches the exception.</span></span> <span data-ttu-id="01f99-111">如果在語句中指定例外狀況而重新擲回例外狀況 `throw` ，堆疊追蹤會在目前的方法重新開機，並在擲回例外狀況的原始方法與目前方法遺失之間的方法呼叫清單中重新開機。</span><span class="sxs-lookup"><span data-stu-id="01f99-111">If an exception is rethrown by specifying the exception in the `throw` statement, the stack trace restarts at the current method and the list of method calls between the original method that threw the exception and the current method is lost.</span></span> <span data-ttu-id="01f99-112">若要保留原始堆疊追蹤資訊的例外狀況，請使用 `throw` 語句而不指定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="01f99-112">To keep the original stack trace information with the exception, use the `throw` statement without specifying the exception.</span></span>

<span data-ttu-id="01f99-113">下列程式碼片段不會產生規則 CA2200 的警告。</span><span class="sxs-lookup"><span data-stu-id="01f99-113">The following code snippet does not produce a warning for rule CA2200.</span></span> <span data-ttu-id="01f99-114">不過，批註的程式程式碼 *會* 觸發違規。</span><span class="sxs-lookup"><span data-stu-id="01f99-114">The commented line *would* trigger a violation, however.</span></span>

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

#### <a name="version-introduced"></a><span data-ttu-id="01f99-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="01f99-115">Version introduced</span></span>

<span data-ttu-id="01f99-116">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="01f99-116">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="01f99-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="01f99-117">Recommended action</span></span>

- <span data-ttu-id="01f99-118">重新擲回例外狀況，而不明確指定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="01f99-118">Rethrow exceptions without specifying the exception explicitly.</span></span> <span data-ttu-id="01f99-119">如需詳細資訊，請參閱 [CA2200](/visualstudio/code-quality/ca2200)。</span><span class="sxs-lookup"><span data-stu-id="01f99-119">For more information, see [CA2200](/visualstudio/code-quality/ca2200).</span></span>

- <span data-ttu-id="01f99-120">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="01f99-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="01f99-121">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="01f99-121">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="01f99-122">類別</span><span class="sxs-lookup"><span data-stu-id="01f99-122">Category</span></span>

<span data-ttu-id="01f99-123">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="01f99-123">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="01f99-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="01f99-124">Affected APIs</span></span>

<span data-ttu-id="01f99-125">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="01f99-125">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
