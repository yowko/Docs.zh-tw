---
title: "XML 項目常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
dev_langs:
- VB
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d5cf769a1e3f668652d1eb4551058deba38a8acf
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="c4afc-102">XML 項目常值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4afc-102">XML Element Literal (Visual Basic)</span></span>
<span data-ttu-id="c4afc-103">常值，表示<xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c4afc-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4afc-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4afc-104">Syntax</span></span>  
  
```  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="c4afc-105">組件</span><span class="sxs-lookup"><span data-stu-id="c4afc-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="c4afc-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-106">Required.</span></span> <span data-ttu-id="c4afc-107">開啟起始項目標記。</span><span class="sxs-lookup"><span data-stu-id="c4afc-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="c4afc-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-108">Required.</span></span> <span data-ttu-id="c4afc-109">元素名稱。</span><span class="sxs-lookup"><span data-stu-id="c4afc-109">Name of the element.</span></span> <span data-ttu-id="c4afc-110">格式為下列其中一項︰</span><span class="sxs-lookup"><span data-stu-id="c4afc-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="c4afc-111">常值文字的項目名稱，表單的 [`ePrefix``:`]`eName`，其中︰</span><span class="sxs-lookup"><span data-stu-id="c4afc-111">Literal text for the element name, of the form [`ePrefix``:`]`eName`, where:</span></span>  
  
        |<span data-ttu-id="c4afc-112">組件</span><span class="sxs-lookup"><span data-stu-id="c4afc-112">Part</span></span>|<span data-ttu-id="c4afc-113">說明</span><span class="sxs-lookup"><span data-stu-id="c4afc-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="c4afc-114">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-114">Optional.</span></span> <span data-ttu-id="c4afc-115">項目的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="c4afc-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="c4afc-116">必須是全域的 XML 命名空間定義的`Imports`陳述式在檔案或專案層級中，或本機的 XML 命名空間定義於這個項目或父項目。</span><span class="sxs-lookup"><span data-stu-id="c4afc-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="c4afc-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-117">Required.</span></span> <span data-ttu-id="c4afc-118">元素名稱。</span><span class="sxs-lookup"><span data-stu-id="c4afc-118">Name of the element.</span></span> <span data-ttu-id="c4afc-119">格式為下列其中一項︰</span><span class="sxs-lookup"><span data-stu-id="c4afc-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="c4afc-120">-常值文字。</span><span class="sxs-lookup"><span data-stu-id="c4afc-120">-   Literal text.</span></span> <span data-ttu-id="c4afc-121">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="c4afc-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="c4afc-122">內嵌運算式格式`<%=`e`NameExp` `%>`。</span><span class="sxs-lookup"><span data-stu-id="c4afc-122">-   Embedded expression of the form `<%=` e`NameExp` `%>`.</span></span> <span data-ttu-id="c4afc-123">型別`eNameExp`必須`String`或可隱含轉換至<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>型別</span><span class="sxs-lookup"><span data-stu-id="c4afc-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="c4afc-124">內嵌運算式格式`<%=` `nameExp` `%>`。</span><span class="sxs-lookup"><span data-stu-id="c4afc-124">Embedded expression of the form `<%=` `nameExp` `%>`.</span></span> <span data-ttu-id="c4afc-125">型別`nameExp`必須`String`或隱含地轉換成<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>類型</span><span class="sxs-lookup"><span data-stu-id="c4afc-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="c4afc-126">項目的結尾標記中不允許內嵌的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4afc-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="c4afc-127">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-127">Optional.</span></span> <span data-ttu-id="c4afc-128">常值中宣告之屬性清單。</span><span class="sxs-lookup"><span data-stu-id="c4afc-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="c4afc-129">每個`attribute`有下列語法︰</span><span class="sxs-lookup"><span data-stu-id="c4afc-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="c4afc-130">屬性指派，表單的 [`aPrefix``:`]`aName``=``aValue`，其中︰</span><span class="sxs-lookup"><span data-stu-id="c4afc-130">Attribute assignment, of the form [`aPrefix``:`]`aName``=``aValue`, where:</span></span>  
  
        |<span data-ttu-id="c4afc-131">組件</span><span class="sxs-lookup"><span data-stu-id="c4afc-131">Part</span></span>|<span data-ttu-id="c4afc-132">說明</span><span class="sxs-lookup"><span data-stu-id="c4afc-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="c4afc-133">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-133">Optional.</span></span> <span data-ttu-id="c4afc-134">屬性的 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="c4afc-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="c4afc-135">必須是全域的 XML 命名空間定義的`Imports`陳述式或區域的 XML 命名空間定義於這個項目或父項目。</span><span class="sxs-lookup"><span data-stu-id="c4afc-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="c4afc-136">必要項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-136">Required.</span></span> <span data-ttu-id="c4afc-137">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="c4afc-137">Name of the attribute.</span></span> <span data-ttu-id="c4afc-138">格式為下列其中一項︰</span><span class="sxs-lookup"><span data-stu-id="c4afc-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="c4afc-139">-常值文字。</span><span class="sxs-lookup"><span data-stu-id="c4afc-139">-   Literal text.</span></span> <span data-ttu-id="c4afc-140">請參閱[宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="c4afc-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="c4afc-141">內嵌運算式格式`<%=` `aNameExp` `%>`。</span><span class="sxs-lookup"><span data-stu-id="c4afc-141">-   Embedded expression of the form `<%=` `aNameExp` `%>`.</span></span> <span data-ttu-id="c4afc-142">型別`aNameExp`必須`String`或可隱含轉換至<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>型別</span><span class="sxs-lookup"><span data-stu-id="c4afc-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="c4afc-143">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-143">Optional.</span></span> <span data-ttu-id="c4afc-144">屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c4afc-144">Value of the attribute.</span></span> <span data-ttu-id="c4afc-145">格式為下列其中一項︰</span><span class="sxs-lookup"><span data-stu-id="c4afc-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="c4afc-146">-常值文字，以引號括住。</span><span class="sxs-lookup"><span data-stu-id="c4afc-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="c4afc-147">內嵌運算式格式`<%=` `aValueExp` `%>`。</span><span class="sxs-lookup"><span data-stu-id="c4afc-147">-   Embedded expression of the form `<%=` `aValueExp` `%>`.</span></span> <span data-ttu-id="c4afc-148">允許任何型別。</span><span class="sxs-lookup"><span data-stu-id="c4afc-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="c4afc-149">內嵌運算式格式`<%=` `aExp` `%>`。</span><span class="sxs-lookup"><span data-stu-id="c4afc-149">Embedded expression of the form `<%=` `aExp` `%>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="c4afc-150">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-150">Optional.</span></span> <span data-ttu-id="c4afc-151">表示的項目是空的項目，不含內容。</span><span class="sxs-lookup"><span data-stu-id="c4afc-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="c4afc-152">必要項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-152">Required.</span></span> <span data-ttu-id="c4afc-153">結束開始或空白項目標記。</span><span class="sxs-lookup"><span data-stu-id="c4afc-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="c4afc-154">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-154">Optional.</span></span> <span data-ttu-id="c4afc-155">項目的內容。</span><span class="sxs-lookup"><span data-stu-id="c4afc-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="c4afc-156">每個`content`可以是下列其中之一︰</span><span class="sxs-lookup"><span data-stu-id="c4afc-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="c4afc-157">常值文字。</span><span class="sxs-lookup"><span data-stu-id="c4afc-157">Literal text.</span></span> <span data-ttu-id="c4afc-158">中的所有泛空白字元`elementContents`太高，如果沒有任何常值文字。</span><span class="sxs-lookup"><span data-stu-id="c4afc-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="c4afc-159">內嵌運算式格式`<%=` `contentExp` `%>`。</span><span class="sxs-lookup"><span data-stu-id="c4afc-159">Embedded expression of the form `<%=` `contentExp` `%>`.</span></span>  
  
    -   <span data-ttu-id="c4afc-160">XML 項目常值。</span><span class="sxs-lookup"><span data-stu-id="c4afc-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="c4afc-161">XML 註解常值。</span><span class="sxs-lookup"><span data-stu-id="c4afc-161">XML comment literal.</span></span> <span data-ttu-id="c4afc-162">請參閱[XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="c4afc-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="c4afc-163">XML 處理指示常值。</span><span class="sxs-lookup"><span data-stu-id="c4afc-163">XML processing instruction literal.</span></span> <span data-ttu-id="c4afc-164">請參閱[XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="c4afc-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="c4afc-165">XML CDATA 常值。</span><span class="sxs-lookup"><span data-stu-id="c4afc-165">XML CDATA literal.</span></span> <span data-ttu-id="c4afc-166">請參閱[XML CDATA 常值](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)。</span><span class="sxs-lookup"><span data-stu-id="c4afc-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   <span data-ttu-id="c4afc-167">`</`[`name`]`>`</span><span class="sxs-lookup"><span data-stu-id="c4afc-167">`</`[`name`]`>`</span></span>  
  
     <span data-ttu-id="c4afc-168">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c4afc-168">Optional.</span></span> <span data-ttu-id="c4afc-169">表示項目的結尾標記。</span><span class="sxs-lookup"><span data-stu-id="c4afc-169">Represents the closing tag for the element.</span></span> <span data-ttu-id="c4afc-170">選擇性`name`參數不允許內嵌的運算式的結果時。</span><span class="sxs-lookup"><span data-stu-id="c4afc-170">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4afc-171">傳回值</span><span class="sxs-lookup"><span data-stu-id="c4afc-171">Return Value</span></span>  
 <span data-ttu-id="c4afc-172"><xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c4afc-172">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4afc-173">備註</span><span class="sxs-lookup"><span data-stu-id="c4afc-173">Remarks</span></span>  
 <span data-ttu-id="c4afc-174">您可以使用 XML 項目常值語法來建立<xref:System.Xml.Linq.XElement>您的程式碼中的物件。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c4afc-174">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4afc-175">XML 常值可以跨越多行程式碼，而不需使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="c4afc-175">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="c4afc-176">這項功能可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。</span><span class="sxs-lookup"><span data-stu-id="c4afc-176">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="c4afc-177">內嵌運算式形式的`<%=` `exp` `%>`可讓您將動態資訊加入至 XML 項目常值。</span><span class="sxs-lookup"><span data-stu-id="c4afc-177">Embedded expressions of the form `<%=` `exp` `%>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="c4afc-178">如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="c4afc-178">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="c4afc-179">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML 項目常值轉換成呼叫<xref:System.Xml.Linq.XElement.%23ctor%2A>建構函式，而且如果它是必要項目，<xref:System.Xml.Linq.XAttribute.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XAttribute.%23ctor%2A> </xref:System.Xml.Linq.XElement.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="c4afc-179">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="c4afc-180">XML 命名空間</span><span class="sxs-lookup"><span data-stu-id="c4afc-180">XML Namespaces</span></span>  
 <span data-ttu-id="c4afc-181">當您必須建立 XML 常值的項目和程式碼中多次相同的命名空間，XML 命名空間前置詞很有用。</span><span class="sxs-lookup"><span data-stu-id="c4afc-181">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="c4afc-182">您可以使用全域 XML 命名空間前置詞，以您定義使用`Imports`陳述式或使用您定義的本機首碼`xmlns:``xmlPrefix`="`xmlNamespace`"屬性語法。</span><span class="sxs-lookup"><span data-stu-id="c4afc-182">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:``xmlPrefix`="`xmlNamespace`" attribute syntax.</span></span> <span data-ttu-id="c4afc-183">如需詳細資訊，請參閱[Imports 陳述式 （XML 命名空間）](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="c4afc-183">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="c4afc-184">XML 命名空間的範圍設定規則，根據本機前置詞的優先順序高於全域首碼。</span><span class="sxs-lookup"><span data-stu-id="c4afc-184">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="c4afc-185">不過，如果 XML 常值定義的 XML 命名空間，該命名空間不適用於內嵌的運算式中出現的運算式。</span><span class="sxs-lookup"><span data-stu-id="c4afc-185">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="c4afc-186">內嵌的運算式可以存取只有通用的 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c4afc-186">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="c4afc-187">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器將會使用 XML 常值至產生的程式碼中的一個區域命名空間定義每個全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c4afc-187">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="c4afc-188">產生的程式碼中看不到未使用的全域 XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="c4afc-188">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4afc-189">範例</span><span class="sxs-lookup"><span data-stu-id="c4afc-189">Example</span></span>  
 <span data-ttu-id="c4afc-190">下列範例示範如何建立簡單的 XML 項目具有兩個巢狀的空項目。</span><span class="sxs-lookup"><span data-stu-id="c4afc-190">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 <span data-ttu-id="c4afc-191">[!code-vb[VbXMLSamples #&20;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4afc-191">[!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]</span></span>  
  
 <span data-ttu-id="c4afc-192">此範例會顯示下列文字。</span><span class="sxs-lookup"><span data-stu-id="c4afc-192">The example displays the following text.</span></span> <span data-ttu-id="c4afc-193">請注意，常值保留空白項目結構。</span><span class="sxs-lookup"><span data-stu-id="c4afc-193">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="c4afc-194">範例</span><span class="sxs-lookup"><span data-stu-id="c4afc-194">Example</span></span>  
 <span data-ttu-id="c4afc-195">下列範例示範如何使用內嵌的運算式來命名項目和建立屬性。</span><span class="sxs-lookup"><span data-stu-id="c4afc-195">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 <span data-ttu-id="c4afc-196">[!code-vb[VbXMLSamples #&21;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4afc-196">[!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]</span></span>  
  
 <span data-ttu-id="c4afc-197">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="c4afc-197">This code displays the following text:</span></span>  
  
```  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="c4afc-198">範例</span><span class="sxs-lookup"><span data-stu-id="c4afc-198">Example</span></span>  
 <span data-ttu-id="c4afc-199">下列範例會宣告 `ns` 作為 XML 命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="c4afc-199">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="c4afc-200">然後建立 XML 常值中使用的命名空間前置詞，並顯示項目的最終格式。</span><span class="sxs-lookup"><span data-stu-id="c4afc-200">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 <span data-ttu-id="c4afc-201">[!code-vb[VbXMLSamples #&22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c4afc-201">[!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]</span></span>  
  
 <span data-ttu-id="c4afc-202">此程式碼顯示下列文字：</span><span class="sxs-lookup"><span data-stu-id="c4afc-202">This code displays the following text:</span></span>  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="c4afc-203">請注意，編譯器的轉換成 XML 命名空間的前置詞定義全域 XML 命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="c4afc-203">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="c4afc-204">\<Ns:middle > 項目重新定義的 XML 命名空間前置詞\<ns:inner1 > 項目。</span><span class="sxs-lookup"><span data-stu-id="c4afc-204">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="c4afc-205">不過， \<ns:inner2 > 項目會使用所定義的命名空間`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="c4afc-205">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4afc-206">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4afc-206">See Also</span></span>  
 <span data-ttu-id="c4afc-207"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c4afc-207"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="c4afc-208"> [宣告的 XML 項目和屬性的名稱](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="c4afc-208"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span></span>  
<span data-ttu-id="c4afc-209"> [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span><span class="sxs-lookup"><span data-stu-id="c4afc-209"> [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span></span>  
<span data-ttu-id="c4afc-210"> [XML CDATA 常值](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md) </span><span class="sxs-lookup"><span data-stu-id="c4afc-210"> [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md) </span></span>  
<span data-ttu-id="c4afc-211"> [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="c4afc-211"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="c4afc-212"> [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="c4afc-212"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="c4afc-213"> [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span><span class="sxs-lookup"><span data-stu-id="c4afc-213"> [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span></span>  
<span data-ttu-id="c4afc-214"> [Imports 陳述式 (XML 命名空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="c4afc-214"> [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)</span></span>
