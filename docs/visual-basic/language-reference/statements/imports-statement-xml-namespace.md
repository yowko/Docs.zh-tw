---
title: Imports 語句-XML 命名空間
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 52864e4d1c8183b6243025e72368d23627049c84
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351055"
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="39d96-102">Imports 陳述式 (XML 命名空間)</span><span class="sxs-lookup"><span data-stu-id="39d96-102">Imports Statement (XML Namespace)</span></span>

<span data-ttu-id="39d96-103">匯入 XML 常值和 XML 軸屬性中所使用的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="39d96-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>

## <a name="syntax"></a><span data-ttu-id="39d96-104">語法</span><span class="sxs-lookup"><span data-stu-id="39d96-104">Syntax</span></span>

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a><span data-ttu-id="39d96-105">組件</span><span class="sxs-lookup"><span data-stu-id="39d96-105">Parts</span></span>

`xmlNamespacePrefix`  
<span data-ttu-id="39d96-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="39d96-106">Optional.</span></span> <span data-ttu-id="39d96-107">XML 元素和屬性可以參考 `xmlNamespaceName`的字串。</span><span class="sxs-lookup"><span data-stu-id="39d96-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="39d96-108">如果未提供任何 `xmlNamespacePrefix`，則匯入的 XML 命名空間是預設的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="39d96-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="39d96-109">必須是有效的 XML 識別碼。</span><span class="sxs-lookup"><span data-stu-id="39d96-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="39d96-110">如需詳細資訊，請參閱宣告[的 XML 元素和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="39d96-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>

`xmlNamespaceName`  
<span data-ttu-id="39d96-111">必要。</span><span class="sxs-lookup"><span data-stu-id="39d96-111">Required.</span></span> <span data-ttu-id="39d96-112">識別正在匯入之 XML 命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="39d96-112">The string identifying the XML namespace being imported.</span></span>

## <a name="remarks"></a><span data-ttu-id="39d96-113">備註</span><span class="sxs-lookup"><span data-stu-id="39d96-113">Remarks</span></span>

<span data-ttu-id="39d96-114">您可以使用 `Imports` 語句來定義可用於 XML 常值和 XML 軸屬性的全域 XML 命名空間，或做為傳遞給 `GetXmlNamespace` 運算子的參數。</span><span class="sxs-lookup"><span data-stu-id="39d96-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="39d96-115">（如需有關使用 `Imports` 語句匯入可在程式碼中使用類型名稱之別名的詳細資訊，請參閱[Imports 語句（.Net 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)。使用 `Imports` 語句來宣告 XML 命名空間的語法，與 XML 中使用的語法相同。</span><span class="sxs-lookup"><span data-stu-id="39d96-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="39d96-116">因此，您可以從 XML 檔案複製命名空間宣告，並在 `Imports` 語句中使用它。</span><span class="sxs-lookup"><span data-stu-id="39d96-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>

<span data-ttu-id="39d96-117">當您想要重複建立來自相同命名空間的 XML 元素時，XML 命名空間前置詞非常有用。</span><span class="sxs-lookup"><span data-stu-id="39d96-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="39d96-118">以 `Imports` 語句宣告的 XML 命名空間前置詞，在檔案中的所有程式碼都可供使用時，是全域的。</span><span class="sxs-lookup"><span data-stu-id="39d96-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="39d96-119">當您建立 XML 專案常值時，以及當您存取 XML 軸屬性時，可以使用它。</span><span class="sxs-lookup"><span data-stu-id="39d96-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="39d96-120">如需詳細資訊，請參閱[Xml 元素常](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)值和[xml 軸屬性](../../../visual-basic/language-reference/xml-axis/index.md)。</span><span class="sxs-lookup"><span data-stu-id="39d96-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/index.md).</span></span>

<span data-ttu-id="39d96-121">如果您定義不含命名空間前置詞的全域 XML 命名空間（例如 `Imports <xmlns="http://SomeNameSpace>"`），該命名空間會被視為預設的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="39d96-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="39d96-122">預設的 XML 命名空間會用於未明確指定命名空間的任何 XML 專案常值或 XML 屬性軸屬性。</span><span class="sxs-lookup"><span data-stu-id="39d96-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="39d96-123">如果指定的命名空間是空的命名空間（也就是 `xmlns=""`），也會使用預設的命名空間。</span><span class="sxs-lookup"><span data-stu-id="39d96-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="39d96-124">預設的 XML 命名空間不適用於 XML 常值中的 XML 屬性，或是沒有命名空間的 XML 屬性軸屬性。</span><span class="sxs-lookup"><span data-stu-id="39d96-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>

