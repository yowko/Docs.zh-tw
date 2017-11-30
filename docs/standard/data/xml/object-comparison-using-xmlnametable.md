---
title: "使用 XmlNameTable 進行物件比較"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd1a3bad69499b4804299adecabad3a43b5eab1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="1c171-102">使用 XmlNameTable 進行物件比較</span><span class="sxs-lookup"><span data-stu-id="1c171-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="1c171-103">**XmlDocuments**、 建立時，特別針對該文件建立一個名稱表。</span><span class="sxs-lookup"><span data-stu-id="1c171-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="1c171-104">當 XML 載入文件，或建立新的項目或屬性時，屬性和項目名稱會放入**XmlNameTable**。</span><span class="sxs-lookup"><span data-stu-id="1c171-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="1c171-105">您也可以建立**XmlDocument**使用現有**NameTable**從其他文件。</span><span class="sxs-lookup"><span data-stu-id="1c171-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="1c171-106">當**XmlDocuments**的建構函式以建立**XmlNameTable**參數時，文件具有存取權的節點名稱、 命名空間和前置詞已經儲存在**XmlNameTable**。</span><span class="sxs-lookup"><span data-stu-id="1c171-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="1c171-107">無論名稱表是以何種名稱載入，一旦名稱儲存在表格後，就可以快速地透過物件比較來比較名稱，而不需要進行字串比較。</span><span class="sxs-lookup"><span data-stu-id="1c171-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="1c171-108">字串也可以加入至名稱表使用<xref:System.Xml.NameTable.Add%2A>。</span><span class="sxs-lookup"><span data-stu-id="1c171-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="1c171-109">下列程式碼範例顯示要建立的名稱表和字串**MyString**加入到資料表。</span><span class="sxs-lookup"><span data-stu-id="1c171-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="1c171-110">在這之後， **XmlDocument**會建立使用該資料表和中的項目和屬性名稱**Myfile.xml**會加入至現有的名稱表。</span><span class="sxs-lookup"><span data-stu-id="1c171-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
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
  
 <span data-ttu-id="1c171-111">下列程式碼範例顯示文件的建立，並且會將兩個新項目加入至文件，這兩個新項目也會加入至文件名稱表，以及名稱上的物件比較。</span><span class="sxs-lookup"><span data-stu-id="1c171-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
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
  
 <span data-ttu-id="1c171-112">上述在兩個文件之間傳遞的名稱表是相同類型的文件要重複處理 (例如在電子商務網站上排序文件) 情況下的典型案例，它會依據 XML 結構描述定義語言 (XSD) 描述結構或文件類型定義 (DTD)，而且相同的字串會重複。</span><span class="sxs-lookup"><span data-stu-id="1c171-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="1c171-113">當多重文件中出現相同的項目名稱時，使用相同的名稱表可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="1c171-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c171-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c171-114">See Also</span></span>  
 [<span data-ttu-id="1c171-115">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="1c171-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
