---
title: 作法：從檔案、字串或資料流程載入 XML （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: ba88ae19abc216a318d6c2069ab0846d5db8a346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054171"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="d2d27-102">HOW TO：從檔案、字串或資料流程載入 XML （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="d2d27-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>

<span data-ttu-id="d2d27-103">您可以使用數種方法來建立[XML 常](../../../../visual-basic/language-reference/xml-literals/index.md)值，並以外部來源（例如檔案、字串或資料流程）的內容填入。</span><span class="sxs-lookup"><span data-stu-id="d2d27-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="d2d27-104">下列範例會顯示這些方法。</span><span class="sxs-lookup"><span data-stu-id="d2d27-104">These methods are shown in the following examples.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-load-xml-from-a-file"></a><span data-ttu-id="d2d27-105">從檔案載入 XML</span><span class="sxs-lookup"><span data-stu-id="d2d27-105">To load XML from a file</span></span>

<span data-ttu-id="d2d27-106">若要從檔案填入 XML 常值<xref:System.Xml.Linq.XElement> （ <xref:System.Xml.Linq.XDocument>例如）或物件，請使用`Load`方法。</span><span class="sxs-lookup"><span data-stu-id="d2d27-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="d2d27-107">這個方法可以接受檔案路徑、文字資料流程或 XML 資料流程做為輸入。</span><span class="sxs-lookup"><span data-stu-id="d2d27-107">This method can take a file path, text stream, or XML stream as input.</span></span>

<span data-ttu-id="d2d27-108">下列程式碼範例示範如何使用<xref:System.Xml.Linq.XDocument.Load%28System.String%29>方法，將文字檔中的 XML <xref:System.Xml.Linq.XDocument>填入物件。</span><span class="sxs-lookup"><span data-stu-id="d2d27-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>

[!code-vb[VbXMLSamples#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#43)]

## <a name="to-load-xml-from-a-string"></a><span data-ttu-id="d2d27-109">從字串載入 XML</span><span class="sxs-lookup"><span data-stu-id="d2d27-109">To load XML from a string</span></span>

<span data-ttu-id="d2d27-110">若要從字串填入 XML 常值<xref:System.Xml.Linq.XElement> （ <xref:System.Xml.Linq.XDocument>例如或物件`Parse` ），您可以使用方法。</span><span class="sxs-lookup"><span data-stu-id="d2d27-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>

<span data-ttu-id="d2d27-111">下列程式碼範例示範如何使用<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>方法，將字串中的 XML <xref:System.Xml.Linq.XDocument>填入物件。</span><span class="sxs-lookup"><span data-stu-id="d2d27-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>

[!code-vb[VbXMLSamples#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#47)]

## <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="d2d27-112">從資料流程載入 XML</span><span class="sxs-lookup"><span data-stu-id="d2d27-112">To load XML from a stream</span></span>

<span data-ttu-id="d2d27-113">若要從資料流程填入 XML 常值<xref:System.Xml.Linq.XElement> （ <xref:System.Xml.Linq.XDocument>例如或物件`Load` ），您可以<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>使用方法或方法。</span><span class="sxs-lookup"><span data-stu-id="d2d27-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d2d27-114">下列程式碼範例示範如何使用<xref:System.Xml.Linq.XNode.ReadFrom%2A>方法，以 xml 資料流程的 xml <xref:System.Xml.Linq.XDocument>填入物件。</span><span class="sxs-lookup"><span data-stu-id="d2d27-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>

[!code-vb[VbXMLSamples#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples15.vb#46)]

## <a name="see-also"></a><span data-ttu-id="d2d27-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2d27-115">See also</span></span>

- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d2d27-116">XML 常值</span><span class="sxs-lookup"><span data-stu-id="d2d27-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="d2d27-117">XML</span><span class="sxs-lookup"><span data-stu-id="d2d27-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="d2d27-118">在 Visual Basic 中管理 XML</span><span class="sxs-lookup"><span data-stu-id="d2d27-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
