---
title: 重大變更： CA2200：重新擲回以保留堆疊詳細資料
description: 瞭解 .NET 5.0 中因為啟用程式碼分析規則 CA2200 所造成的重大變更。
ms.date: 09/03/2020
ms.openlocfilehash: 74e169906a8b826328de8d4c5f69c32234c2ce95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760708"
---
# <a name="warning-ca2200-rethrow-to-preserve-stack-details"></a><span data-ttu-id="e8d51-103">警告 CA2200：重新擲回以保留堆疊詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8d51-103">Warning CA2200: Rethrow to preserve stack details</span></span>

<span data-ttu-id="e8d51-104">預設會啟用 .NET 程式碼分析器規則 [CA2200](/visualstudio/code-quality/ca2200) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="e8d51-104">.NET code analyzer rule [CA2200](/visualstudio/code-quality/ca2200) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="e8d51-105">它會針對重新擲回例外狀況的任何區塊產生組建警告 `catch` ，並在語句中明確指定例外狀況 `throw` 。</span><span class="sxs-lookup"><span data-stu-id="e8d51-105">It produces a build warning for any `catch` blocks that rethrow an exception and the exception is explicitly specified in the `throw` statement.</span></span>

## <a name="change-description"></a><span data-ttu-id="e8d51-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="e8d51-106">Change description</span></span>

<span data-ttu-id="e8d51-107">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../fundamentals/code-analysis/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e8d51-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="e8d51-108">預設會啟用這些規則中的數個，包括 [CA2200](/visualstudio/code-quality/ca2200)。</span><span class="sxs-lookup"><span data-stu-id="e8d51-108">Several of these rules are enabled, by default, including [CA2200](/visualstudio/code-quality/ca2200).</span></span> <span data-ttu-id="e8d51-109">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="e8d51-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="e8d51-110">規則 CA2200 會將擲回例外狀況的程式碼加上旗標，並在語句中指定例外狀況變數 `throw` 。</span><span class="sxs-lookup"><span data-stu-id="e8d51-110">Rule CA2200 flags code where exceptions are rethrown and the exception variable is specified in the `throw` statement.</span></span> <span data-ttu-id="e8d51-111">擲回例外狀況時，它所攜帶的部分資訊就是堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="e8d51-111">When an exception is thrown, part of the information it carries is the stack trace.</span></span> <span data-ttu-id="e8d51-112">堆疊追蹤是方法呼叫階層的清單，其開頭為擲回例外狀況的方法，並以捕捉例外狀況的方法結束。</span><span class="sxs-lookup"><span data-stu-id="e8d51-112">The stack trace is a list of the method call hierarchy that starts with the method that throws the exception and ends with the method that catches the exception.</span></span> <span data-ttu-id="e8d51-113">如果在語句中指定例外狀況而重新擲回例外狀況 `throw` ，堆疊追蹤會在目前的方法重新開機，並在擲回例外狀況的原始方法與目前方法遺失之間的方法呼叫清單中重新開機。</span><span class="sxs-lookup"><span data-stu-id="e8d51-113">If an exception is rethrown by specifying the exception in the `throw` statement, the stack trace restarts at the current method and the list of method calls between the original method that threw the exception and the current method is lost.</span></span> <span data-ttu-id="e8d51-114">若要保留原始堆疊追蹤資訊的例外狀況，請使用 `throw` 語句而不指定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e8d51-114">To keep the original stack trace information with the exception, use the `throw` statement without specifying the exception.</span></span>

<span data-ttu-id="e8d51-115">下列程式碼片段不會產生規則 CA2200 的警告。</span><span class="sxs-lookup"><span data-stu-id="e8d51-115">The following code snippet does not produce a warning for rule CA2200.</span></span> <span data-ttu-id="e8d51-116">不過，批註的程式程式碼 *會* 觸發違規。</span><span class="sxs-lookup"><span data-stu-id="e8d51-116">The commented line *would* trigger a violation, however.</span></span>

```csharp
catch (ArithmeticException e)
{
    // throw e;
    throw;
}
```

## <a name="version-introduced"></a><span data-ttu-id="e8d51-117">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e8d51-117">Version introduced</span></span>

<span data-ttu-id="e8d51-118">5.0</span><span class="sxs-lookup"><span data-stu-id="e8d51-118">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e8d51-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e8d51-119">Recommended action</span></span>

- <span data-ttu-id="e8d51-120">重新擲回例外狀況，而不明確指定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e8d51-120">Rethrow exceptions without specifying the exception explicitly.</span></span> <span data-ttu-id="e8d51-121">如需詳細資訊，請參閱 [CA2200](/visualstudio/code-quality/ca2200)。</span><span class="sxs-lookup"><span data-stu-id="e8d51-121">For more information, see [CA2200](/visualstudio/code-quality/ca2200).</span></span>

- <span data-ttu-id="e8d51-122">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="e8d51-122">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="e8d51-123">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="e8d51-123">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e8d51-124">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e8d51-124">Affected APIs</span></span>

<span data-ttu-id="e8d51-125">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="e8d51-125">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
