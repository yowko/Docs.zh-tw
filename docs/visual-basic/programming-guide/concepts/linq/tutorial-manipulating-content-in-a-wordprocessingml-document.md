---
title: "教學課程︰ 操作 WordprocessingML 文件 (Visual Basic) 中的內容 |Microsoft 文件"
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
ms.assetid: f8028ba8-2dd1-4425-930c-8cc23176ebbc
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 28ab2d19cba0344868061fbe1f59c546a569fbdc
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-visual-basic"></a><span data-ttu-id="33d36-102">教學課程︰ 操作 WordprocessingML 文件 (Visual Basic) 中的內容</span><span class="sxs-lookup"><span data-stu-id="33d36-102">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>
<span data-ttu-id="33d36-103">本教學課程顯示如何應用功能性轉換方法與 LINQ to XML 來管理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="33d36-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="33d36-104">Visual Basic 範例查詢，並管理 Microsoft Word 所儲存之 Office Open XML WordprocessingML 文件中的資訊。</span><span class="sxs-lookup"><span data-stu-id="33d36-104">The Visual Basic examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="33d36-105">如需詳細資訊，請參閱[OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573)網站。</span><span class="sxs-lookup"><span data-stu-id="33d36-105">For more information, see the [OpenXML Developer](http://go.microsoft.com/fwlink/?LinkID=95573) Web site.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33d36-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="33d36-106">In This Section</span></span>  
  
|<span data-ttu-id="33d36-107">主題</span><span class="sxs-lookup"><span data-stu-id="33d36-107">Topic</span></span>|<span data-ttu-id="33d36-108">描述</span><span class="sxs-lookup"><span data-stu-id="33d36-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="33d36-109">WordprocessingML 文件的 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d36-109">Shape of WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)|<span data-ttu-id="33d36-110">提供 WordprocessingML 文件詳細資料的快速說明。</span><span class="sxs-lookup"><span data-stu-id="33d36-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="33d36-111">建立來源 Office Open XML 文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d36-111">Creating the Source Office Open XML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)|<span data-ttu-id="33d36-112">提供逐步指示來建立此教學課程中，查詢的來源文件。</span><span class="sxs-lookup"><span data-stu-id="33d36-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="33d36-113">尋找預設段落樣式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d36-113">Finding the Default Paragraph Style (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)|<span data-ttu-id="33d36-114">顯示查詢來尋找文件之預設樣式的名稱。</span><span class="sxs-lookup"><span data-stu-id="33d36-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="33d36-115">擷取段落及其樣式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d36-115">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="33d36-116">顯示擷取文件之段落集合的查詢。</span><span class="sxs-lookup"><span data-stu-id="33d36-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="33d36-117">擷取文字的段落 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d36-117">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="33d36-118">擴大上一個查詢來擷取每個段落的文字。</span><span class="sxs-lookup"><span data-stu-id="33d36-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="33d36-119">重構的擴充方法 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d36-119">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)|<span data-ttu-id="33d36-120">使用擴充方法重構來簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="33d36-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="33d36-121">重構使用純虛擬函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d36-121">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)|<span data-ttu-id="33d36-122">使用虛擬函式重構進一步簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="33d36-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="33d36-123">組織結構規劃 XML 不同形式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d36-123">Projecting XML in a Different Shape (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projecting-xml-in-a-different-shape.md)|<span data-ttu-id="33d36-124">利用與原始文件不同的組織結構投影 XML 來完成 XML 轉換。</span><span class="sxs-lookup"><span data-stu-id="33d36-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="33d36-125">Word 文件 (Visual Basic) 中尋找文字</span><span class="sxs-lookup"><span data-stu-id="33d36-125">Finding Text in Word Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/finding-text-in-word-documents.md)|<span data-ttu-id="33d36-126">使用上一個查詢來尋找文件中指定的文字字串。</span><span class="sxs-lookup"><span data-stu-id="33d36-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="33d36-127">詳細資料的 Office Open XML WordprocessingML 文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33d36-127">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="33d36-128">提供 Office Open XML WordprocessingML 文件的一些詳細資料。</span><span class="sxs-lookup"><span data-stu-id="33d36-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33d36-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33d36-129">See Also</span></span>  
 <span data-ttu-id="33d36-130">[純功能性轉換 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span><span class="sxs-lookup"><span data-stu-id="33d36-130">[Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md) </span></span>  
<span data-ttu-id="33d36-131"> [純功能性轉換 (Visual Basic) 簡介](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="33d36-131"> [Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)</span></span>
