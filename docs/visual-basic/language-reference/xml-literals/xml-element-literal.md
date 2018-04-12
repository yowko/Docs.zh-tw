---
title: XML 項目常值 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de5825a6af1dd1b93c3c85651125cf817dc564f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="93972-102">XML 項目常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93972-102">XML Element Literal (Visual Basic)</span></span>

<span data-ttu-id="93972-103">常值，表示<xref:System.Xml.Linq.XElement>物件。</span><span class="sxs-lookup"><span data-stu-id="93972-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93972-104">語法</span><span class="sxs-lookup"><span data-stu-id="93972-104">Syntax</span></span>  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="93972-105">組件</span><span class="sxs-lookup"><span data-stu-id="93972-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="93972-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="93972-106">Required.</span></span> <span data-ttu-id="93972-107">開啟 開始項目標記。</span><span class="sxs-lookup"><span data-stu-id="93972-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="93972-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="93972-108">Required.</span></span> <span data-ttu-id="93972-109">元素名稱。</span><span class="sxs-lookup"><span data-stu-id="93972-109">Name of the element.</span></span> <span data-ttu-id="93972-110">格式為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="93972-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="93972-111">常值文字的項目名稱，表單`[ePrefix:]eName`，其中：</span><span class="sxs-lookup"><span data-stu-id="93972-111">Literal text for the element name, of the form `[ePrefix:]eName`, where:</span></span>  
  
        |<span data-ttu-id="93972-112">組件</span><span class="sxs-lookup"><span data-stu-id="93972-112">Part</span></span>|<span data-ttu-id="93972-113">說明</span><span class="sxs-lookup"><span data-stu-id="93972-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="93972-114">選擇項。</span><span class="sxs-lookup"><span data-stu-id="93972-114">Optional.</span></span> <span data-ttu-id="93972-115">XML 命名空間前置詞的項目。</span><span class="sxs-lookup"><span data-stu-id="93972-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="93972-116">必須是全域的 XML 命名空間定義與`Imports`檔案中，或在專案層級或本機的 XML 命名空間中這個項目或父項目所定義的陳述式。</span><span class="sxs-lookup"><span data-stu-id="93972-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="93972-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="93972-117">Required.</span></span> <span data-ttu-id="93972-118">元素名稱。</span><span class="sxs-lookup"><span data-stu-id="93972-118">Name of the element.</span></span> <span data-ttu-id="93972-119">格式為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="93972-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="93972-120">-常值文字。</span><span class="sxs-lookup"><span data-stu-id="93972-120">-   Literal text.</span></span> <span data-ttu-id="93972-121">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="93972-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="93972-122">內嵌運算式的形式`<%= eNameExp %>`。</span><span class="sxs-lookup"><span data-stu-id="93972-122">-   Embedded expression of the form `<%= eNameExp %>`.</span></span> <span data-ttu-id="93972-123">型別`eNameExp`必須`String`或隱含轉換為型別<xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="93972-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="93972-124">內嵌運算式的形式`<%= nameExp %>`。</span><span class="sxs-lookup"><span data-stu-id="93972-124">Embedded expression of the form `<%= nameExp %>`.</span></span> <span data-ttu-id="93972-125">型別`nameExp`必須`String`或隱含地轉換成類型<xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="93972-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="93972-126">項目的結尾標記中不允許內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="93972-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="93972-127">選擇項。</span><span class="sxs-lookup"><span data-stu-id="93972-127">Optional.</span></span> <span data-ttu-id="93972-128">常值中所宣告的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="93972-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="93972-129">每個`attribute`有一個下列語法：</span><span class="sxs-lookup"><span data-stu-id="93972-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="93972-130">屬性指派，表單`[aPrefix:]aName=aValue`，其中：</span><span class="sxs-lookup"><span data-stu-id="93972-130">Attribute assignment, of the form `[aPrefix:]aName=aValue`, where:</span></span>  
  
        |<span data-ttu-id="93972-131">組件</span><span class="sxs-lookup"><span data-stu-id="93972-131">Part</span></span>|<span data-ttu-id="93972-132">說明</span><span class="sxs-lookup"><span data-stu-id="93972-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="93972-133">選擇項。</span><span class="sxs-lookup"><span data-stu-id="93972-133">Optional.</span></span> <span data-ttu-id="93972-134">屬性的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="93972-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="93972-135">必須是全域的 XML 命名空間定義與`Imports`陳述式或區域的 XML 命名空間中這個項目或父項目所定義。</span><span class="sxs-lookup"><span data-stu-id="93972-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="93972-136">必要項。</span><span class="sxs-lookup"><span data-stu-id="93972-136">Required.</span></span> <span data-ttu-id="93972-137">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="93972-137">Name of the attribute.</span></span> <span data-ttu-id="93972-138">格式為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="93972-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="93972-139">-常值文字。</span><span class="sxs-lookup"><span data-stu-id="93972-139">-   Literal text.</span></span> <span data-ttu-id="93972-140">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="93972-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="93972-141">內嵌運算式的形式`<%= aNameExp %>`。</span><span class="sxs-lookup"><span data-stu-id="93972-141">-   Embedded expression of the form `<%= aNameExp %>`.</span></span> <span data-ttu-id="93972-142">型別`aNameExp`必須`String`或隱含轉換為型別<xref:System.Xml.Linq.XName>。</span><span class="sxs-lookup"><span data-stu-id="93972-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="93972-143">選擇項。</span><span class="sxs-lookup"><span data-stu-id="93972-143">Optional.</span></span> <span data-ttu-id="93972-144">屬性的值。</span><span class="sxs-lookup"><span data-stu-id="93972-144">Value of the attribute.</span></span> <span data-ttu-id="93972-145">格式為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="93972-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="93972-146">-常值文字，以引號括住。</span><span class="sxs-lookup"><span data-stu-id="93972-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="93972-147">內嵌運算式的形式`<%= aValueExp %>`。</span><span class="sxs-lookup"><span data-stu-id="93972-147">-   Embedded expression of the form `<%= aValueExp %>`.</span></span> <span data-ttu-id="93972-148">不允許任何類型。</span><span class="sxs-lookup"><span data-stu-id="93972-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="93972-149">內嵌運算式的形式`<%= aExp %>`。</span><span class="sxs-lookup"><span data-stu-id="93972-149">Embedded expression of the form `<%= aExp %>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="93972-150">選擇項。</span><span class="sxs-lookup"><span data-stu-id="93972-150">Optional.</span></span> <span data-ttu-id="93972-151">表示項目是空的項目，不含內容。</span><span class="sxs-lookup"><span data-stu-id="93972-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="93972-152">必要項。</span><span class="sxs-lookup"><span data-stu-id="93972-152">Required.</span></span> <span data-ttu-id="93972-153">結束起始或空白項目標記。</span><span class="sxs-lookup"><span data-stu-id="93972-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="93972-154">選擇項。</span><span class="sxs-lookup"><span data-stu-id="93972-154">Optional.</span></span> <span data-ttu-id="93972-155">項目的內容。</span><span class="sxs-lookup"><span data-stu-id="93972-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="93972-156">每個`content`可以是下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="93972-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="93972-157">常值文字。</span><span class="sxs-lookup"><span data-stu-id="93972-157">Literal text.</span></span> <span data-ttu-id="93972-158">中的所有空白字元`elementContents`太高，如果沒有任何常值文字。</span><span class="sxs-lookup"><span data-stu-id="93972-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="93972-159">內嵌運算式的形式`<%= contentExp %>`。</span><span class="sxs-lookup"><span data-stu-id="93972-159">Embedded expression of the form `<%= contentExp %>`.</span></span>  
  
    -   <span data-ttu-id="93972-160">XML 元素常值。</span><span class="sxs-lookup"><span data-stu-id="93972-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="93972-161">XML 註解常值。</span><span class="sxs-lookup"><span data-stu-id="93972-161">XML comment literal.</span></span> <span data-ttu-id="93972-162">請參閱[XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="93972-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="93972-163">XML 處理指示常值。</span><span class="sxs-lookup"><span data-stu-id="93972-163">XML processing instruction literal.</span></span> <span data-ttu-id="93972-164">請參閱[XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="93972-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="93972-165">XML CDATA 常值。</span><span class="sxs-lookup"><span data-stu-id="93972-165">XML CDATA literal.</span></span> <span data-ttu-id="93972-166">請參閱[XML CDATA 常值](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="93972-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   `</[name]>`  
  
     <span data-ttu-id="93972-167">選擇項。</span><span class="sxs-lookup"><span data-stu-id="93972-167">Optional.</span></span> <span data-ttu-id="93972-168">代表項目的結尾標記。</span><span class="sxs-lookup"><span data-stu-id="93972-168">Represents the closing tag for the element.</span></span> <span data-ttu-id="93972-169">選擇性`name`內嵌運算式的結果時，不允許參數。</span><span class="sxs-lookup"><span data-stu-id="93972-169">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93972-170">傳回值</span><span class="sxs-lookup"><span data-stu-id="93972-170">Return Value</span></span>  
 <span data-ttu-id="93972-171"><xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="93972-171">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93972-172">備註</span><span class="sxs-lookup"><span data-stu-id="93972-172">Remarks</span></span>  
 <span data-ttu-id="93972-173">您可以使用 XML 元素常值的語法來建立<xref:System.Xml.Linq.XElement>您的程式碼中的物件。</span><span class="sxs-lookup"><span data-stu-id="93972-173">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93972-174">XML 常值可以跨越多行，而不使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="93972-174">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="93972-175">這項功能可讓您從 XML 文件內容複製並貼上直接將[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="93972-175">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="93972-176">內嵌運算式的形式`<%= exp %>`可讓您將動態資訊加入至 XML 元素常值。</span><span class="sxs-lookup"><span data-stu-id="93972-176">Embedded expressions of the form `<%= exp %>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="93972-177">如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="93972-177">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="93972-178">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器會將 XML 元素常值轉換成呼叫<xref:System.Xml.Linq.XElement.%23ctor%2A>建構函式，而且如果它是必要項，<xref:System.Xml.Linq.XAttribute.%23ctor%2A>建構函式。</span><span class="sxs-lookup"><span data-stu-id="93972-178">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="93972-179">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="93972-179">XML Namespaces</span></span>  
 <span data-ttu-id="93972-180">當您必須建立 XML 常值的項目和程式碼中多次相同的命名空間，XML 命名空間前置詞很有用。</span><span class="sxs-lookup"><span data-stu-id="93972-180">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="93972-181">您可以使用全域 XML 命名空間前置詞，您定義使用`Imports`陳述式或使用您定義的本機前置詞`xmlns:xmlPrefix="xmlNamespace"`屬性語法。</span><span class="sxs-lookup"><span data-stu-id="93972-181">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:xmlPrefix="xmlNamespace"` attribute syntax.</span></span> <span data-ttu-id="93972-182">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="93972-182">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="93972-183">XML 命名空間之範圍規則，根據本機的前置詞的優先順序高於通用的前置詞。</span><span class="sxs-lookup"><span data-stu-id="93972-183">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="93972-184">不過，如果 XML 常值定義的 XML 命名空間，該命名空間不適用於內嵌的運算式中出現的運算式。</span><span class="sxs-lookup"><span data-stu-id="93972-184">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="93972-185">內嵌的運算式可以存取只有的全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="93972-185">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="93972-186">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器會將轉換成產生的程式碼中的一個區域命名空間定義使用 XML 常值每個全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="93972-186">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="93972-187">未使用的全域 XML 命名空間不會出現在產生的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="93972-187">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93972-188">範例</span><span class="sxs-lookup"><span data-stu-id="93972-188">Example</span></span>  
 <span data-ttu-id="93972-189">下列範例會示範如何建立簡單的 XML 項目具有兩個巢狀的空項目。</span><span class="sxs-lookup"><span data-stu-id="93972-189">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 <span data-ttu-id="93972-190">此範例會顯示下列文字。</span><span class="sxs-lookup"><span data-stu-id="93972-190">The example displays the following text.</span></span> <span data-ttu-id="93972-191">請注意，常值保留空白元素的結構。</span><span class="sxs-lookup"><span data-stu-id="93972-191">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="93972-192">範例</span><span class="sxs-lookup"><span data-stu-id="93972-192">Example</span></span>  
 <span data-ttu-id="93972-193">下列範例會示範如何使用內嵌的運算式來命名項目和建立屬性。</span><span class="sxs-lookup"><span data-stu-id="93972-193">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 <span data-ttu-id="93972-194">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="93972-194">This code displays the following text:</span></span>  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="93972-195">範例</span><span class="sxs-lookup"><span data-stu-id="93972-195">Example</span></span>  
 <span data-ttu-id="93972-196">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="93972-196">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="93972-197">然後建立 XML 常值中使用的命名空間前置詞，並顯示項目的最終格式。</span><span class="sxs-lookup"><span data-stu-id="93972-197">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 <span data-ttu-id="93972-198">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="93972-198">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="93972-199">請注意編譯器，轉換成 XML 命名空間的前置詞定義的全域 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="93972-199">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="93972-200">\<Ns:middle > 項目會重新定義的 XML 命名空間前置詞\<ns:inner1 > 項目。</span><span class="sxs-lookup"><span data-stu-id="93972-200">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="93972-201">不過， \<ns:inner2 > 元素會使用所定義的命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="93972-201">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93972-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93972-202">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="93972-203">宣告的 XML 項目和屬性的名稱</span><span class="sxs-lookup"><span data-stu-id="93972-203">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [<span data-ttu-id="93972-204">XML 註解常值</span><span class="sxs-lookup"><span data-stu-id="93972-204">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [<span data-ttu-id="93972-205">XML CDATA 常值</span><span class="sxs-lookup"><span data-stu-id="93972-205">XML CDATA Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [<span data-ttu-id="93972-206">XML 常值</span><span class="sxs-lookup"><span data-stu-id="93972-206">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="93972-207">在 Visual Basic 中建立 XML</span><span class="sxs-lookup"><span data-stu-id="93972-207">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="93972-208">XML 中內嵌的運算式</span><span class="sxs-lookup"><span data-stu-id="93972-208">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="93972-209">Imports 陳述式 (XML 命名空間)</span><span class="sxs-lookup"><span data-stu-id="93972-209">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
