---
title: "純功能性轉換 XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e19b74a-7773-4b58-b110-953ffd364c55
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01ad228d91037de1585d1e66292fddb80c785ada
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="pure-functional-transformations-of-xml-visual-basic"></a><span data-ttu-id="61bb7-102">純功能性轉換 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61bb7-102">Pure Functional Transformations of XML (Visual Basic)</span></span>
<span data-ttu-id="61bb7-103">本節提供 XML 的功能性轉換教學課程。</span><span class="sxs-lookup"><span data-stu-id="61bb7-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="61bb7-104">這包含您必須了解之主要概念和語言建構以使用功能性轉換的說明，以及使用功能性轉換以管理 XML 文件的範例。</span><span class="sxs-lookup"><span data-stu-id="61bb7-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="61bb7-105">雖然這個教學課程提供 LINQ to XML 程式碼範例，但是所有基礎概念也適用於其他 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="61bb7-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="61bb7-106">[教學課程： WordprocessingML 文件 (Visual Basic) 中的 內容操作](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)教學課程提供的一系列範例，每個在前一個上建置。</span><span class="sxs-lookup"><span data-stu-id="61bb7-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="61bb7-107">這些範例會示範純功能性轉換方法以管理 XML。</span><span class="sxs-lookup"><span data-stu-id="61bb7-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="61bb7-108">本教學課程假設您已經具備 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="61bb7-108">This tutorial assumes a working knowledge of Visual Basic.</span></span> <span data-ttu-id="61bb7-109">在此教學課程中不會提供語言建構的詳細語意，但是會適當地提供語言文件的連結。</span><span class="sxs-lookup"><span data-stu-id="61bb7-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="61bb7-110">同時也假設具備資訊科學基本概念與 XML (包括 XML 命名空間) 的實用知識。</span><span class="sxs-lookup"><span data-stu-id="61bb7-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61bb7-111">本章節內容</span><span class="sxs-lookup"><span data-stu-id="61bb7-111">In This Section</span></span>  
  
|<span data-ttu-id="61bb7-112">主題</span><span class="sxs-lookup"><span data-stu-id="61bb7-112">Topic</span></span>|<span data-ttu-id="61bb7-113">說明</span><span class="sxs-lookup"><span data-stu-id="61bb7-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="61bb7-114">Introduction to 純功能性轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61bb7-114">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="61bb7-115">描述功能性轉換並定義相關的術語。</span><span class="sxs-lookup"><span data-stu-id="61bb7-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="61bb7-116">教學課程： 延後執行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61bb7-116">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)|<span data-ttu-id="61bb7-117">詳細描述延遲評估以及延後執行。</span><span class="sxs-lookup"><span data-stu-id="61bb7-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="61bb7-118">教學課程： 操作 WordprocessingML 文件 (Visual Basic) 中的內容</span><span class="sxs-lookup"><span data-stu-id="61bb7-118">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="61bb7-119">示範功能性轉換的教學課程。</span><span class="sxs-lookup"><span data-stu-id="61bb7-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61bb7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61bb7-120">See Also</span></span>  
 [<span data-ttu-id="61bb7-121">查詢 XML 樹狀結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="61bb7-121">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