<span data-ttu-id="39d96-125">Xml 常值中定義的 XML 命名空間（稱為*本機 XML 命名空間*）優先于 `Imports` 語句定義為全域的 xml 命名空間。</span><span class="sxs-lookup"><span data-stu-id="39d96-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="39d96-126">`Imports` 語句所定義的 XML 命名空間會優先于針對 Visual Basic 專案匯入的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="39d96-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="39d96-127">如果 XML 常值定義 XML 命名空間，該本機命名空間就不會套用至內嵌運算式。</span><span class="sxs-lookup"><span data-stu-id="39d96-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>

<span data-ttu-id="39d96-128">全域 XML 命名空間會遵循與 .NET Framework 命名空間相同的範圍和定義規則。</span><span class="sxs-lookup"><span data-stu-id="39d96-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="39d96-129">因此，您可以在任何可匯入 .NET Framework 命名空間的位置加入 `Imports` 語句，以定義全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="39d96-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="39d96-130">這包括程式碼檔案和專案層級的匯入命名空間。</span><span class="sxs-lookup"><span data-stu-id="39d96-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="39d96-131">如需專案層級匯入之命名空間的詳細資訊，請參閱[專案設計工具、參考頁（Visual Basic）](/visualstudio/ide/reference/references-page-project-designer-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="39d96-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="39d96-132">每個來源檔案都可以包含任意數目的 `Imports` 語句。</span><span class="sxs-lookup"><span data-stu-id="39d96-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="39d96-133">這些必須遵循 option 宣告（例如 `Option Strict` 語句），而且必須在程式設計專案宣告之前，例如 `Module` 或 `Class` 語句。</span><span class="sxs-lookup"><span data-stu-id="39d96-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>

## <a name="example"></a><span data-ttu-id="39d96-134">範例</span><span class="sxs-lookup"><span data-stu-id="39d96-134">Example</span></span>

<span data-ttu-id="39d96-135">下列範例會匯入預設的 XML 命名空間和以前置詞 `ns`識別的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="39d96-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="39d96-136">然後，它會建立同時使用這兩個命名空間的 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="39d96-136">It then creates XML literals that use both namespaces.</span></span>

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

<span data-ttu-id="39d96-137">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="39d96-137">This code displays the following text:</span></span>

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a><span data-ttu-id="39d96-138">範例</span><span class="sxs-lookup"><span data-stu-id="39d96-138">Example</span></span>

<span data-ttu-id="39d96-139">下列範例會將 XML 命名空間前置詞彙入 `ns`。</span><span class="sxs-lookup"><span data-stu-id="39d96-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="39d96-140">然後，它會建立使用命名空間前置詞的 XML 常值，並顯示專案的最終格式。</span><span class="sxs-lookup"><span data-stu-id="39d96-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

<span data-ttu-id="39d96-141">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="39d96-141">This code displays the following text:</span></span>

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

<span data-ttu-id="39d96-142">請注意，編譯器會將 XML 命名空間前置詞從全域前置詞轉換成本機前置詞定義。</span><span class="sxs-lookup"><span data-stu-id="39d96-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>

## <a name="example"></a><span data-ttu-id="39d96-143">範例</span><span class="sxs-lookup"><span data-stu-id="39d96-143">Example</span></span>

<span data-ttu-id="39d96-144">下列範例會將 XML 命名空間前置詞彙入 `ns`。</span><span class="sxs-lookup"><span data-stu-id="39d96-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="39d96-145">然後它會使用命名空間的前置詞來建立 XML 常值，以及存取完整名稱為 `ns:name` 的第一個子節點。</span><span class="sxs-lookup"><span data-stu-id="39d96-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

<span data-ttu-id="39d96-146">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="39d96-146">This code displays the following text:</span></span>

`Patrick Hines`

## <a name="see-also"></a><span data-ttu-id="39d96-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="39d96-147">See also</span></span>

- [<span data-ttu-id="39d96-148">XML 項目常值</span><span class="sxs-lookup"><span data-stu-id="39d96-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="39d96-149">XML 軸屬性</span><span class="sxs-lookup"><span data-stu-id="39d96-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="39d96-150">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="39d96-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [<span data-ttu-id="39d96-151">GetXmlNamespace 運算子</span><span class="sxs-lookup"><span data-stu-id="39d96-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
