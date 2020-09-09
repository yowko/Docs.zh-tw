---
title: 程式碼分析的重大變更
description: 列出 .NET 來源程式碼分析器中的重大變更。
ms.date: 09/02/2020
ms.openlocfilehash: f1e89c90e6d91b9b3555542a0c7adf2607a76a01
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598061"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="e3a49-103">程式碼分析的重大變更</span><span class="sxs-lookup"><span data-stu-id="e3a49-103">Code analysis breaking changes</span></span>

<span data-ttu-id="e3a49-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="e3a49-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="e3a49-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="e3a49-105">Breaking change</span></span> | <span data-ttu-id="e3a49-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e3a49-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="e3a49-107">CA1417： P/Invoke 的字串參數上的 OutAttribute</span><span class="sxs-lookup"><span data-stu-id="e3a49-107">CA1417: OutAttribute on string parameter for P/Invoke</span></span>](#ca1417-outattribute-on-string-parameter-for-pinvoke) | <span data-ttu-id="e3a49-108">5.0</span><span class="sxs-lookup"><span data-stu-id="e3a49-108">5.0</span></span> |
| [<span data-ttu-id="e3a49-109">CA1831：針對字串使用 AsSpan 而非以範圍為基礎的索引子</span><span class="sxs-lookup"><span data-stu-id="e3a49-109">CA1831: Use AsSpan instead of Range-based indexers for string</span></span>](#ca1831-use-asspan-instead-of-range-based-indexers-for-string) | <span data-ttu-id="e3a49-110">5.0</span><span class="sxs-lookup"><span data-stu-id="e3a49-110">5.0</span></span> |
| [<span data-ttu-id="e3a49-111">CA2013：請勿使用具有值類型的 ReferenceEquals</span><span class="sxs-lookup"><span data-stu-id="e3a49-111">CA2013: Do not use ReferenceEquals with value types</span></span>](#ca2013-do-not-use-referenceequals-with-value-types) | <span data-ttu-id="e3a49-112">5.0</span><span class="sxs-lookup"><span data-stu-id="e3a49-112">5.0</span></span> |
| [<span data-ttu-id="e3a49-113">CA2014：請勿在迴圈中使用 stackalloc</span><span class="sxs-lookup"><span data-stu-id="e3a49-113">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="e3a49-114">5.0</span><span class="sxs-lookup"><span data-stu-id="e3a49-114">5.0</span></span> |
| [<span data-ttu-id="e3a49-115">CA2015：請勿定義衍生自 MemoryManager 之類型的完成項\<T></span><span class="sxs-lookup"><span data-stu-id="e3a49-115">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="e3a49-116">5.0</span><span class="sxs-lookup"><span data-stu-id="e3a49-116">5.0</span></span> |
| [<span data-ttu-id="e3a49-117">CA2247： >taskcompletionsource 的引數應為 TaskCreationOptions 值</span><span class="sxs-lookup"><span data-stu-id="e3a49-117">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="e3a49-118">5.0</span><span class="sxs-lookup"><span data-stu-id="e3a49-118">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="e3a49-119">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="e3a49-119">.NET 5.0</span></span>

[!INCLUDE [outattributes-on-pinvoke-string-parameters](../../../includes/core-changes/codeanalysis/5.0/outattributes-on-pinvoke-string-parameters.md)]

***

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [referenceequals-on-value-types](../../../includes/core-changes/codeanalysis/5.0/referenceequals-on-value-types.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
