---
title: 如何：從檔案、字串或資料流載入 XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 241f6552e46d7689b42a409ba44bc747984773ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647627"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="5ec63-102">如何：從檔案、字串或資料流載入 XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ec63-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="5ec63-103">您可以建立[XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)，並將它們從外部來源，例如檔案、 字串或資料流的內容填入使用數種方法。</span><span class="sxs-lookup"><span data-stu-id="5ec63-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="5ec63-104">在下列範例會顯示這些方法。</span><span class="sxs-lookup"><span data-stu-id="5ec63-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="5ec63-105">若要從檔案載入 XML</span><span class="sxs-lookup"><span data-stu-id="5ec63-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="5ec63-106">若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件從檔案、 使用`Load`方法。</span><span class="sxs-lookup"><span data-stu-id="5ec63-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="5ec63-107">這個方法可以採用檔案路徑、 文字資料流或 XML 資料流，做為輸入。</span><span class="sxs-lookup"><span data-stu-id="5ec63-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="5ec63-108">下列程式碼範例示範使用<xref:System.Xml.Linq.XDocument.Load%28System.String%29>方法來填入<xref:System.Xml.Linq.XDocument>物件之 XML 文字檔案。</span><span class="sxs-lookup"><span data-stu-id="5ec63-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="5ec63-109">從字串載入 XML</span><span class="sxs-lookup"><span data-stu-id="5ec63-109">To load XML from a string</span></span>  
  
-   <span data-ttu-id="5ec63-110">若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件的字串，您可以使用`Parse`方法。</span><span class="sxs-lookup"><span data-stu-id="5ec63-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="5ec63-111">下列程式碼範例示範使用<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>方法來填入<xref:System.Xml.Linq.XDocument>以 XML 字串中的物件。</span><span class="sxs-lookup"><span data-stu-id="5ec63-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="5ec63-112">若要從資料流載入 XML</span><span class="sxs-lookup"><span data-stu-id="5ec63-112">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="5ec63-113">若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>物件從資料流中，您可以使用`Load`方法或<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="5ec63-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5ec63-114">下列程式碼範例示範使用<xref:System.Xml.Linq.XNode.ReadFrom%2A>方法來填入<xref:System.Xml.Linq.XDocument>具有從 XML 資料流的 XML 物件。</span><span class="sxs-lookup"><span data-stu-id="5ec63-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5ec63-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ec63-115">See Also</span></span>  
 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
 <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="5ec63-116">XML 常值</span><span class="sxs-lookup"><span data-stu-id="5ec63-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="5ec63-117">XML</span><span class="sxs-lookup"><span data-stu-id="5ec63-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="5ec63-118">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="5ec63-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
