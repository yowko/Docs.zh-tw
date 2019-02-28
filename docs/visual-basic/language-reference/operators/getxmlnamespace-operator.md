---
title: GetXmlNamespace 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: e02a7c5c9859352aa07bfaa741b80b7fd18d1da4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979901"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="7fcb2-102">GetXmlNamespace 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fcb2-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="7fcb2-103">取得<xref:System.Xml.Linq.XNamespace>對應至指定的 XML 命名空間前置詞的物件。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fcb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="7fcb2-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="7fcb2-105">組件</span><span class="sxs-lookup"><span data-stu-id="7fcb2-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="7fcb2-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-106">Optional.</span></span> <span data-ttu-id="7fcb2-107">識別 XML 命名空間前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="7fcb2-108">如果提供，這個字串必須是有效的 XML 識別項。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="7fcb2-109">如需詳細資訊，請參閱 <<c0> [ 名稱的宣告 XML 元素和屬性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="7fcb2-110">如果未不指定任何前置詞，則會傳回預設的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="7fcb2-111">如果未不指定任何預設命名空間，則會傳回空的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fcb2-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="7fcb2-112">Return Value</span></span>  
 <span data-ttu-id="7fcb2-113"><xref:System.Xml.Linq.XNamespace> XML 命名空間前置詞對應的物件。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fcb2-114">備註</span><span class="sxs-lookup"><span data-stu-id="7fcb2-114">Remarks</span></span>  
 <span data-ttu-id="7fcb2-115">`GetXmlNamespace`運算子取得<xref:System.Xml.Linq.XNamespace>物件，對應至 XML 命名空間前置詞`xmlNamespacePrefix`。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="7fcb2-116">您可以使用 XML 命名空間前置詞，直接在 XML 常值和 XML 軸屬性。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="7fcb2-117">不過，您必須使用`GetXmlNamespace`運算子，將轉換的命名空間前置詞<xref:System.Xml.Linq.XNamespace>物件，才能用於您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="7fcb2-118">您可以將附加至未限定的項目名稱<xref:System.Xml.Linq.XNamespace>以取得完整限定的物件<xref:System.Xml.Linq.XName>物件，哪一個多[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]方法都需要。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fcb2-119">範例</span><span class="sxs-lookup"><span data-stu-id="7fcb2-119">Example</span></span>  
 <span data-ttu-id="7fcb2-120">下列範例會匯入`ns`作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="7fcb2-121">然後它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定的名稱的第一個子節點`ns:phone`。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="7fcb2-122">接著，將該子節點`ShowName`藉由建構限定的名稱的副程式`GetXmlNamespace`運算子。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="7fcb2-123">`ShowName`副程式接著會將傳遞的限定的名稱<xref:System.Xml.Linq.XNode.Ancestors%2A>方法來取得父代`ns:contact`節點。</span><span class="sxs-lookup"><span data-stu-id="7fcb2-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="7fcb2-124">當您呼叫`TestGetXmlNamespace.RunSample()`，它會顯示訊息方塊包含下列文字：</span><span class="sxs-lookup"><span data-stu-id="7fcb2-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="7fcb2-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7fcb2-125">See also</span></span>
- [<span data-ttu-id="7fcb2-126">Imports 陳述式 (XML 命名空間)</span><span class="sxs-lookup"><span data-stu-id="7fcb2-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="7fcb2-127">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="7fcb2-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
