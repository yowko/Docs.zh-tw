---
title: "處理 XML 命名空間 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 428bf4b0-e348-4ffd-986b-d905d5a0e7fa
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4ddbc7a241fa8dee886fb0aeb5951f1ee622efb5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="working-with-xml-namespaces-visual-basic"></a><span data-ttu-id="aff9f-102">處理 XML 命名空間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aff9f-102">Working with XML Namespaces (Visual Basic)</span></span>
<span data-ttu-id="aff9f-103">本章節的主題描述如何[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]支援命名空間。</span><span class="sxs-lookup"><span data-stu-id="aff9f-103">The topics in this section describe how [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] supports namespaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aff9f-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="aff9f-104">In This Section</span></span>  
  
|<span data-ttu-id="aff9f-105">主題</span><span class="sxs-lookup"><span data-stu-id="aff9f-105">Topic</span></span>|<span data-ttu-id="aff9f-106">描述</span><span class="sxs-lookup"><span data-stu-id="aff9f-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="aff9f-107">命名空間概觀 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="aff9f-107">Namespaces Overview (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md)|<span data-ttu-id="aff9f-108">本主題說明命名空間的<xref:System.Xml.Linq.XName>類別和<xref:System.Xml.Linq.XNamespace>類別。</xref:System.Xml.Linq.XNamespace> </xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="aff9f-108">This topic introduces namespaces, the <xref:System.Xml.Linq.XName> class, and the <xref:System.Xml.Linq.XNamespace> class.</span></span>|  
|[<span data-ttu-id="aff9f-109">如何︰ 建立包含命名空間 (LINQ to XML) 文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aff9f-109">How to: Create a Document with Namespaces (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-document-with-namespaces.md)|<span data-ttu-id="aff9f-110">顯示如何利用命名空間建立文件。</span><span class="sxs-lookup"><span data-stu-id="aff9f-110">Shows how to create documents with namespaces.</span></span>|  
|[<span data-ttu-id="aff9f-111">如何︰ 控制命名空間前置詞 (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="aff9f-111">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-control-namespace-prefixes-linq-to-xml.md)|<span data-ttu-id="aff9f-112">顯示如何藉由宣告全域命名空間來控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="aff9f-112">Shows how to control namespace prefixes by declaring global namespaces.</span></span>|  
|[<span data-ttu-id="aff9f-113">在 Visual Basic 中的預設命名空間的範圍</span><span class="sxs-lookup"><span data-stu-id="aff9f-113">Scope of Default Namespaces in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/scope-of-default-namespaces.md)|<span data-ttu-id="aff9f-114">示範在預設的命名空間中，撰寫 XML 之查詢的適當方式。</span><span class="sxs-lookup"><span data-stu-id="aff9f-114">Demonstrates the appropriate way to write queries for XML in the default namespace.</span></span>|  
|[<span data-ttu-id="aff9f-115">使用全域命名空間 (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="aff9f-115">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-global-namespaces-linq-to-xml.md)|<span data-ttu-id="aff9f-116">說明在 Visual Basic 中，並使用它們的原因的全域命名空間的語意。</span><span class="sxs-lookup"><span data-stu-id="aff9f-116">Explains the semantics of global namespaces in Visual Basic, and reasons for using them.</span></span>|  
|[<span data-ttu-id="aff9f-117">如何︰ 在命名空間 (Visual Basic) 中的 XML 上撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="aff9f-117">How to: Write Queries on XML in Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-write-queries-on-xml-in-namespaces.md)|<span data-ttu-id="aff9f-118">示範如何在 Visual Basic LINQ 中指定 XML 命名空間，XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="aff9f-118">Demonstrates how to specify XML namespaces in Visual Basic LINQ to XML queries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aff9f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aff9f-119">See Also</span></span>  
 [<span data-ttu-id="aff9f-120">程式設計手冊 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aff9f-120">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
