---
title: HOW TO：從檔案、 字串或 Stream (Visual Basic) 載入 XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: 2b9da2062068ef25c5df97ef19b1502999ea78ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052530"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="4bf33-102">HOW TO：從檔案、 字串或 Stream (Visual Basic) 載入 XML</span><span class="sxs-lookup"><span data-stu-id="4bf33-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="4bf33-103">您可以建立[XML 常值](../../../../visual-basic/language-reference/xml-literals/index.md)並且填入從外部來源，例如檔案、 字串或資料流的內容使用幾種方法。</span><span class="sxs-lookup"><span data-stu-id="4bf33-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="4bf33-104">在下列範例會顯示這些方法。</span><span class="sxs-lookup"><span data-stu-id="4bf33-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="4bf33-105">若要從檔案載入 XML</span><span class="sxs-lookup"><span data-stu-id="4bf33-105">To load XML from a file</span></span>  
  
- <span data-ttu-id="4bf33-106">若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XDocument>檔案中，使用從物件`Load`方法。</span><span class="sxs-lookup"><span data-stu-id="4bf33-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="4bf33-107">這個方法可能需要的檔案路徑、 文字資料流或 XML 資料流，做為輸入。</span><span class="sxs-lookup"><span data-stu-id="4bf33-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="4bf33-108">下列程式碼範例示範使用<xref:System.Xml.Linq.XDocument.Load%28System.String%29>方法來填入<xref:System.Xml.Linq.XDocument>具有來自文字檔案的 XML 物件。</span><span class="sxs-lookup"><span data-stu-id="4bf33-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="4bf33-109">從字串載入 XML</span><span class="sxs-lookup"><span data-stu-id="4bf33-109">To load XML from a string</span></span>  
  
- <span data-ttu-id="4bf33-110">若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XDocument>物件的字串，您可以使用`Parse`方法。</span><span class="sxs-lookup"><span data-stu-id="4bf33-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="4bf33-111">下列程式碼範例示範使用<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>方法來填入<xref:System.Xml.Linq.XDocument>以 XML 字串中的物件。</span><span class="sxs-lookup"><span data-stu-id="4bf33-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="4bf33-112">若要從資料流載入 XML</span><span class="sxs-lookup"><span data-stu-id="4bf33-112">To load XML from a stream</span></span>  
  
- <span data-ttu-id="4bf33-113">若要填入 XML 常值，例如<xref:System.Xml.Linq.XElement>或是<xref:System.Xml.Linq.XDocument>物件從資料流中，您可以使用`Load`方法或<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="4bf33-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="4bf33-114">下列程式碼範例示範使用<xref:System.Xml.Linq.XNode.ReadFrom%2A>方法來填入<xref:System.Xml.Linq.XDocument>具有從 XML 資料流的 XML 物件。</span><span class="sxs-lookup"><span data-stu-id="4bf33-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="4bf33-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bf33-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4bf33-116">XML 常值</span><span class="sxs-lookup"><span data-stu-id="4bf33-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="4bf33-117">XML</span><span class="sxs-lookup"><span data-stu-id="4bf33-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="4bf33-118">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="4bf33-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
