---
title: 建立 XML 文件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b76140fb7d79b1e191c0451cd7556963130d224a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45646177"
---
# <a name="xml-document-creation"></a><span data-ttu-id="f8c33-102">建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="f8c33-102">XML Document Creation</span></span>
<span data-ttu-id="f8c33-103">有兩種方式可用來建立 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="f8c33-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="f8c33-104">一種方法是不用參數建立 **XmlDocument**。</span><span class="sxs-lookup"><span data-stu-id="f8c33-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="f8c33-105">另一種方法是建立 **XmlDocument**，並且將 XmlNameTable 當作參數傳給它。</span><span class="sxs-lookup"><span data-stu-id="f8c33-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="f8c33-106">下列範例顯示如何在不使用參數的情況下，建立新的空白 **XmlDocument**。</span><span class="sxs-lookup"><span data-stu-id="f8c33-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="f8c33-107">一旦文件建立之後，您可以使用 **Load** 方法，將來自字串、資料流、URL、文字讀取器或 **XmlReader** 衍生類別的資料載入該文件。</span><span class="sxs-lookup"><span data-stu-id="f8c33-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="f8c33-108">另一個 Load 方法是 **LoadXML** 方法，它會從字串中讀取 XML。</span><span class="sxs-lookup"><span data-stu-id="f8c33-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="f8c33-109">如需各種 **Load** 方法的詳細資訊，請參閱[將 XML 文件讀入 DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c33-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="f8c33-110">有另一種類別叫做 **XmlNameTable**。</span><span class="sxs-lookup"><span data-stu-id="f8c33-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="f8c33-111">這個類別是原子化字串物件的表格。</span><span class="sxs-lookup"><span data-stu-id="f8c33-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="f8c33-112">這個表格可為 XML 剖析器提供一種有效的方式，用以針對 XML 文件中所有重複的項目和屬性名稱使用相同的字串物件。</span><span class="sxs-lookup"><span data-stu-id="f8c33-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="f8c33-113">當文件依照上述方式建立時，**XmlNameTable** 也會自動建立，並且會在載入文件時，同時載入其屬性和項目名稱。</span><span class="sxs-lookup"><span data-stu-id="f8c33-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="f8c33-114">如果您已經有一個具有名稱表格的文件，而且這些名稱在另一個文件也很有用，則可以使用以 **XmlNameTable** 做為參數的 **Load** 方法來建立新文件。</span><span class="sxs-lookup"><span data-stu-id="f8c33-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="f8c33-115">當文件以這種方法建立時，它會使用含有已經從其他文件載入之所有屬性和項目的現有 **XmlNameTable**。</span><span class="sxs-lookup"><span data-stu-id="f8c33-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="f8c33-116">它可以用來有效地比較項目和屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="f8c33-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="f8c33-117">如需 **XmlNameTable** 的詳細資訊，請參閱[使用 XmlNameTable 進行物件比較](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)。</span><span class="sxs-lookup"><span data-stu-id="f8c33-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="f8c33-118">如需參考，請參閱 <xref:System.Xml.XmlNameTable>。</span><span class="sxs-lookup"><span data-stu-id="f8c33-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c33-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8c33-119">See also</span></span>

- [<span data-ttu-id="f8c33-120">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="f8c33-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
