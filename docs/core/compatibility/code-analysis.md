---
title: 程式碼分析的重大變更
description: 列出 .NET 來源程式碼分析器中的重大變更。
ms.date: 08/22/2020
ms.openlocfilehash: 8b2b50c5f03a3ca971aefd0f2cf53624dfa82274
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465561"
---
# <a name="code-analysis-breaking-changes"></a><span data-ttu-id="4d486-103">程式碼分析的重大變更</span><span class="sxs-lookup"><span data-stu-id="4d486-103">Code analysis breaking changes</span></span>

<span data-ttu-id="4d486-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="4d486-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="4d486-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="4d486-105">Breaking change</span></span> | <span data-ttu-id="4d486-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="4d486-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="4d486-107">CA1831：使用 AsSpan 或 AsMemory，而非以範圍為基礎的索引子</span><span class="sxs-lookup"><span data-stu-id="4d486-107">CA1831: Use AsSpan or AsMemory instead of Range-based indexer</span></span>](#ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer) | <span data-ttu-id="4d486-108">5.0</span><span class="sxs-lookup"><span data-stu-id="4d486-108">5.0</span></span> |
| [<span data-ttu-id="4d486-109">CA2014：請勿在迴圈中使用 stackalloc</span><span class="sxs-lookup"><span data-stu-id="4d486-109">CA2014: Do not use stackalloc in loops</span></span>](#ca2014-do-not-use-stackalloc-in-loops) | <span data-ttu-id="4d486-110">5.0</span><span class="sxs-lookup"><span data-stu-id="4d486-110">5.0</span></span> |
| [<span data-ttu-id="4d486-111">CA2015：請勿定義衍生自 MemoryManager 之類型的完成項\<T></span><span class="sxs-lookup"><span data-stu-id="4d486-111">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>](#ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert) | <span data-ttu-id="4d486-112">5.0</span><span class="sxs-lookup"><span data-stu-id="4d486-112">5.0</span></span> |
| [<span data-ttu-id="4d486-113">CA2247： >taskcompletionsource 的引數應為 TaskCreationOptions 值</span><span class="sxs-lookup"><span data-stu-id="4d486-113">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>](#ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value) | <span data-ttu-id="4d486-114">5.0</span><span class="sxs-lookup"><span data-stu-id="4d486-114">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="4d486-115">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="4d486-115">.NET 5.0</span></span>

[!INCLUDE [range-based-indexer-on-string](../../../includes/core-changes/codeanalysis/5.0/range-based-indexer-on-string.md)]

***

[!INCLUDE [stackalloc-in-loops](../../../includes/core-changes/codeanalysis/5.0/stackalloc-in-loops.md)]

***

[!INCLUDE [finalizers-for-memorymanager-types](../../../includes/core-changes/codeanalysis/5.0/finalizers-for-memorymanager-types.md)]

***

[!INCLUDE [ctor-arg-should-be-taskcreationoptions](../../../includes/core-changes/codeanalysis/5.0/ctor-arg-should-be-taskcreationoptions.md)]

***
