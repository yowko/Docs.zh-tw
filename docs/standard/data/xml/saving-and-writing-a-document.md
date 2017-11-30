---
title: "儲存與寫入文件"
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
ms.assetid: 097b0cb1-5743-4c3a-86ef-caf5cbe6750d
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ad656e2db17e44733b5718fe2e3a2a48afcb1381
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="saving-and-writing-a-document"></a><span data-ttu-id="d5ea3-102">儲存與寫入文件</span><span class="sxs-lookup"><span data-stu-id="d5ea3-102">Saving and Writing a Document</span></span>
<span data-ttu-id="d5ea3-103">載入及儲存 <xref:System.Xml.XmlDocument> 時，儲存的文件與原始文件在下列方面可能不同：</span><span class="sxs-lookup"><span data-stu-id="d5ea3-103">When you load and save an <xref:System.Xml.XmlDocument>, the saved document may differ from the original in the following ways:</span></span>  
  
-   <span data-ttu-id="d5ea3-104">如果在呼叫 <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> 方法之前將 `true` 屬性設為 <xref:System.Xml.XmlDocument.Save%2A>，則在輸出中會保留文件中的泛空白字元；如果此屬性為 `false`，則 <xref:System.Xml.XmlDocument> 會自動縮排輸出。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-104">If the <xref:System.Xml.XmlDocument.PreserveWhitespace%2A> property is set to `true` before the <xref:System.Xml.XmlDocument.Save%2A> method is called, white space in the document is preserved in the output; if this property is `false`, <xref:System.Xml.XmlDocument> auto-indents the output.</span></span>  
  
-   <span data-ttu-id="d5ea3-105">屬性之間的所有泛空白字元會縮減為單一空格字元。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-105">All the white space between attributes is reduced to a single space character.</span></span>  
  
-   <span data-ttu-id="d5ea3-106">變更項目之間的泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-106">The white space between elements is changed.</span></span> <span data-ttu-id="d5ea3-107">保留顯著的泛空白字元，但不保留不顯著的泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-107">Significant white space is preserved and insignificant white space is not.</span></span> <span data-ttu-id="d5ea3-108">但在儲存文件時，它會使用<xref:System.Xml.XmlTextWriter>**縮排**整齊列印，讓它更容易閱讀輸出的預設模式。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-108">But when the document is saved, it will use the <xref:System.Xml.XmlTextWriter> **Indenting** mode by default to neatly print the output to make it more readable.</span></span>  
  
-   <span data-ttu-id="d5ea3-109">依預設，會將屬性值周圍的引號字元變更為雙引號。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-109">The quote character used around attribute values is changed to double quote by default.</span></span> <span data-ttu-id="d5ea3-110">您可以使用 <xref:System.Xml.XmlTextReader.QuoteChar%2A> 上的 <xref:System.Xml.XmlTextWriter> 屬性，將引號字元設為雙引號或單引號。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-110">You can use the <xref:System.Xml.XmlTextReader.QuoteChar%2A> property on <xref:System.Xml.XmlTextWriter> to set the quote character to either double quote or single quote.</span></span>  
  
-   <span data-ttu-id="d5ea3-111">依預設，會展開 `{` 之類的數字字元實體。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-111">By default, numeric character entities like `{` are expanded.</span></span>  
  
-   <span data-ttu-id="d5ea3-112">不保留在輸入文件中發現的位元組順序標記。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-112">The byte-order mark found in the input document is not preserved.</span></span> <span data-ttu-id="d5ea3-113">除非您明確建立指定不同編碼的 XML 宣告，否則會將 UCS-2 儲存為 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-113">UCS-2 is saved as UTF-8 unless you explicitly create an XML declaration that specifies a different encoding.</span></span>  
  
-   <span data-ttu-id="d5ea3-114">如果您要將 <xref:System.Xml.XmlDocument> 寫入檔案或資料流，則寫出的輸出與文件的內容相同。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-114">If you want to write out the <xref:System.Xml.XmlDocument> into a file or stream, the output written out is the same as the content of the document.</span></span> <span data-ttu-id="d5ea3-115">換言之，唯有當文件中已包含一個 <xref:System.Xml.XmlDeclaration> 時，才會將其寫出，而且寫出文件時所使用的編碼與宣告節點中指定的編碼相同。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-115">That is, the <xref:System.Xml.XmlDeclaration> is written out only if there is one contained in the document, and the encoding used when writing out the document is the same encoding given in the declaration node.</span></span>  
  
