---
title: "如何︰ 建立項目清單 |Microsoft 文件"
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
helpviewer_keywords:
- list [LINQ in Visual Basic]
- objects [Visual Basic], list of items
ms.assetid: fe941aba-6340-455c-8b1f-ffd9c3eb1ac5
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ad0d2dfd38e30ddff1a5b030ec1ace884539d134
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-list-of-items"></a><span data-ttu-id="e3929-102">如何：建立項目清單</span><span class="sxs-lookup"><span data-stu-id="e3929-102">How to: Create a List of Items</span></span>
<span data-ttu-id="e3929-103">本主題中的程式碼定義 `Student` 類別並建立此類別的執行個體清單。</span><span class="sxs-lookup"><span data-stu-id="e3929-103">The code in this topic defines a `Student` class and creates a list of instances of the class.</span></span> <span data-ttu-id="e3929-104">清單設計來支援主題[逐步解說︰ 在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e3929-104">The list is designed to support the topic [Walkthrough: Writing Queries in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).</span></span> <span data-ttu-id="e3929-105">也可以用於任何需要物件清單的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e3929-105">It also can be used for any application that requires a list of objects.</span></span> <span data-ttu-id="e3929-106">程式碼會使用物件初始設定式來定義學員清單中的項目。</span><span class="sxs-lookup"><span data-stu-id="e3929-106">The code defines the items in the list of students by using object initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3929-107">範例</span><span class="sxs-lookup"><span data-stu-id="e3929-107">Example</span></span>  
 <span data-ttu-id="e3929-108">如果您正在執行本逐步解說，可將此程式碼使用於在其中建立之專案的 Module1.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="e3929-108">If you are working on the walkthrough, you can use this code for the Module1.vb file of the project that is created there.</span></span> <span data-ttu-id="e3929-109">使用本逐步解說中所提供的查詢和查詢執行，取代 `Main` 中標示 **** 的程式行。</span><span class="sxs-lookup"><span data-stu-id="e3929-109">Just replace the lines marked with **** in the `Main` method with the queries and query executions that are provided in the walkthrough.</span></span>  
  
 <span data-ttu-id="e3929-110">[!code-vb[VbLINQHowToCreateList #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/how-to-create-a-list-of-items_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e3929-110">[!code-vb[VbLINQHowToCreateList#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/how-to-create-a-list-of-items_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3929-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3929-111">See Also</span></span>  
 <span data-ttu-id="e3929-112">[逐步解說︰ 在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md) </span><span class="sxs-lookup"><span data-stu-id="e3929-112">[Walkthrough: Writing Queries in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md) </span></span>  
<span data-ttu-id="e3929-113"> [在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="e3929-113"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="e3929-114"> [物件初始設定式︰ 具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="e3929-114"> [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="e3929-115"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="e3929-115"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="e3929-116"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="e3929-116"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="e3929-117"> [查詢](../../../../visual-basic/language-reference/queries/queries.md)</span><span class="sxs-lookup"><span data-stu-id="e3929-117"> [Queries](../../../../visual-basic/language-reference/queries/queries.md)</span></span>
