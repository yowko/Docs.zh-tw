---
title: "處理 XML 命名空間 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 428bf4b0-e348-4ffd-986b-d905d5a0e7fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd38b2421a58fafa807d39506b728b7d3a4645a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="working-with-xml-namespaces-visual-basic"></a><span data-ttu-id="e23d7-102">處理 XML 命名空間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e23d7-102">Working with XML Namespaces (Visual Basic)</span></span>
<span data-ttu-id="e23d7-103">本節中的主題描述 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 如何支援命名空間。</span><span class="sxs-lookup"><span data-stu-id="e23d7-103">The topics in this section describe how [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] supports namespaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e23d7-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e23d7-104">In This Section</span></span>  
  
|<span data-ttu-id="e23d7-105">主題</span><span class="sxs-lookup"><span data-stu-id="e23d7-105">Topic</span></span>|<span data-ttu-id="e23d7-106">說明</span><span class="sxs-lookup"><span data-stu-id="e23d7-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e23d7-107">命名空間概觀 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e23d7-107">Namespaces Overview (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md)|<span data-ttu-id="e23d7-108">本主題說明命名空間 <xref:System.Xml.Linq.XName> 類別與 <xref:System.Xml.Linq.XNamespace> 類別。</span><span class="sxs-lookup"><span data-stu-id="e23d7-108">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>|  
|[<span data-ttu-id="e23d7-109">如何： 建立包含命名空間 (LINQ to XML) 的文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e23d7-109">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-document-with-namespaces.md)|<span data-ttu-id="e23d7-110">顯示如何利用命名空間建立文件。</span><span class="sxs-lookup"><span data-stu-id="e23d7-110">Shows how to create documents with namespaces.</span></span>|  
|[<span data-ttu-id="e23d7-111">如何： 控制命名空間前置詞 (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e23d7-111">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-control-namespace-prefixes-linq-to-xml.md)|<span data-ttu-id="e23d7-112">顯示如何藉由宣告全域命名空間來控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="e23d7-112">Shows how to control namespace prefixes by declaring global namespaces.</span></span>|  
|[<span data-ttu-id="e23d7-113">在 Visual Basic 中的預設命名空間的範圍</span><span class="sxs-lookup"><span data-stu-id="e23d7-113">Scope of Default Namespaces in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/scope-of-default-namespaces.md)|<span data-ttu-id="e23d7-114">示範在預設的命名空間中，撰寫 XML 之查詢的適當方式。</span><span class="sxs-lookup"><span data-stu-id="e23d7-114">Demonstrates the appropriate way to write queries for XML in the default namespace.</span></span>|  
|[<span data-ttu-id="e23d7-115">處理全域命名空間 (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e23d7-115">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-global-namespaces-linq-to-xml.md)|<span data-ttu-id="e23d7-116">說明 Visual Basic 中，並使用它們的原因中全域命名空間的語意。</span><span class="sxs-lookup"><span data-stu-id="e23d7-116">Explains the semantics of global namespaces in Visual Basic, and reasons for using them.</span></span>|  
|[<span data-ttu-id="e23d7-117">如何： 在命名空間 (Visual Basic) 中的 XML 上撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="e23d7-117">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-queries-on-xml-in-namespaces.md)|<span data-ttu-id="e23d7-118">示範如何在 Visual Basic LINQ XML 查詢指定 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="e23d7-118">Demonstrates how to specify XML namespaces in Visual Basic LINQ to XML queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e23d7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e23d7-119">See Also</span></span>  
 [<span data-ttu-id="e23d7-120">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e23d7-120">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
