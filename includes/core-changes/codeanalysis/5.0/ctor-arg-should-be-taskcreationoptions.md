---
ms.openlocfilehash: 6bb3b11ef4e4cb6f6a039c97911b0acca862fe6f
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465563"
---
### <a name="ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a><span data-ttu-id="df5c6-101">CA2247： >taskcompletionsource 的引數應為 TaskCreationOptions 值</span><span class="sxs-lookup"><span data-stu-id="df5c6-101">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>

<span data-ttu-id="df5c6-102">預設會啟用 .NET 程式碼分析器規則 [CA2247](/visualstudio/code-quality/ca2247) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="df5c6-102">.NET code analyzer rule [CA2247](/visualstudio/code-quality/ca2247) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="df5c6-103">它會針對傳遞型別引數的函式呼叫產生組建警告 <xref:System.Threading.Tasks.TaskCompletionSource%601> <xref:System.Threading.Tasks.TaskContinuationOptions> 。</span><span class="sxs-lookup"><span data-stu-id="df5c6-103">It produces a build warning for calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="df5c6-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="df5c6-104">Change description</span></span>

<span data-ttu-id="df5c6-105">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="df5c6-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="df5c6-106">預設會啟用這些規則中的數個，包括 [CA2247](/visualstudio/code-quality/ca2247)。</span><span class="sxs-lookup"><span data-stu-id="df5c6-106">Several of these rules are enabled, by default, including [CA2247](/visualstudio/code-quality/ca2247).</span></span> <span data-ttu-id="df5c6-107">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="df5c6-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="df5c6-108">規則 CA2247 <xref:System.Threading.Tasks.TaskCompletionSource%601> 會尋找傳遞型別引數之函式的呼叫 <xref:System.Threading.Tasks.TaskContinuationOptions> 。</span><span class="sxs-lookup"><span data-stu-id="df5c6-108">Rule CA2247 finds calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span> <span data-ttu-id="df5c6-109"><xref:System.Threading.Tasks.TaskCompletionSource%601>型別具有接受值的函式 <xref:System.Threading.Tasks.TaskCreationOptions> ，以及接受的另一個函式 <xref:System.Object> 。</span><span class="sxs-lookup"><span data-stu-id="df5c6-109">The <xref:System.Threading.Tasks.TaskCompletionSource%601> type has a constructor that accepts a <xref:System.Threading.Tasks.TaskCreationOptions> value, and another constructor that accepts an <xref:System.Object>.</span></span> <span data-ttu-id="df5c6-110">如果您不小心傳遞 <xref:System.Threading.Tasks.TaskContinuationOptions> 值而非 <xref:System.Threading.Tasks.TaskCreationOptions> 值，則 <xref:System.Object> 會在執行時間呼叫具有參數的函式。</span><span class="sxs-lookup"><span data-stu-id="df5c6-110">If you accidentally pass a <xref:System.Threading.Tasks.TaskContinuationOptions> value instead of a <xref:System.Threading.Tasks.TaskCreationOptions> value, the constructor with the <xref:System.Object> parameter is called at run time.</span></span> <span data-ttu-id="df5c6-111">您的程式碼會編譯並執行，但不會有預期的行為。</span><span class="sxs-lookup"><span data-stu-id="df5c6-111">Your code will compile and run but won't have the intended behavior.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="df5c6-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="df5c6-112">Version introduced</span></span>

<span data-ttu-id="df5c6-113">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="df5c6-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="df5c6-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="df5c6-114">Recommended action</span></span>

- <span data-ttu-id="df5c6-115"><xref:System.Threading.Tasks.TaskContinuationOptions>以對應的值取代自 <xref:System.Threading.Tasks.TaskCreationOptions> 變數。</span><span class="sxs-lookup"><span data-stu-id="df5c6-115">Replace the <xref:System.Threading.Tasks.TaskContinuationOptions> argument with the corresponding <xref:System.Threading.Tasks.TaskCreationOptions> value.</span></span> <span data-ttu-id="df5c6-116">請勿隱藏此警告，因為它幾乎一律會在您的程式碼中反白顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="df5c6-116">Do not suppress this warning, since it almost always highlights a bug in your code.</span></span> <span data-ttu-id="df5c6-117">如需詳細資訊，請參閱 [CA2247](/visualstudio/code-quality/ca2247)。</span><span class="sxs-lookup"><span data-stu-id="df5c6-117">For more information, see [CA2247](/visualstudio/code-quality/ca2247).</span></span>

- <span data-ttu-id="df5c6-118">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="df5c6-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="df5c6-119">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="df5c6-119">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="df5c6-120">類別</span><span class="sxs-lookup"><span data-stu-id="df5c6-120">Category</span></span>

<span data-ttu-id="df5c6-121">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="df5c6-121">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="df5c6-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="df5c6-122">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

#### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

-->