## <a name="writing-an-xmldeclaration"></a><span data-ttu-id="d5ea3-116">寫入 XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="d5ea3-116">Writing an XmlDeclaration</span></span>  
 <span data-ttu-id="d5ea3-117">除了 <xref:System.Xml.XmlDocument> 及 <xref:System.Xml.XmlDeclaration> 的 <xref:System.Xml.XmlNode.OuterXml%2A> 方法之外，<xref:System.Xml.XmlNode.InnerXml%2A>、<xref:System.Xml.XmlNode.WriteTo%2A> 及 <xref:System.Xml.XmlDocument> 的<xref:System.Xml.XmlDocument.Save%2A> 及 <xref:System.Xml.XmlDocument.WriteContentTo%2A> 成員也會建立 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-117">The <xref:System.Xml.XmlDocument> and <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlNode.InnerXml%2A>, and <xref:System.Xml.XmlNode.WriteTo%2A>, in addition to the <xref:System.Xml.XmlDocument> methods of <xref:System.Xml.XmlDocument.Save%2A> and <xref:System.Xml.XmlDocument.WriteContentTo%2A>, create an XML declaration.</span></span>  
  
 <span data-ttu-id="d5ea3-118">對於 <xref:System.Xml.XmlDocument>、<xref:System.Xml.XmlNode.OuterXml%2A> 與 <xref:System.Xml.XmlDocument.InnerXml%2A>、<xref:System.Xml.XmlDocument.Save%2A> 及 <xref:System.Xml.XmlDocument.WriteTo%2A> 方法的 <xref:System.Xml.XmlDocument.WriteContentTo%2A> 屬性，XML 宣告中寫出的編碼取自 <xref:System.Xml.XmlDeclaration> 節點。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-118">For the <xref:System.Xml.XmlDocument> properties of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDocument.InnerXml%2A>, and the <xref:System.Xml.XmlDocument.Save%2A>, <xref:System.Xml.XmlDocument.WriteTo%2A>, and <xref:System.Xml.XmlDocument.WriteContentTo%2A> methods, the encoding written out in the XML declaration is taken from the <xref:System.Xml.XmlDeclaration> node.</span></span> <span data-ttu-id="d5ea3-119">如果不存在 <xref:System.Xml.XmlDeclaration> 節點，則不會寫出 <xref:System.Xml.XmlDeclaration>。如果 <xref:System.Xml.XmlDeclaration> 節點中沒有編碼，則不會在 XML 宣告中寫出編碼。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-119">If there is no <xref:System.Xml.XmlDeclaration> node, <xref:System.Xml.XmlDeclaration> is not written out. If there is no encoding in the <xref:System.Xml.XmlDeclaration> node, encoding is not written out in the XML declaration.</span></span>  
  
 <span data-ttu-id="d5ea3-120"><xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> 及 <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> 方法始終會寫出 <xref:System.Xml.XmlDeclaration>。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-120">The <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> and <xref:System.Xml.XmlDocument.Save%2A?displayProperty=nameWithType> methods always write out an <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="d5ea3-121">這些方法從其正寫入的寫入器取得編碼。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-121">These methods take the encoding from the writer that it is writing to.</span></span> <span data-ttu-id="d5ea3-122">換言之，寫入器上的編碼值會覆寫文件上及 <xref:System.Xml.XmlDeclaration> 中的編碼。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-122">That is, the encoding value on the writer overrides the encoding on the document and in the <xref:System.Xml.XmlDeclaration>.</span></span> <span data-ttu-id="d5ea3-123">例如，下列程式碼不會將編碼寫入輸出檔案 `out.xml` 中發現的 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-123">For example, the following code does not write an encoding in the XML declaration found in the output file `out.xml`.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
