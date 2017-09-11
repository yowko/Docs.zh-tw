---
title: "教學課程︰ 延後執行 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c80d53a8-1a30-4115-b232-52f0d089fec5
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9a5d83091e1edcd0d8902878a22ee39577f89592
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="tutorial-deferred-execution-visual-basic"></a><span data-ttu-id="8cbcd-102">教學課程︰ 延後執行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cbcd-102">Tutorial: Deferred Execution (Visual Basic)</span></span>
<span data-ttu-id="8cbcd-103">此教學課程說明將查詢鏈結在一起時的處理模型。</span><span class="sxs-lookup"><span data-stu-id="8cbcd-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="8cbcd-104">將查詢鏈結在一起是撰寫功能性轉換的重要部分。</span><span class="sxs-lookup"><span data-stu-id="8cbcd-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="8cbcd-105">確實了解鏈結的查詢如何運作相當重要。</span><span class="sxs-lookup"><span data-stu-id="8cbcd-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="8cbcd-106">處理 Office Open XML 文件的查詢會廣泛使用這個技術。</span><span class="sxs-lookup"><span data-stu-id="8cbcd-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8cbcd-107">本章節內容</span><span class="sxs-lookup"><span data-stu-id="8cbcd-107">In This Section</span></span>  
  
|<span data-ttu-id="8cbcd-108">主題</span><span class="sxs-lookup"><span data-stu-id="8cbcd-108">Topic</span></span>|<span data-ttu-id="8cbcd-109">描述</span><span class="sxs-lookup"><span data-stu-id="8cbcd-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8cbcd-110">延後的執行與延遲評估在 LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cbcd-110">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="8cbcd-111">描述延後執行和延遲評估的概念。</span><span class="sxs-lookup"><span data-stu-id="8cbcd-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="8cbcd-112">延後的執行範例 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cbcd-112">Deferred Execution Example (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="8cbcd-113">提供延後執行的範例。</span><span class="sxs-lookup"><span data-stu-id="8cbcd-113">Provides an example of deferred execution.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cbcd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cbcd-114">See Also</span></span>  
 [<span data-ttu-id="8cbcd-115">純功能性轉換 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8cbcd-115">Pure Functional Transformations of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
