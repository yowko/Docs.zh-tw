---
ms.openlocfilehash: 4fc31f75e8f8cdd50abebd399d9749688e6faa5a
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465564"
---
### <a name="ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="bc3f6-101">CA2015：請勿針對衍生自 MemoryManager\<T> 的類型定義完成項</span><span class="sxs-lookup"><span data-stu-id="bc3f6-101">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="bc3f6-102">預設會啟用 .NET 程式碼分析器規則 [CA2015](/visualstudio/code-quality/ca2015) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-102">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="bc3f6-103">它會針對衍生自訂完成項的任何類型產生組建警告 <xref:System.Buffers.MemoryManager%601> 。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-103">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bc3f6-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="bc3f6-104">Change description</span></span>

<span data-ttu-id="bc3f6-105">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../docs/fundamentals/productivity/code-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="bc3f6-106">預設會啟用這些規則中的數個，包括 [CA2015](/visualstudio/code-quality/ca2015)。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-106">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="bc3f6-107">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="bc3f6-108">從定義完成項的衍生自的規則 CA2015 旗標類型 <xref:System.Buffers.MemoryManager%601> 。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-108">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="bc3f6-109">將完成項加入至衍生自的型別， <xref:System.Buffers.MemoryManager%601> 可能表示有錯誤。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-109">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="bc3f6-110">這表示可能已在中取得的原生資源 <xref:System.Span%601> 正在進行清除，可能是因為仍在使用中 <xref:System.Span%601> 。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-110">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bc3f6-111">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bc3f6-111">Version introduced</span></span>

<span data-ttu-id="bc3f6-112">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="bc3f6-112">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bc3f6-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bc3f6-113">Recommended action</span></span>

- <span data-ttu-id="bc3f6-114">移除完成項定義。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-114">Remove the finalizer definition.</span></span> <span data-ttu-id="bc3f6-115">如需詳細資訊，請參閱 [CA2015](/visualstudio/code-quality/ca2015)。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-115">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="bc3f6-116">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-116">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="bc3f6-117">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-117">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="bc3f6-118">類別</span><span class="sxs-lookup"><span data-stu-id="bc3f6-118">Category</span></span>

<span data-ttu-id="bc3f6-119">程式碼分析</span><span class="sxs-lookup"><span data-stu-id="bc3f6-119">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bc3f6-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bc3f6-120">Affected APIs</span></span>

<span data-ttu-id="bc3f6-121">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="bc3f6-121">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
