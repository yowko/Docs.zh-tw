---
title: 程式碼分析的重大變更
description: 列出 .NET 來源程式碼分析器中的重大變更。
ms.date: 09/02/2020
ms.openlocfilehash: 3cbe2ecf5d08084db542db0c2da016f1f391452e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538915"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="e3c08-103">程式碼分析的重大變更</span><span class="sxs-lookup"><span data-stu-id="e3c08-103">Code analysis breaking changes</span></span>

<span data-ttu-id="e3c08-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="e3c08-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="e3c08-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="e3c08-105">Breaking change</span></span> | <span data-ttu-id="e3c08-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e3c08-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="e3c08-107">CA1416：平臺相容性</span><span class="sxs-lookup"><span data-stu-id="e3c08-107">CA1416: Platform compatibility</span></span>](#ca1416-platform-compatibility) | <span data-ttu-id="e3c08-108">5.0</span><span class="sxs-lookup"><span data-stu-id="e3c08-108">5.0</span></span> |
| [<span data-ttu-id="e3c08-109">CA1417： P/Invoke 的字串參數上的 OutAttribute</span><span class="sxs-lookup"><span data-stu-id="e3c08-109">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="e3c08-110">5.0</span><span class="sxs-lookup"><span data-stu-id="e3c08-110">5.0</span></span> |
| [<span data-ttu-id="e3c08-111">CA1831：針對字串使用 AsSpan 而非以範圍為基礎的索引子</span><span class="sxs-lookup"><span data-stu-id="e3c08-111">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="e3c08-112">5.0</span><span class="sxs-lookup"><span data-stu-id="e3c08-112">5.0</span></span> |
| [<span data-ttu-id="e3c08-113">CA2013：請勿使用具有值類型的 ReferenceEquals</span><span class="sxs-lookup"><span data-stu-id="e3c08-113">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="e3c08-114">5.0</span><span class="sxs-lookup"><span data-stu-id="e3c08-114">5.0</span></span> |
| [<span data-ttu-id="e3c08-115">CA2014：請勿在迴圈中使用 stackalloc</span><span class="sxs-lookup"><span data-stu-id="e3c08-115">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="e3c08-116">5.0</span><span class="sxs-lookup"><span data-stu-id="e3c08-116">5.0</span></span> |
| [<span data-ttu-id="e3c08-117">CA2015：請勿定義衍生自 MemoryManager 之類型的完成項\<T></span><span class="sxs-lookup"><span data-stu-id="e3c08-117">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="e3c08-118">5.0</span><span class="sxs-lookup"><span data-stu-id="e3c08-118">5.0</span></span> |
| [<span data-ttu-id="e3c08-119">CA2200:必須重新擲回以保存堆疊詳細資料</span><span class="sxs-lookup"><span data-stu-id="e3c08-119">CA2200: Rethrow to preserve stack details</span></span>](#ca2200-rethrow-to-preserve-stack-details) | <span data-ttu-id="e3c08-120">5.0</span><span class="sxs-lookup"><span data-stu-id="e3c08-120">5.0</span></span> |
| [<span data-ttu-id="e3c08-121">CA2247： >taskcompletionsource 的引數應為 TaskCreationOptions 值</span><span class="sxs-lookup"><span data-stu-id="e3c08-121">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="e3c08-122">5.0</span><span class="sxs-lookup"><span data-stu-id="e3c08-122">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="e3c08-123">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="e3c08-123">.NET 5.0</span></span>

[!INCLUDE [ca1416-platform-compatibility-analyzer](../../../includes/core-changes/codeanalysis/5.0/ca1416-platform-compatibility-analyzer.md)]

***

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/ca1417-outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/ca1831-range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/ca2013-referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/ca2014-stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/ca2015-finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ca2200-rethrow-to-preserve-stack-details](../../../includes/core-changes/codeanalysis/5.0/ca2200-rethrow-to-preserve-stack-details.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ca2247-ctor-arg-should-be-taskcreationoptions.md)]

***