Dim tw As XmlTextWriter = New XmlTextWriter("out.xml", Nothing)  
doc.Load("text.xml")  
doc.Save(tw)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlTextWriter tw = new XmlTextWriter("out.xml", null);  
doc.Load("text.xml");  
doc.Save(tw);  
```  
  
 <span data-ttu-id="d5ea3-124">針對 <xref:System.Xml.XmlDocument.Save%2A> 方法，會使用 <xref:System.Xml.XmlWriter.WriteStartDocument%2A> 類別中的 <xref:System.Xml.XmlWriter> 方法寫出 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-124">For the <xref:System.Xml.XmlDocument.Save%2A> method, the XML declaration is written out using the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method in the <xref:System.Xml.XmlWriter> class.</span></span> <span data-ttu-id="d5ea3-125">因此，覆寫 <xref:System.Xml.XmlWriter.WriteStartDocument%2A> 方法會變更文件開頭的寫入方式。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-125">Therefore, overwriting the <xref:System.Xml.XmlWriter.WriteStartDocument%2A> method changes how the start of the document is written.</span></span>  
  
 <span data-ttu-id="d5ea3-126">針對 <xref:System.Xml.XmlDeclaration>、<xref:System.Xml.XmlNode.OuterXml%2A> 及 <xref:System.Xml.XmlDeclaration.WriteTo%2A> 的 <xref:System.Xml.XmlNode.InnerXml%2A> 成員，如果未設定 <xref:System.Xml.XmlDeclaration.Encoding%2A> 屬性，則不會寫出編碼。否則，在 XML 宣告中寫出的編碼與在 <xref:System.Xml.XmlDeclaration.Encoding%2A> 屬性中發現的編碼相同。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-126">For the <xref:System.Xml.XmlDeclaration> members of <xref:System.Xml.XmlNode.OuterXml%2A>, <xref:System.Xml.XmlDeclaration.WriteTo%2A>, and <xref:System.Xml.XmlNode.InnerXml%2A>, if the <xref:System.Xml.XmlDeclaration.Encoding%2A> property is not set, no encoding is written out. Otherwise, the encoding written out in the XML declaration is the same as the encoding found in the <xref:System.Xml.XmlDeclaration.Encoding%2A> property.</span></span>  
  
## <a name="writing-document-content-using-the-outerxml-property"></a><span data-ttu-id="d5ea3-127">使用 OuterXml 屬性寫入文件內容</span><span class="sxs-lookup"><span data-stu-id="d5ea3-127">Writing Document Content Using the OuterXml Property</span></span>  
 <span data-ttu-id="d5ea3-128"><xref:System.Xml.XmlNode.OuterXml%2A> 屬性是全球資訊網協會 (W3C) XML 文件物件模型 (DOM) 標準的 Microsoft 擴充程式。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-128">The <xref:System.Xml.XmlNode.OuterXml%2A> property is a Microsoft extension to the World Wide Web Consortium (W3C) XML Document Object Model (DOM) standards.</span></span> <span data-ttu-id="d5ea3-129"><xref:System.Xml.XmlNode.OuterXml%2A> 屬性可用於取得整個 XML 文件的標記，或僅取得單一節點及其子節點的標記。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-129">The <xref:System.Xml.XmlNode.OuterXml%2A> property is used to get the markup of the whole XML document, or just the markup of a single node and its child nodes.</span></span> <span data-ttu-id="d5ea3-130"><xref:System.Xml.XmlNode.OuterXml%2A> 會傳回表示給定節點及其所有子節點的標記。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-130"><xref:System.Xml.XmlNode.OuterXml%2A> returns the markup representing the given node and all its child nodes.</span></span>  
  
 <span data-ttu-id="d5ea3-131">下列程式碼範例顯示如何將整個文件儲存為字串。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-131">The following code sample shows how to save a document in its entirety as a string.</span></span>  
  
```vb  
Dim mydoc As New XmlDocument()  
' Perform application needs here, like mydoc.Load("myfile");  
' Now save the entire document to a string variable called "xml".  
Dim xml As String = mydoc.OuterXml  
```  
  
```csharp  
XmlDocument mydoc = new XmlDocument();  
// Perform application needs here, like mydoc.Load("myfile");  
// Now save the entire document to a string variable called "xml".  
string xml = mydoc.OuterXml;  
```  
  
 <span data-ttu-id="d5ea3-132">下列程式碼範例顯示如何只儲存文件項目。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-132">The following code sample shows how to save only the document element.</span></span>  
  
```vb  
' For the content of the Document Element only.  
Dim xml As String = mydoc.DocumentElement.OuterXml  
```  
  
```csharp  
// For the content of the Document Element only.  
string xml = mydoc.DocumentElement.OuterXml;  
```  
  
 <span data-ttu-id="d5ea3-133">相反地，如果您需要子節點的內容，則可使用 <xref:System.Xml.XmlNode.InnerText%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d5ea3-133">In contrast, you can use the <xref:System.Xml.XmlNode.InnerText%2A> property if you want the content of child nodes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ea3-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5ea3-134">See Also</span></span>  
 [<span data-ttu-id="d5ea3-135">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="d5ea3-135">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
