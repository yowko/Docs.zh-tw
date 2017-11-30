---
title: "使用 XPathDocument 及 XmlDocument 讀取 XML 資料"
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
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 607d9d3616db0d0bd431fa2ca0b6aee03a85f896
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a><span data-ttu-id="e7761-102">使用 XPathDocument 及 XmlDocument 讀取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="e7761-102">Reading XML Data using XPathDocument and XmlDocument</span></span>
<span data-ttu-id="e7761-103">讀取 <xref:System.Xml.XPath?displayProperty=nameWithType> 命名空間中的 XML 文件有兩種方式。</span><span class="sxs-lookup"><span data-stu-id="e7761-103">There are two ways to read an XML document in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e7761-104">一種是使用唯讀的 <xref:System.Xml.XPath.XPathDocument> 類別讀取 XML 文件，另一種是使用 <xref:System.Xml.XmlDocument> 命名空間中可編輯的 <xref:System.Xml?displayProperty=nameWithType> 類別讀取 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e7761-104">One is to read an XML document using the read-only <xref:System.Xml.XPath.XPathDocument> class and the other is to read an XML document using the editable <xref:System.Xml.XmlDocument> class in the <xref:System.Xml?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a><span data-ttu-id="e7761-105">使用 XPathDocument 類別讀取 XML 文件</span><span class="sxs-lookup"><span data-stu-id="e7761-105">Reading XML Documents using the XPathDocument Class</span></span>  
 <span data-ttu-id="e7761-106"><xref:System.Xml.XPath.XPathDocument> 類別會使用 XPath 資料模型，以快速且唯讀的方式來表示記憶體中的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e7761-106">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="e7761-107">可使用 <xref:System.Xml.XPath.XPathDocument> 類別的六個建構函式之一，建立該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7761-107">Instances of the <xref:System.Xml.XPath.XPathDocument> class are created using one of its six constructors.</span></span> <span data-ttu-id="e7761-108">這些建構函式可讓您使用 <xref:System.IO.Stream>、<xref:System.IO.TextReader> 或 <xref:System.Xml.XmlReader> 物件，以及 XML 檔案的 `string` 路徑，讀取 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e7761-108">These constructors allow you to read an XML document using a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="e7761-109">下列範例說明如何使用 <xref:System.Xml.XPath.XPathDocument> 類別的 `string` 建構函式來讀取 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e7761-109">The following example illustrates using the <xref:System.Xml.XPath.XPathDocument> class's `string` constructor to read an XML document.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a><span data-ttu-id="e7761-110">使用 XmlDocument 類別讀取 XML 文件</span><span class="sxs-lookup"><span data-stu-id="e7761-110">Reading XML Documents using the XmlDocument Class</span></span>  
 <span data-ttu-id="e7761-111"><xref:System.Xml.XmlDocument> 類別是 XML 文件的可編輯記憶體中表示，它會實作 W3C 文件物件模型 (DOM) 層級 1 核心及核心 DOM 層級 2。</span><span class="sxs-lookup"><span data-stu-id="e7761-111">The <xref:System.Xml.XmlDocument> class is an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="e7761-112">可使用 <xref:System.Xml.XmlDocument> 類別的三種建構函式之一，來建立該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7761-112">Instances of the <xref:System.Xml.XmlDocument> class are created using one of its three constructors.</span></span> <span data-ttu-id="e7761-113">您可籍由呼叫不具參數的 <xref:System.Xml.XmlDocument> 類別建構函式，來建立新的空白<xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="e7761-113">You can create a new, empty <xref:System.Xml.XmlDocument> object by calling the <xref:System.Xml.XmlDocument> class constructor with no parameters.</span></span> <span data-ttu-id="e7761-114">呼叫該建構函式後，請使用 <xref:System.Xml.XmlDocument.Load%2A> 方法將 XML 資料從 <xref:System.Xml.XmlDocument>、<xref:System.IO.Stream> 或<xref:System.IO.TextReader> 物件，以及 XML 檔案的 <xref:System.Xml.XmlReader> 路徑載入到新的 `string` 物件。</span><span class="sxs-lookup"><span data-stu-id="e7761-114">After calling the constructor, use the <xref:System.Xml.XmlDocument.Load%2A> method to load XML data into the new <xref:System.Xml.XmlDocument> object from a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="e7761-115">下列範例說明如何使用不具參數的 <xref:System.Xml.XmlDocument> 類別建構函式及 <xref:System.Xml.XmlDocument.Load%2A> 方法來讀取 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e7761-115">The following example illustrates using the <xref:System.Xml.XmlDocument> class constructor with no parameters and the <xref:System.Xml.XmlDocument.Load%2A> method to read an XML document.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a><span data-ttu-id="e7761-116">決定 XML 文件的編碼方式</span><span class="sxs-lookup"><span data-stu-id="e7761-116">Determining the Encoding of an XML Document</span></span>  
 <span data-ttu-id="e7761-117">如先前各節所示，可使用 <xref:System.Xml.XmlReader> 物件讀取 XML 文件，並建立 <xref:System.Xml.XPath.XPathDocument> 及 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="e7761-117">An <xref:System.Xml.XmlReader> object can be used to read an XML document and to create <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> objects as shown in the previous sections.</span></span> <span data-ttu-id="e7761-118">不過，<xref:System.Xml.XmlReader> 物件可能會讀取未編碼的資料，因此不會提供任何編碼資訊。</span><span class="sxs-lookup"><span data-stu-id="e7761-118">However, an <xref:System.Xml.XmlReader> object may read data that is not encoded and as a result does not provide any encoding information.</span></span>  
  
 <span data-ttu-id="e7761-119"><xref:System.Xml.XmlTextReader> 類別會繼承 <xref:System.Xml.XmlReader> 類別，透過其 <xref:System.Xml.XmlTextReader.Encoding%2A> 屬性提供編碼資訊，並可用於建立 <xref:System.Xml.XPath.XPathDocument> 物件或 <xref:System.Xml.XmlDocument> 物件。</span><span class="sxs-lookup"><span data-stu-id="e7761-119">The <xref:System.Xml.XmlTextReader> class inherits from the <xref:System.Xml.XmlReader> class, provides encoding information using its <xref:System.Xml.XmlTextReader.Encoding%2A> property, and can be used to create an <xref:System.Xml.XPath.XPathDocument> object or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="e7761-120">如需 <xref:System.Xml.XmlTextReader> 類別提供之編碼資訊的詳細資訊，請參閱 <xref:System.Xml.XmlTextReader.Encoding%2A> 類別參考文件中的 <xref:System.Xml.XmlTextReader> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e7761-120">For more information about the encoding information provided by the <xref:System.Xml.XmlTextReader> class, see the <xref:System.Xml.XmlTextReader.Encoding%2A> property in the <xref:System.Xml.XmlTextReader> class reference documentation.</span></span>  
  
