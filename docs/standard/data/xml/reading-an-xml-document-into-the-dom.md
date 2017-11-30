---
title: "將 XML 文件讀取到 DOM"
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
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b8844705b492574443ff4f37de33ccaf1f5fedd7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="ae2d4-102">將 XML 文件讀取到 DOM</span><span class="sxs-lookup"><span data-stu-id="ae2d4-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="ae2d4-103">從不同的格式將 XML 資訊讀取到記憶體。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="ae2d4-104">可從字串、資料流、URL、文字讀取器或衍生自 <xref:System.Xml.XmlReader> 的類別讀取它。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="ae2d4-105"><xref:System.Xml.XmlDocument.Load%2A> 方法將文件引入記憶體，並擁有可從各個不同格式取得資料的多載方法。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="ae2d4-106">另外還有一個 <xref:System.Xml.XmlDocument.LoadXml%2A> 方法，可從字串讀取 XML。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="ae2d4-107">不同的 <xref:System.Xml.XmlDocument.Load%2A> 方法會影響載入 XML 文件物件模型 (DOM) 時建立的節點。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="ae2d4-108">下表列出某些 <xref:System.Xml.XmlDocument.Load%2A> 方法及說明這些方法之主題間的差異。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="ae2d4-109">主旨</span><span class="sxs-lookup"><span data-stu-id="ae2d4-109">Subject</span></span>|<span data-ttu-id="ae2d4-110">主題</span><span class="sxs-lookup"><span data-stu-id="ae2d4-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="ae2d4-111">建立泛空白字元節點</span><span class="sxs-lookup"><span data-stu-id="ae2d4-111">Creation of white space nodes</span></span>|<span data-ttu-id="ae2d4-112">用來載入 DOM 的物件會影響在 DOM 中產生的泛空白字元及顯著泛空白字元節點。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="ae2d4-113">如需詳細資訊，請參閱[泛空白字元和顯著泛空白字元處理載入 DOM 時](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="ae2d4-114">從特定節點開始載入 XML 或載入整個 XML 文件</span><span class="sxs-lookup"><span data-stu-id="ae2d4-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="ae2d4-115">使用<xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType>方法資料可以從特定節點載入至 dom。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="ae2d4-116">如需詳細資訊，請參閱[從讀取器載入資料](../../../../docs/standard/data/xml/load-data-from-a-reader.md)。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-116">For more information, see [Load Data from a Reader](../../../../docs/standard/data/xml/load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="ae2d4-117">載入 XML 時進行驗證</span><span class="sxs-lookup"><span data-stu-id="ae2d4-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="ae2d4-118">可在將 XML 資料載入至 DOM 時對其進行驗證。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="ae2d4-119">使用驗證 <xref:System.Xml.XmlReader> 來完成此作業。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="ae2d4-120">如需在載入時，驗證 XML 的詳細資訊，請參閱[驗證 DOM 中的 XML 文件](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="ae2d4-121">下列範例顯示以 <xref:System.Xml.XmlDocument.LoadXml%2A> 方法載入的 XML，以及隨後儲存至稱為 `data.xml` 之文字檔的資料。</span><span class="sxs-lookup"><span data-stu-id="ae2d4-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae2d4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae2d4-122">See Also</span></span>  
 [<span data-ttu-id="ae2d4-123">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="ae2d4-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
