---
title: GetXmlNamespace 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 660474c1193076755889fd885c1b78bec78f0a2c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873471"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="cb146-102">GetXmlNamespace 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb146-102">GetXmlNamespace Operator (Visual Basic)</span></span>

<span data-ttu-id="cb146-103">取得 <xref:System.Xml.Linq.XNamespace> 對應到指定 XML 命名空間前置詞的物件。</span><span class="sxs-lookup"><span data-stu-id="cb146-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb146-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb146-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="cb146-105">組件</span><span class="sxs-lookup"><span data-stu-id="cb146-105">Parts</span></span>  

 `xmlNamespacePrefix`  
 <span data-ttu-id="cb146-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="cb146-106">Optional.</span></span> <span data-ttu-id="cb146-107">識別 XML 命名空間前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="cb146-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="cb146-108">如果有提供，此字串必須是有效的 XML 識別碼。</span><span class="sxs-lookup"><span data-stu-id="cb146-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="cb146-109">如需詳細資訊，請參閱宣告 [的 XML 元素和屬性的名稱](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="cb146-109">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="cb146-110">如果未指定前置詞，則會傳回預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="cb146-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="cb146-111">如果未指定預設命名空間，則會傳回空的命名空間。</span><span class="sxs-lookup"><span data-stu-id="cb146-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb146-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="cb146-112">Return Value</span></span>  

 <span data-ttu-id="cb146-113"><xref:System.Xml.Linq.XNamespace>對應至 XML 命名空間前置詞的物件。</span><span class="sxs-lookup"><span data-stu-id="cb146-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb146-114">備註</span><span class="sxs-lookup"><span data-stu-id="cb146-114">Remarks</span></span>  

 <span data-ttu-id="cb146-115">`GetXmlNamespace`運算子 <xref:System.Xml.Linq.XNamespace> 會取得對應至 XML 命名空間前置詞的物件 `xmlNamespacePrefix` 。</span><span class="sxs-lookup"><span data-stu-id="cb146-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="cb146-116">您可以直接在 XML 常值和 XML 軸屬性中使用 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="cb146-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="cb146-117">不過，您必須使用 `GetXmlNamespace` 運算子將命名空間前置詞轉換成 <xref:System.Xml.Linq.XNamespace> 物件，才能在程式碼中使用它。</span><span class="sxs-lookup"><span data-stu-id="cb146-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="cb146-118">您可以將不合格的元素名稱附加至 <xref:System.Xml.Linq.XNamespace> 物件，以取得 <xref:System.Xml.Linq.XName> 許多方法需要的完整物件 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cb146-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb146-119">範例</span><span class="sxs-lookup"><span data-stu-id="cb146-119">Example</span></span>  

 <span data-ttu-id="cb146-120">下列範例會匯入 `ns` 為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="cb146-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="cb146-121">然後，它會使用命名空間的前置詞來建立 XML 常值，並存取具有限定名稱的第一個子節點 `ns:phone` 。</span><span class="sxs-lookup"><span data-stu-id="cb146-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="cb146-122">然後，它會將該子節點傳遞至 `ShowName` 副程式，以使用運算子來建立限定名稱 `GetXmlNamespace` 。</span><span class="sxs-lookup"><span data-stu-id="cb146-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="cb146-123">然後，副程式會將 `ShowName` 限定名稱傳遞給 <xref:System.Xml.Linq.XNode.Ancestors%2A> 方法，以取得父 `ns:contact` 節點。</span><span class="sxs-lookup"><span data-stu-id="cb146-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="cb146-124">當您呼叫時 `TestGetXmlNamespace.RunSample()` ，它會顯示訊息方塊，其中包含下列文字：</span><span class="sxs-lookup"><span data-stu-id="cb146-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="cb146-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb146-125">See also</span></span>

- [<span data-ttu-id="cb146-126">Imports 陳述式 (XML 命名空間)</span><span class="sxs-lookup"><span data-stu-id="cb146-126">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="cb146-127">在 Visual Basic 中存取 XML</span><span class="sxs-lookup"><span data-stu-id="cb146-127">Accessing XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/accessing-xml.md)
