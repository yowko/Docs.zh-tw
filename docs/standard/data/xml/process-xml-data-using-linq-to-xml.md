---
title: 使用 LINQ to XML 處理 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1554c3e2b13dd0ea0d64ccd7e7caee0a1e0dd3f9
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835561"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="1a4b2-102">使用 LINQ to XML 處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="1a4b2-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="1a4b2-103">LINQ to XML 是 .NET Framework 3.5 版中用來處理 XML 資料的新模型。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="1a4b2-104">LINQ to XML 可讓開發人員進行預期對 XML 資料做的所有事情：查詢、修改、建立、儲存和序列化 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="1a4b2-105">真正的優點則在於查詢和建立功能。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="1a4b2-106">LINQ to XML 中的查詢非常簡潔且具表達性，使用的語法比較類似於 SQL，而比較不像 XPath 或 XQuery。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="1a4b2-107">由於查詢結果可以當做項目或屬性的集合傳回，而且可以當做 XElement 物件的參數使用，所以 XML 樹狀結構可以輕鬆地在不同形狀之間轉換。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="1a4b2-108">LINQ to XML 會利用 .NET Framework 3.5 版中的 Language-integrated Query (LINQ) 技術。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="1a4b2-109">LINQ 會擴充 C# 和 Visual Basic 的語言語法，以提供可擴充至任何可能資料存放區的強大查詢功能。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="1a4b2-110">如需其用法的詳細討論，請參閱 [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) 和 [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="1a4b2-111">如需 LINQ 架構的概觀，請參閱 [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) 或 [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="1a4b2-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4b2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a4b2-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="1a4b2-113">LINQ to XML 與DOM 的比較 (C#)</span><span class="sxs-lookup"><span data-stu-id="1a4b2-113">LINQ to XML vs. DOM (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="1a4b2-114">LINQ to XML 與DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a4b2-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="1a4b2-115">LINQ to XML 與其他 XML 技術 (C#) 的比較</span><span class="sxs-lookup"><span data-stu-id="1a4b2-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- [<span data-ttu-id="1a4b2-116">LINQ to XML 與其他 XML 技術 (Visual Basic) 的比較</span><span class="sxs-lookup"><span data-stu-id="1a4b2-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
