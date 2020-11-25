---
title: 重大變更： CA2015：請勿定義衍生自 MemoryManager 之類型的完成項<T>
description: 瞭解 .NET 5.0 中因為啟用程式碼分析規則 CA2015 所造成的重大變更。
ms.date: 09/03/2020
ms.openlocfilehash: 5d0ba0546b5a72363559f23713c8af4bb4e26e48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760426"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="4a4eb-103">警告 CA2015：請勿定義衍生自 MemoryManager 之類型的完成項\<T></span><span class="sxs-lookup"><span data-stu-id="4a4eb-103">Warning CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="4a4eb-104">預設會啟用 .NET 程式碼分析器規則 [CA2015](/visualstudio/code-quality/ca2015) ，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-104">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="4a4eb-105">它會針對衍生自訂完成項的任何類型產生組建警告 <xref:System.Buffers.MemoryManager%601> 。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-105">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

## <a name="change-description"></a><span data-ttu-id="4a4eb-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="4a4eb-106">Change description</span></span>

<span data-ttu-id="4a4eb-107">從 .NET 5.0 開始，.NET SDK 包含 [.net source 程式碼分析器](../../../../fundamentals/code-analysis/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="4a4eb-108">預設會啟用這些規則中的數個，包括 [CA2015](/visualstudio/code-quality/ca2015)。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-108">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="4a4eb-109">如果您的專案包含違反此規則的程式碼，而且設定為將警告視為錯誤，這項變更可能會中斷您的組建。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="4a4eb-110">從定義完成項的衍生自的規則 CA2015 旗標類型 <xref:System.Buffers.MemoryManager%601> 。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-110">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="4a4eb-111">將完成項加入至衍生自的型別， <xref:System.Buffers.MemoryManager%601> 可能表示有錯誤。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-111">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="4a4eb-112">這表示可能已在中取得的原生資源 <xref:System.Span%601> 正在進行清除，可能是因為仍在使用中 <xref:System.Span%601> 。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-112">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="4a4eb-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4a4eb-113">Version introduced</span></span>

<span data-ttu-id="4a4eb-114">5.0</span><span class="sxs-lookup"><span data-stu-id="4a4eb-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="4a4eb-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="4a4eb-115">Recommended action</span></span>

- <span data-ttu-id="4a4eb-116">移除完成項定義。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-116">Remove the finalizer definition.</span></span> <span data-ttu-id="4a4eb-117">如需詳細資訊，請參閱 [CA2015](/visualstudio/code-quality/ca2015)。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-117">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="4a4eb-118">若要完全停用程式碼分析，請 `EnableNETAnalyzers` `false` 在您的專案檔中將設定為。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="4a4eb-119">如需詳細資訊，請參閱 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="4a4eb-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="4a4eb-120">Affected APIs</span></span>

<span data-ttu-id="4a4eb-121">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="4a4eb-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
