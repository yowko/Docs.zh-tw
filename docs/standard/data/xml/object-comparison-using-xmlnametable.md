---
title: 使用 XmlNameTable 進行物件比較
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 814f5434dd0473b3b1dd613a2eba14a828c464d9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862775"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="262d3-102">使用 XmlNameTable 進行物件比較</span><span class="sxs-lookup"><span data-stu-id="262d3-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="262d3-103">建立 **XmlDocuments** 時，會為此文件特別建立一個名稱表。</span><span class="sxs-lookup"><span data-stu-id="262d3-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="262d3-104">當 XML 載入文件，或新項目或屬性建立時，屬性和項目名稱會放入 **XmlNameTable**。</span><span class="sxs-lookup"><span data-stu-id="262d3-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="262d3-105">您也可以使用另一個文件中現有的 **NameTable** 來建立 **XmlDocument**。</span><span class="sxs-lookup"><span data-stu-id="262d3-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="262d3-106">當 **XmlDocuments** 是以使用 **XmlNameTable** 參數的建構函式建立時，文件可以存取已經儲存在 **XmlNameTable** 中的節點名稱、命名空間和前置詞。</span><span class="sxs-lookup"><span data-stu-id="262d3-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="262d3-107">無論名稱表是以何種名稱載入，一旦名稱儲存在表格後，就可以快速地透過物件比較來比較名稱，而不需要進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="262d3-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="262d3-108">字串也可以使用 <xref:System.Xml.NameTable.Add%2A> 加入至名稱表。</span><span class="sxs-lookup"><span data-stu-id="262d3-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="262d3-109">下列程式碼範例將說明要建立的名稱表，以及要加入表格的字串 **MyString**。</span><span class="sxs-lookup"><span data-stu-id="262d3-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="262d3-110">之後，**XmlDocument** 會透過此表格來建立，並且 **Myfile.xml** 中的項目和屬性名稱也會加入至現有的名稱表。</span><span class="sxs-lookup"><span data-stu-id="262d3-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="262d3-111">下列程式碼範例顯示文件的建立，並且會將兩個新項目加入至文件，這兩個新項目也會加入至文件名稱表，以及名稱上的物件比較。</span><span class="sxs-lookup"><span data-stu-id="262d3-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="262d3-112">上述在兩個文件之間傳遞的名稱表是相同類型的文件要重複處理 (例如在電子商務網站上排序文件) 情況下的典型案例，它會依據 XML 結構描述定義語言 (XSD) 描述結構或文件類型定義 (DTD)，而且相同的字串會重複。</span><span class="sxs-lookup"><span data-stu-id="262d3-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="262d3-113">當多重文件中出現相同的項目名稱時，使用相同的名稱表可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="262d3-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="262d3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="262d3-114">See also</span></span>

- [<span data-ttu-id="262d3-115">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="262d3-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
