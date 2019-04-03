---
title: Imports 陳述式-XML 命名空間 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 97d08113a37477add9d770b0a680c303fe7e3040
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841403"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="4fdf7-102">Imports 陳述式 (XML 命名空間)</span><span class="sxs-lookup"><span data-stu-id="4fdf7-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="4fdf7-103">匯入適用於 XML 常值和 XML 軸屬性的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fdf7-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fdf7-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="4fdf7-105">組件</span><span class="sxs-lookup"><span data-stu-id="4fdf7-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="4fdf7-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-106">Optional.</span></span> <span data-ttu-id="4fdf7-107">字串的 xml 項目和屬性可以參考`xmlNamespaceName`。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="4fdf7-108">如果沒有`xmlNamespacePrefix`是提供，匯入的 XML 命名空間是預設 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="4fdf7-109">必須是有效的 XML 識別項。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="4fdf7-110">如需詳細資訊，請參閱 <<c0> [ 名稱的宣告 XML 元素和屬性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="4fdf7-111">必要項。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-111">Required.</span></span> <span data-ttu-id="4fdf7-112">識別要匯入的 XML 命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fdf7-113">備註</span><span class="sxs-lookup"><span data-stu-id="4fdf7-113">Remarks</span></span>  
 <span data-ttu-id="4fdf7-114">您可以使用`Imports`陳述式來定義通用的 XML 命名空間，您可以使用 XML 常值和 XML 軸屬性，或做為參數傳遞至`GetXmlNamespace`運算子。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="4fdf7-115">(如需有關使用資訊`Imports`陳述式匯入別名可用型別名稱，用於您的程式碼，請參閱[Imports 陳述式 （.NET 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。)宣告 XML 命名空間所使用的語法`Imports`陳述式是用於 XML 的語法相同。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="4fdf7-116">因此，您可以從 XML 檔案複製命名空間宣告，並將它用於`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="4fdf7-117">當您想要重複建立來自相同的命名空間的 XML 項目，則 XML 命名空間前置詞會很有用。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="4fdf7-118">使用 XML 命名空間前置詞宣告`Imports`陳述式是全域的因為它可供在檔案中的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="4fdf7-119">當您建立 XML 元素常值和 XML 軸屬性的存取時，您可以使用它。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="4fdf7-120">如需詳細資訊，請參閱 < [XML 元素常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)並[XML 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>  
  
 <span data-ttu-id="4fdf7-121">如果您定義不含命名空間前置詞的全域 XML 命名空間 (例如`Imports <xmlns="http://SomeNameSpace>"`)，該命名空間會被視為預設 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="4fdf7-122">預設 XML 命名空間用於任何 XML 元素常值或未明確指定命名空間的 XML 屬性軸屬性。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="4fdf7-123">如果指定的命名空間是空的命名空間，也會使用預設命名空間 (也就是`xmlns=""`)。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="4fdf7-124">預設 XML 命名空間不適用於 XML 常值中的 XML 屬性或沒有命名空間的 XML 屬性軸屬性。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="4fdf7-125">XML 命名空間定義在 XML 常值，稱為*本機的 XML 命名空間*，所定義的 XML 命名空間中的優先順序高於`Imports`為全域的陳述式。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="4fdf7-126">所定義的 XML 命名空間`Imports`陳述式的優先順序高於針對 Visual Basic 專案匯入的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="4fdf7-127">如果 XML 常值定義 XML 命名空間，該區域的命名空間不適用於內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="4fdf7-128">通用的 XML 命名空間會遵循.NET Framework 命名空間相同的限制範圍與定義規則。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="4fdf7-129">如此一來，您可以在其中包含`Imports`陳述式來定義的全域 XML 命名空間任何位置匯入的.NET Framework 命名空間。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="4fdf7-130">這包括程式碼檔案和專案層級匯入的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="4fdf7-131">專案層級匯入的命名空間的相關資訊，請參閱[專案設計工具 (Visual Basic)、 參考頁](/visualstudio/ide/reference/references-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="4fdf7-132">每個來源檔案可以包含任意數目的`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="4fdf7-133">這些必須遵循選項的宣告，例如`Option Strict`陳述式，而且它們必須在前面程式設計項目宣告，例如`Module`或`Class`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fdf7-134">範例</span><span class="sxs-lookup"><span data-stu-id="4fdf7-134">Example</span></span>  
 <span data-ttu-id="4fdf7-135">下列範例會匯入預設 XML 命名空間和 XML 命名空間前置詞識別`ns`。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="4fdf7-136">然後，它會建立使用兩個命名空間的 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-136">It then creates XML literals that use both namespaces.</span></span>  
  
 [!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]  
  
 <span data-ttu-id="4fdf7-137">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="4fdf7-137">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="4fdf7-138">範例</span><span class="sxs-lookup"><span data-stu-id="4fdf7-138">Example</span></span>  
 <span data-ttu-id="4fdf7-139">下列範例會匯入的 XML 命名空間前置詞`ns`。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="4fdf7-140">然後，它會建立 XML 常值，會使用命名空間前置詞，並顯示項目的最終格式。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 <span data-ttu-id="4fdf7-141">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="4fdf7-141">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="4fdf7-142">請注意，編譯器轉換 XML 命名空間前置詞從全域首碼做為本機的前置詞定義。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fdf7-143">範例</span><span class="sxs-lookup"><span data-stu-id="4fdf7-143">Example</span></span>  
 <span data-ttu-id="4fdf7-144">下列範例會匯入的 XML 命名空間前置詞`ns`。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="4fdf7-145">然後它會使用命名空間的前置詞來建立 XML 常值，以及存取完整名稱為 `ns:name` 的第一個子節點。</span><span class="sxs-lookup"><span data-stu-id="4fdf7-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 <span data-ttu-id="4fdf7-146">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="4fdf7-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="4fdf7-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fdf7-147">See also</span></span>

- [<span data-ttu-id="4fdf7-148">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="4fdf7-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="4fdf7-149">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="4fdf7-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="4fdf7-150">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="4fdf7-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="4fdf7-151">GetXmlNamespace 運算子</span><span class="sxs-lookup"><span data-stu-id="4fdf7-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
