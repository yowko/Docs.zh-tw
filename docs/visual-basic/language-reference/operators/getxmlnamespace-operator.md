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
ms.openlocfilehash: bfccdcd9b5d35418b206dfa9fefffb5ddab69c66
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592159"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="d5d42-102">GetXmlNamespace 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5d42-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="d5d42-103">取得對應至指定 XML 命名空間前置詞的 <xref:System.Xml.Linq.XNamespace> 物件。</span><span class="sxs-lookup"><span data-stu-id="d5d42-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5d42-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5d42-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="d5d42-105">組件</span><span class="sxs-lookup"><span data-stu-id="d5d42-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="d5d42-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d5d42-106">Optional.</span></span> <span data-ttu-id="d5d42-107">識別 XML 命名空間前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="d5d42-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="d5d42-108">如果提供，此字串必須是有效的 XML 識別碼。</span><span class="sxs-lookup"><span data-stu-id="d5d42-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="d5d42-109">如需詳細資訊，請參閱宣告[的 XML 元素和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d42-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="d5d42-110">如果沒有指定前置詞，則會傳回預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="d5d42-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="d5d42-111">如果未指定預設命名空間，則會傳回空的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d5d42-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5d42-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d5d42-112">Return Value</span></span>  
 <span data-ttu-id="d5d42-113">對應至 XML 命名空間前置詞的 <xref:System.Xml.Linq.XNamespace> 物件。</span><span class="sxs-lookup"><span data-stu-id="d5d42-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5d42-114">備註</span><span class="sxs-lookup"><span data-stu-id="d5d42-114">Remarks</span></span>  
 <span data-ttu-id="d5d42-115">@No__t-0 運算子會取得對應至 XML 命名空間前置詞 `xmlNamespacePrefix` 的 <xref:System.Xml.Linq.XNamespace> 物件。</span><span class="sxs-lookup"><span data-stu-id="d5d42-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="d5d42-116">您可以直接在 XML 常值和 XML 軸屬性中使用 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="d5d42-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="d5d42-117">不過，您必須使用 `GetXmlNamespace` 運算子，將命名空間前置詞轉換成 @no__t 1 物件，然後才能在程式碼中使用它。</span><span class="sxs-lookup"><span data-stu-id="d5d42-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="d5d42-118">您可以將不合格的專案名稱附加至 @no__t 0 物件，以取得完整的 @no__t 1 物件，而這需要許多 @no__t 2 方法。</span><span class="sxs-lookup"><span data-stu-id="d5d42-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5d42-119">範例</span><span class="sxs-lookup"><span data-stu-id="d5d42-119">Example</span></span>  
 <span data-ttu-id="d5d42-120">下列範例會將 `ns` 匯入為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="d5d42-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="d5d42-121">然後，它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱 `ns:phone` 的第一個子節點。</span><span class="sxs-lookup"><span data-stu-id="d5d42-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="d5d42-122">然後，它會將該子節點傳遞給 `ShowName` 副程式，這會使用 `GetXmlNamespace` 運算子來構造限定的名稱。</span><span class="sxs-lookup"><span data-stu-id="d5d42-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="d5d42-123">@No__t-0 副程式接著會將限定名稱傳遞給 <xref:System.Xml.Linq.XNode.Ancestors%2A> 方法，以取得父 `ns:contact` 節點。</span><span class="sxs-lookup"><span data-stu-id="d5d42-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="d5d42-124">當您呼叫 `TestGetXmlNamespace.RunSample()` 時，它會顯示訊息方塊，其中包含下列文字：</span><span class="sxs-lookup"><span data-stu-id="d5d42-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="d5d42-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d42-125">See also</span></span>

- [<span data-ttu-id="d5d42-126">Imports 陳述式 (XML 命名空間)</span><span class="sxs-lookup"><span data-stu-id="d5d42-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="d5d42-127">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="d5d42-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
