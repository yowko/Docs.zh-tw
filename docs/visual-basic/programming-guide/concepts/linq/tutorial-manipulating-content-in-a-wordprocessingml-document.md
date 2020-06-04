---
title: 教學課程：管理 WordprocessingML 文件中的內容
ms.date: 07/20/2015
ms.assetid: f8028ba8-2dd1-4425-930c-8cc23176ebbc
ms.openlocfilehash: 9fd5fd5092a74ad8124a691d7d3bb479fa5dcdde
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396268"
---
# <a name="tutorial-manipulating-content-in-a-wordprocessingml-document-visual-basic"></a><span data-ttu-id="d29dd-102">教學課程：操作 WordprocessingML 檔中的內容（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-102">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>
<span data-ttu-id="d29dd-103">本教學課程顯示如何應用功能性轉換方法與 LINQ to XML 來管理 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="d29dd-103">This tutorial shows how to apply the functional transformational approach and LINQ to XML to manipulate XML documents.</span></span> <span data-ttu-id="d29dd-104">Visual Basic 範例會查詢並管理 Microsoft Word 所儲存之 Office Open XML WordprocessingML 檔中的資訊。</span><span class="sxs-lookup"><span data-stu-id="d29dd-104">The Visual Basic examples query and manipulate information in Office Open XML WordprocessingML documents that are saved by Microsoft Word.</span></span>  
  
 <span data-ttu-id="d29dd-105">如需詳細資訊，請參閱[Eric 白的 Blog](http://www.ericwhite.com)。</span><span class="sxs-lookup"><span data-stu-id="d29dd-105">For more information, see the [Eric White's Blog](http://www.ericwhite.com).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d29dd-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="d29dd-106">In This Section</span></span>  
  
|<span data-ttu-id="d29dd-107">主題</span><span class="sxs-lookup"><span data-stu-id="d29dd-107">Topic</span></span>|<span data-ttu-id="d29dd-108">說明</span><span class="sxs-lookup"><span data-stu-id="d29dd-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d29dd-109">WordprocessingML 檔的形狀（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-109">Shape of WordprocessingML Documents (Visual Basic)</span></span>](shape-of-wordprocessingml-documents.md)|<span data-ttu-id="d29dd-110">提供 WordprocessingML 文件詳細資料的快速說明。</span><span class="sxs-lookup"><span data-stu-id="d29dd-110">Provides a quick explanation of details of a WordprocessingML document.</span></span>|  
|[<span data-ttu-id="d29dd-111">建立來源 Office Open XML 檔（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-111">Creating the Source Office Open XML Document (Visual Basic)</span></span>](creating-the-source-office-open-xml-document.md)|<span data-ttu-id="d29dd-112">提供逐步指示來建立此教學課程中，查詢的來源文件。</span><span class="sxs-lookup"><span data-stu-id="d29dd-112">Provides step-by-step instructions to create the source document for queries in this tutorial.</span></span>|  
|[<span data-ttu-id="d29dd-113">尋找預設段落樣式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-113">Finding the Default Paragraph Style (Visual Basic)</span></span>](finding-the-default-paragraph-style.md)|<span data-ttu-id="d29dd-114">顯示查詢來尋找文件之預設樣式的名稱。</span><span class="sxs-lookup"><span data-stu-id="d29dd-114">Shows a query to find the name of the default style for a document.</span></span>|  
|[<span data-ttu-id="d29dd-115">抓取段落和其樣式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-115">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](retrieving-the-paragraphs-and-their-styles.md)|<span data-ttu-id="d29dd-116">顯示擷取文件之段落集合的查詢。</span><span class="sxs-lookup"><span data-stu-id="d29dd-116">Shows a query that retrieves a collection of the paragraphs of a document.</span></span>|  
|[<span data-ttu-id="d29dd-117">正在抓取段落的文字（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-117">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>](retrieving-the-text-of-the-paragraphs.md)|<span data-ttu-id="d29dd-118">擴大上一個查詢來擷取每個段落的文字。</span><span class="sxs-lookup"><span data-stu-id="d29dd-118">Augments the previous query to retrieve the text of each paragraph.</span></span>|  
|[<span data-ttu-id="d29dd-119">使用擴充方法（Visual Basic）進行重構</span><span class="sxs-lookup"><span data-stu-id="d29dd-119">Refactoring Using an Extension Method (Visual Basic)</span></span>](refactoring-using-an-extension-method.md)|<span data-ttu-id="d29dd-120">使用擴充方法重構來簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="d29dd-120">Simplifies the code by refactoring using an extension method.</span></span>|  
|[<span data-ttu-id="d29dd-121">使用純虛擬函式進行重構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d29dd-121">Refactoring Using a Pure Function (Visual Basic)</span></span>](refactoring-using-a-pure-function.md)|<span data-ttu-id="d29dd-122">使用虛擬函式重構進一步簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="d29dd-122">Further simplifies the code by refactoring using a pure function.</span></span>|  
|[<span data-ttu-id="d29dd-123">以不同的形狀投射 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-123">Projecting XML in a Different Shape (Visual Basic)</span></span>](projecting-xml-in-a-different-shape.md)|<span data-ttu-id="d29dd-124">利用與原始文件不同的組織結構投影 XML 來完成 XML 轉換。</span><span class="sxs-lookup"><span data-stu-id="d29dd-124">Completes an XML transformation by projecting XML in a different shape than the original document.</span></span>|  
|[<span data-ttu-id="d29dd-125">尋找 Word 檔中的文字（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-125">Finding Text in Word Documents (Visual Basic)</span></span>](finding-text-in-word-documents.md)|<span data-ttu-id="d29dd-126">使用上一個查詢來尋找文件中指定的文字字串。</span><span class="sxs-lookup"><span data-stu-id="d29dd-126">Uses the previous queries to find a specified text string in a document.</span></span>|  
|[<span data-ttu-id="d29dd-127">Office Open XML WordprocessingML 檔的詳細資料（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-127">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)|<span data-ttu-id="d29dd-128">提供 Office Open XML WordprocessingML 文件的一些詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d29dd-128">Provides some details of Office Open XML WordprocessingML documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d29dd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d29dd-129">See also</span></span>

- [<span data-ttu-id="d29dd-130">XML 的純功能性轉換（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-130">Pure Functional Transformations of XML (Visual Basic)</span></span>](pure-functional-transformations-of-xml.md)
- [<span data-ttu-id="d29dd-131">純功能性轉換簡介（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d29dd-131">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)
