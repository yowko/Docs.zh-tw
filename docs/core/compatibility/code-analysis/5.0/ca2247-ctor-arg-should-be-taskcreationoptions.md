---
title: 重大變更： CA2247： >taskcompletionsource 的引數應為 TaskCreationOptions 值
description: 瞭解 .NET 5.0 中因為啟用程式碼分析規則 CA2247 所造成的重大變更。
ms.date: 09/03/2020
ms.openlocfilehash: 323fd5a05da4dfeb68ef75d88d5d293ba01c8ade
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760709"
---
# <a name="warning-ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a><span data-ttu-id="8825d-103">警告 CA2247： >taskcompletionsource 的引數應為 TaskCreationOptions 值</span><span class="sxs-lookup"><span data-stu-id="8825d-103">Warning CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>

<span data-ttu-id="8825d-104">預設會啟用 .NET 程式碼分析器規則 [CA2247](/visualstudio/code-quality/ca2247) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="8825d-104">.NET code analyzer rule [CA2247](/visualstudio/code-quality/ca2247) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="8825d-105">它會針對傳遞型別引數的函式呼叫產生組建警告 <xref:System.Threading.Tasks.TaskCompletionSource%601> <xref:System.Threading.Tasks.TaskContinuationOptions> 。</span><span class="sxs-lookup"><span data-stu-id="8825d-105">It produces a build warning for calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span>

## <a name="change-description"></a><span data-ttu-id="8825d-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="8825d-106">Change description</span></span>

<span data-ttu-id="8825d-107">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../fundamentals/code-analysis/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="8825d-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="8825d-108">預設會啟用這些規則中的數個，包括 [CA2247](/visualstudio/code-quality/ca2247)。</span><span class="sxs-lookup"><span data-stu-id="8825d-108">Several of these rules are enabled, by default, including [CA2247](/visualstudio/code-quality/ca2247).</span></span> <span data-ttu-id="8825d-109">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="8825d-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="8825d-110">規則 CA2247 <xref:System.Threading.Tasks.TaskCompletionSource%601> 會尋找傳遞型別引數之函式的呼叫 <xref:System.Threading.Tasks.TaskContinuationOptions> 。</span><span class="sxs-lookup"><span data-stu-id="8825d-110">Rule CA2247 finds calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span> <span data-ttu-id="8825d-111"><xref:System.Threading.Tasks.TaskCompletionSource%601>型別具有接受值的函式 <xref:System.Threading.Tasks.TaskCreationOptions> ，以及接受的另一個函式 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="8825d-111">The <xref:System.Threading.Tasks.TaskCompletionSource%601> type has a constructor that accepts a <xref:System.Threading.Tasks.TaskCreationOptions> value, and another constructor that accepts an <xref:System.Object>.</span></span> <span data-ttu-id="8825d-112">如果您不小心傳遞 <xref:System.Threading.Tasks.TaskContinuationOptions> 值而非 <xref:System.Threading.Tasks.TaskCreationOptions> 值，則 <xref:System.Object> 會在執行時間呼叫具有參數的函式。</span><span class="sxs-lookup"><span data-stu-id="8825d-112">If you accidentally pass a <xref:System.Threading.Tasks.TaskContinuationOptions> value instead of a <xref:System.Threading.Tasks.TaskCreationOptions> value, the constructor with the <xref:System.Object> parameter is called at run time.</span></span> <span data-ttu-id="8825d-113">您的程式碼會編譯並執行，但不會有預期的行為。</span><span class="sxs-lookup"><span data-stu-id="8825d-113">Your code will compile and run but won't have the intended behavior.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8825d-114">引進的版本</span><span class="sxs-lookup"><span data-stu-id="8825d-114">Version introduced</span></span>

<span data-ttu-id="8825d-115">5.0</span><span class="sxs-lookup"><span data-stu-id="8825d-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8825d-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="8825d-116">Recommended action</span></span>

- <span data-ttu-id="8825d-117"><xref:System.Threading.Tasks.TaskContinuationOptions>以對應的值取代自 <xref:System.Threading.Tasks.TaskCreationOptions> 變數。</span><span class="sxs-lookup"><span data-stu-id="8825d-117">Replace the <xref:System.Threading.Tasks.TaskContinuationOptions> argument with the corresponding <xref:System.Threading.Tasks.TaskCreationOptions> value.</span></span> <span data-ttu-id="8825d-118">請勿隱藏此警告，因為它幾乎一律會在您的程式碼中反白顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="8825d-118">Do not suppress this warning, since it almost always highlights a bug in your code.</span></span> <span data-ttu-id="8825d-119">如需詳細資訊，請參閱 [CA2247](/visualstudio/code-quality/ca2247)。</span><span class="sxs-lookup"><span data-stu-id="8825d-119">For more information, see [CA2247](/visualstudio/code-quality/ca2247).</span></span>

- <span data-ttu-id="8825d-120">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="8825d-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="8825d-121">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="8825d-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8825d-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="8825d-122">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

### Category

Code analysis

-->
