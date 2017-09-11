---
title: "剖析 XML (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 7ea83f83-a779-423a-9875-4ea4e51f97fc
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 13807e57b3616d51bd88b37d0acc703a18445a02
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="parsing-xml-c"></a><span data-ttu-id="7c960-102">剖析 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7c960-102">Parsing XML (C#)</span></span>
<span data-ttu-id="7c960-103">本節中的主題描述如何剖析 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="7c960-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c960-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="7c960-104">In This Section</span></span>  
  
|<span data-ttu-id="7c960-105">主題</span><span class="sxs-lookup"><span data-stu-id="7c960-105">Topic</span></span>|<span data-ttu-id="7c960-106">描述</span><span class="sxs-lookup"><span data-stu-id="7c960-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7c960-107">如何：剖析字串 (C#)</span><span class="sxs-lookup"><span data-stu-id="7c960-107">How to: Parse a String (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="7c960-108">顯示如何剖析字串以建立 XML 樹狀。</span><span class="sxs-lookup"><span data-stu-id="7c960-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="7c960-109">如何：從檔案載入 XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7c960-109">How to: Load XML from a File (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="7c960-110">顯示如何使用 <xref:System.Xml.Linq.XElement.Load%2A> 方法，從 URI 載入 XML。</span><span class="sxs-lookup"><span data-stu-id="7c960-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="7c960-111">載入或剖析 XML 時保留空白字元</span><span class="sxs-lookup"><span data-stu-id="7c960-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml1.md)|<span data-ttu-id="7c960-112">描述如何在載入 XML 樹狀結構時，控制 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的空白字元行為。</span><span class="sxs-lookup"><span data-stu-id="7c960-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="7c960-113">如何：攔截剖析錯誤 (C#)</span><span class="sxs-lookup"><span data-stu-id="7c960-113">How to: Catch Parsing Errors (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="7c960-114">顯示如何偵測格式錯誤或無效的 XML。</span><span class="sxs-lookup"><span data-stu-id="7c960-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="7c960-115">如何：從 XmlReader 建立樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="7c960-115">How to: Create a Tree from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="7c960-116">顯示如何從 <xref:System.Xml.XmlReader> 直接建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="7c960-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="7c960-117">如何：從 XmlReader 串流 XML 片段 (C#)</span><span class="sxs-lookup"><span data-stu-id="7c960-117">How to: Stream XML Fragments from an XmlReader (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="7c960-118">顯示如何使用 <xref:System.Xml.XmlReader> 串流 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="7c960-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="7c960-119">當您必須處理非常大的 XML 檔案時，可能無法將整個 XML 樹狀結構載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="7c960-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="7c960-120">但是，您可以串流 XML 片段。</span><span class="sxs-lookup"><span data-stu-id="7c960-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c960-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c960-121">See Also</span></span>  
 [<span data-ttu-id="7c960-122">建立 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="7c960-122">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

