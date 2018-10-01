---
title: 教學課程：將查詢鏈結在一起 (C#)
ms.date: 07/20/2015
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
ms.openlocfilehash: cab012a6ae618bd731c26bc1a002c144b84d2169
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47204514"
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="8ff28-102">教學課程：將查詢鏈結在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="8ff28-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="8ff28-103">此教學課程說明將查詢鏈結在一起時的處理模型。</span><span class="sxs-lookup"><span data-stu-id="8ff28-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="8ff28-104">將查詢鏈結在一起是撰寫功能性轉換的重要部分。</span><span class="sxs-lookup"><span data-stu-id="8ff28-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="8ff28-105">確實了解鏈結的查詢如何運作相當重要。</span><span class="sxs-lookup"><span data-stu-id="8ff28-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="8ff28-106">處理 Office Open XML 文件的查詢會廣泛使用這個技術。</span><span class="sxs-lookup"><span data-stu-id="8ff28-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ff28-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="8ff28-107">In This Section</span></span>  
  
|<span data-ttu-id="8ff28-108">主題</span><span class="sxs-lookup"><span data-stu-id="8ff28-108">Topic</span></span>|<span data-ttu-id="8ff28-109">描述</span><span class="sxs-lookup"><span data-stu-id="8ff28-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8ff28-110">LINQ to XML 中的延後執行和延遲評估 (C#)</span><span class="sxs-lookup"><span data-stu-id="8ff28-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="8ff28-111">描述延後執行和延遲評估的概念。</span><span class="sxs-lookup"><span data-stu-id="8ff28-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="8ff28-112">延後執行範例 (C#)</span><span class="sxs-lookup"><span data-stu-id="8ff28-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="8ff28-113">提供延後執行的範例。</span><span class="sxs-lookup"><span data-stu-id="8ff28-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="8ff28-114">鏈結查詢範例 (C#)</span><span class="sxs-lookup"><span data-stu-id="8ff28-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="8ff28-115">顯示將查詢鏈結在一起時，延後執行如何運作。</span><span class="sxs-lookup"><span data-stu-id="8ff28-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="8ff28-116">中繼具體化 (C#)</span><span class="sxs-lookup"><span data-stu-id="8ff28-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="8ff28-117">識別並說明中繼具體化的語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="8ff28-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="8ff28-118">將標準查詢運算子鏈結在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="8ff28-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="8ff28-119">描述標準查詢運算子的延遲語意。</span><span class="sxs-lookup"><span data-stu-id="8ff28-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ff28-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="8ff28-120">See Also</span></span>

- [<span data-ttu-id="8ff28-121">XML 純功能性轉換 (C#)</span><span class="sxs-lookup"><span data-stu-id="8ff28-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
