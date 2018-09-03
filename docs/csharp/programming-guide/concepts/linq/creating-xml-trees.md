---
title: 建立 XML 樹狀結構 (C#)
ms.date: 07/20/2015
ms.assetid: bccc3e0a-c08c-468e-9d30-e075670fdace
ms.openlocfilehash: a9e9cfd82434de0fabc8119aa500ad9d9ef8155a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481371"
---
# <a name="creating-xml-trees-c"></a><span data-ttu-id="e1b1f-102">建立 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="e1b1f-102">Creating XML Trees (C#)</span></span>
<span data-ttu-id="e1b1f-103">其中一個最常見的 XML 工做為建構 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-103">One of the most common XML tasks is constructing an XML tree.</span></span> <span data-ttu-id="e1b1f-104">本節描述數種建立這些樹狀結構的方式。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-104">This section describes several ways to create them.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1b1f-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="e1b1f-105">In This Section</span></span>  
  
|<span data-ttu-id="e1b1f-106">主題</span><span class="sxs-lookup"><span data-stu-id="e1b1f-106">Topic</span></span>|<span data-ttu-id="e1b1f-107">描述</span><span class="sxs-lookup"><span data-stu-id="e1b1f-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e1b1f-108">函數式建構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e1b1f-108">Functional Construction (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)|<span data-ttu-id="e1b1f-109">提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的功能結構概觀。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-109">Provides an overview of functional construction in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="e1b1f-110">功能結構可讓您利用單一陳述式建立所有或部分 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-110">Functional construction enables you to create all or part of your XML tree in a single statement.</span></span> <span data-ttu-id="e1b1f-111">這個主題也顯示如何在建構 XML 樹狀時內嵌查詢。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-111">This topic also shows how to embed queries when constructing an XML tree.</span></span>|  
|[<span data-ttu-id="e1b1f-112">在 C# 中建立 XML 樹狀結構 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e1b1f-112">Creating XML Trees in C# (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md)|<span data-ttu-id="e1b1f-113">顯示如何在 C# 中建立樹狀。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-113">Shows how to create trees in C#.</span></span>|  
|[<span data-ttu-id="e1b1f-114">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e1b1f-114">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)|<span data-ttu-id="e1b1f-115">顯示如何從各種來源剖析 XML。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-115">Shows how to parse XML from a variety of sources.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="e1b1f-116"> 的層級位於用來剖析 XML 的 <xref:System.Xml.XmlReader> 頂端。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-116"> is layered on top of <xref:System.Xml.XmlReader>, which is used to parse the XML.</span></span>|  
|[<span data-ttu-id="e1b1f-117">如何：使用 XmlWriter 填入 XML 樹狀結構 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e1b1f-117">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml.md)|<span data-ttu-id="e1b1f-118">顯示如何使用 <xref:System.Xml.XmlWriter> 填入 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-118">Shows how to populate an XML tree by using an <xref:System.Xml.XmlWriter>.</span></span>|  
|[<span data-ttu-id="e1b1f-119">如何：使用 XSD 進行驗證 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e1b1f-119">How to: Validate Using XSD (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md)|<span data-ttu-id="e1b1f-120">顯示如何使用 XSD 驗證 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-120">Shows how to validate an XML tree using XSD.</span></span>|  
|[<span data-ttu-id="e1b1f-121">XElement 和 XDocument 物件的有效內容</span><span class="sxs-lookup"><span data-stu-id="e1b1f-121">Valid Content of XElement and XDocument Objects</span></span>](../../../../csharp/programming-guide/concepts/linq/valid-content-of-xelement-and-xdocument-objects3.md)|<span data-ttu-id="e1b1f-122">說明可以傳遞給用於將內容加入至項目和文件之建構函式和方法的有效引數。</span><span class="sxs-lookup"><span data-stu-id="e1b1f-122">Describes the valid arguments that can be passed to the constructors and methods that are used to add content to elements and documents.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1b1f-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="e1b1f-123">See Also</span></span>  
 [<span data-ttu-id="e1b1f-124">程式設計手冊 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e1b1f-124">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