## <a name="creating-xpathnavigator-objects"></a><span data-ttu-id="e7761-121">建立 XPathNavigator 物件</span><span class="sxs-lookup"><span data-stu-id="e7761-121">Creating XPathNavigator Objects</span></span>  
 <span data-ttu-id="e7761-122">將 XML 文件讀入 <xref:System.Xml.XPath.XPathDocument> 或 <xref:System.Xml.XmlDocument> 物件後，您可以建立 <xref:System.Xml.XPath.XPathNavigator> 物件以選取、評估、巡覽以及 (在某些情況下) 編輯基礎 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="e7761-122">After you have read an XML document into either an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, you can create an <xref:System.Xml.XPath.XPathNavigator> object to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="e7761-123">除了 <xref:System.Xml.XPath.XPathDocument> 類別之外，<xref:System.Xml.XmlDocument> 及 <xref:System.Xml.XmlNode> 類別也會實作 <xref:System.Xml.XPath.IXPathNavigable> 命名空間的 <xref:System.Xml.XPath?displayProperty=nameWithType> 介面。</span><span class="sxs-lookup"><span data-stu-id="e7761-123">Both the <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> classes, in addition to the <xref:System.Xml.XmlNode> class, implement the <xref:System.Xml.XPath.IXPathNavigable> interface of the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e7761-124">所以，所有三個類別均可提供傳回 <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> 物件的 <xref:System.Xml.XPath.XPathNavigator> 方法。</span><span class="sxs-lookup"><span data-stu-id="e7761-124">As a result, all three classes provide a <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> method that returns an <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a><span data-ttu-id="e7761-125">使用 XPathNavigator 類別編輯 XML 文件</span><span class="sxs-lookup"><span data-stu-id="e7761-125">Editing XML Documents using the XPathNavigator Class</span></span>  
 <span data-ttu-id="e7761-126">除了選取、評估及巡覽 XML 資料之外，在某些情況下，<xref:System.Xml.XPath.XPathNavigator> 類別還可用於編輯 XML 文件 (根據建立該文件的物件)。</span><span class="sxs-lookup"><span data-stu-id="e7761-126">In addition to selecting, evaluating, and navigating XML data, the <xref:System.Xml.XPath.XPathNavigator> class can be used to edit an XML document in some cases, based on the object that created it.</span></span>  
  
 <span data-ttu-id="e7761-127"><xref:System.Xml.XPath.XPathDocument> 類別是唯讀的，而 <xref:System.Xml.XmlDocument> 類別則可以編輯；因此，從 <xref:System.Xml.XPath.XPathNavigator> 物件建立的 <xref:System.Xml.XPath.XPathDocument> 物件不能用來編輯 XML 文件，而從 <xref:System.Xml.XmlDocument> 物件建立的那些物件則可以。</span><span class="sxs-lookup"><span data-stu-id="e7761-127">The <xref:System.Xml.XPath.XPathDocument> class is read-only while the <xref:System.Xml.XmlDocument> class is editable and as a result, <xref:System.Xml.XPath.XPathNavigator> objects created from an <xref:System.Xml.XPath.XPathDocument> object cannot be used to edit an XML document while those created from an <xref:System.Xml.XmlDocument> object can.</span></span> <span data-ttu-id="e7761-128"><xref:System.Xml.XPath.XPathDocument> 類別應該只能用來讀取 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="e7761-128">The <xref:System.Xml.XPath.XPathDocument> class should be used to read an XML document only.</span></span> <span data-ttu-id="e7761-129">如果需要編輯 XML 文件，或要求 <xref:System.Xml.XmlDocument> 類別所提供之其他功能的存取權 (如事件處理)，應使用 <xref:System.Xml.XmlDocument> 類別。</span><span class="sxs-lookup"><span data-stu-id="e7761-129">In cases where you need to edit an XML document, or require access to the additional functionality provided by the <xref:System.Xml.XmlDocument> class, like event handling, the <xref:System.Xml.XmlDocument> class should be used.</span></span>  
  
 <span data-ttu-id="e7761-130"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 類別的 <xref:System.Xml.XPath.XPathNavigator> 屬性可指定 <xref:System.Xml.XPath.XPathNavigator> 物件是否可編輯 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="e7761-130">The <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class specifies if an <xref:System.Xml.XPath.XPathNavigator> object may edit XML data.</span></span>  
  
 <span data-ttu-id="e7761-131">下表說明每個類別的 <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 屬性值。</span><span class="sxs-lookup"><span data-stu-id="e7761-131">The following table describes the value of the <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property for each class.</span></span>  
  
|<span data-ttu-id="e7761-132"><xref:System.Xml.XPath.IXPathNavigable> 實作</span><span class="sxs-lookup"><span data-stu-id="e7761-132"><xref:System.Xml.XPath.IXPathNavigable> Implementation</span></span>|<span data-ttu-id="e7761-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> 值</span><span class="sxs-lookup"><span data-stu-id="e7761-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Value</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a><span data-ttu-id="e7761-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7761-134">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="e7761-135">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="e7761-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="e7761-136">使用 XPathNavigator 存取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="e7761-136">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="e7761-137">使用 XPathNavigator 編輯 XML 資料</span><span class="sxs-lookup"><span data-stu-id="e7761-137">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="e7761-138">使用 xpathnavigator 進行結構描述驗證</span><span class="sxs-lookup"><span data-stu-id="e7761-138">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
