---
title: 使用 msxsl:script 的指令碼區塊
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fde6f43f-c594-486f-abcb-2211197fae20
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4d7dee9ebaed20970f715026661c29aae701289
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "45970626"
---
# <a name="script-blocks-using-msxslscript"></a><span data-ttu-id="c2351-102">使用 msxsl:script 的指令碼區塊</span><span class="sxs-lookup"><span data-stu-id="c2351-102">Script Blocks Using msxsl:script</span></span>
<span data-ttu-id="c2351-103"><xref:System.Xml.Xsl.XslCompiledTransform> 類別支援使用 `msxsl:script` 項目的內嵌指令碼。</span><span class="sxs-lookup"><span data-stu-id="c2351-103">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports embedded scripts using the `msxsl:script` element.</span></span> <span data-ttu-id="c2351-104">載入樣式表時，程式碼文件物件模型 (CodeDOM) 會將任何已定義的函式編譯成 Microsoft Intermediate Language (MSIL)，並在執行階段期間執行。</span><span class="sxs-lookup"><span data-stu-id="c2351-104">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by the Code Document Object Model (CodeDOM) and are executed during run time.</span></span> <span data-ttu-id="c2351-105">從內嵌指令碼區塊產生的組件不同於為樣式表產生的組件。</span><span class="sxs-lookup"><span data-stu-id="c2351-105">The assembly generated from the embedded script block is separate than the assembly generated for the style sheet.</span></span>  
  
## <a name="enable-xslt-script"></a><span data-ttu-id="c2351-106">啟用 XSLT 指令碼</span><span class="sxs-lookup"><span data-stu-id="c2351-106">Enable XSLT Script</span></span>  
 <span data-ttu-id="c2351-107">內嵌指令碼支援是 <xref:System.Xml.Xsl.XslCompiledTransform> 類別上的選擇性 XSLT 設定。</span><span class="sxs-lookup"><span data-stu-id="c2351-107">Support for embedded scripts is an optional XSLT setting on the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="c2351-108">預設會停用指令碼支援。</span><span class="sxs-lookup"><span data-stu-id="c2351-108">Script support is disabled by default.</span></span> <span data-ttu-id="c2351-109">若要啟用指令碼支援，請建立 <xref:System.Xml.Xsl.XsltSettings> 物件 (將 <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> 屬性設為 `true`)，並將該物件傳遞至 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c2351-109">To enable script support, create an <xref:System.Xml.Xsl.XsltSettings> object with the <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A> property set to `true` and pass the object to the <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2351-110">僅當需要指令碼支援且在完全受信任的環境中運作時，才應啟用 XSLT 指令碼。</span><span class="sxs-lookup"><span data-stu-id="c2351-110">XSLT scripting should be enabled only if you require script support and you are working in a fully trusted environment.</span></span>  
  
## <a name="msxslscript-element-definition"></a><span data-ttu-id="c2351-111">msxsl:script 項目定義</span><span class="sxs-lookup"><span data-stu-id="c2351-111">msxsl:script Element Definition</span></span>  
 <span data-ttu-id="c2351-112">`msxsl:script` 項目是 XSLT 1.0 版建議事項的 Microsoft 擴充功能，其定義如下：</span><span class="sxs-lookup"><span data-stu-id="c2351-112">The `msxsl:script` element is a Microsoft extension to the XSLT 1.0 recommendation and has the following definition:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="c2351-113">`msxsl` 前置詞會繫結至 `urn:schemas-microsoft-com:xslt` 命名空間 URI。</span><span class="sxs-lookup"><span data-stu-id="c2351-113">The `msxsl` prefix is bound to the `urn:schemas-microsoft-com:xslt` namespace URI.</span></span> <span data-ttu-id="c2351-114">樣式表必須包括 `xmlns:msxsl=urn:schemas-microsoft-com:xslt` 命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="c2351-114">The style sheet must include the `xmlns:msxsl=urn:schemas-microsoft-com:xslt` namespace declaration.</span></span>  
  
 <span data-ttu-id="c2351-115">`language` 屬性是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c2351-115">The `language` attribute is optional.</span></span> <span data-ttu-id="c2351-116">其值是內嵌程式碼區塊的程式碼語言。</span><span class="sxs-lookup"><span data-stu-id="c2351-116">Its value is the code language of the embedded code block.</span></span> <span data-ttu-id="c2351-117">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> 方法，可將該語言對應至適當的 CodeDOM 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c2351-117">The language is mapped to the appropriate CodeDOM compiler using the <xref:System.CodeDom.Compiler.CodeDomProvider.CreateProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c2351-118"><xref:System.Xml.Xsl.XslCompiledTransform> 類別可支援任何 Microsoft .NET 語言 (假設機器上已安裝適當的提供者，且已註冊到 machine.config 檔案的 system.codedom 區段中)。</span><span class="sxs-lookup"><span data-stu-id="c2351-118">The <xref:System.Xml.Xsl.XslCompiledTransform> class can support any Microsoft .NET language, assuming the appropriate provider is installed on the machine and is registered in the system.codedom section of the machine.config file.</span></span> <span data-ttu-id="c2351-119">如果沒有指定 `language` 屬性，語言預設為 JScript。</span><span class="sxs-lookup"><span data-stu-id="c2351-119">If a `language` attribute is not specified, the language defaults to JScript.</span></span> <span data-ttu-id="c2351-120">語言名稱不區分大小寫，因此 JavaScript 與 javascript 是一樣的。</span><span class="sxs-lookup"><span data-stu-id="c2351-120">The language name is not case-sensitive so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="c2351-121">`implements-prefix` 屬性是必要的。</span><span class="sxs-lookup"><span data-stu-id="c2351-121">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="c2351-122">這個屬性用來宣告命名空間，並把它與指令碼區塊產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c2351-122">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="c2351-123">這個屬性的值是表示命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="c2351-123">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="c2351-124">這個前置詞可以被定義在樣式表內的任意處。</span><span class="sxs-lookup"><span data-stu-id="c2351-124">This prefix can be defined somewhere in a style sheet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2351-125">使用 `msxsl:script` 項目時，無論所使用的語言為何，都強烈建議將指令碼置於 CDATA 區段內。</span><span class="sxs-lookup"><span data-stu-id="c2351-125">When using the `msxsl:script` element, we strongly recommend that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="c2351-126">因為指令碼可能包含給定語言的運算子、識別項或分隔符號，所以如果未包含在 CDATA 區段中，則有可能會錯誤解譯為 XML。</span><span class="sxs-lookup"><span data-stu-id="c2351-126">Because the script can contain operators, identifiers, or delimiters for a given language, if it is not contained within a CDATA section, it has the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="c2351-127">下列 XML 顯示可將程式碼放置其中的 CDATA 區段範本。</span><span class="sxs-lookup"><span data-stu-id="c2351-127">The following XML shows a template of the CDATA section where code can be placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='your-prefix' language='CSharp'>  
<![CDATA[  
// Code block.  
]]>  
</msxsl:script>  
```  
  
## <a name="script-functions"></a><span data-ttu-id="c2351-128">指令碼函式</span><span class="sxs-lookup"><span data-stu-id="c2351-128">Script Functions</span></span>  
 <span data-ttu-id="c2351-129">函式可在 `msxsl:script` 項目內進行宣告。</span><span class="sxs-lookup"><span data-stu-id="c2351-129">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="c2351-130">宣告函式時，函式是包含在指令碼區塊內。</span><span class="sxs-lookup"><span data-stu-id="c2351-130">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="c2351-131">樣式表可以包含多個指令碼區塊，而每一個都會各自獨立運作。</span><span class="sxs-lookup"><span data-stu-id="c2351-131">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="c2351-132">這表示如果您在指令碼區塊內執行，您無法呼叫在另一個指令碼區塊內所定義的函式，除非它被宣告成有相同的命名空間和相同的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="c2351-132">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="c2351-133">因為每一個指令碼區塊都可以使用本身的語言，且這些區塊是根據該語言剖析器的文法規則進行剖析，建議您針對使用中的語言使用正確的語法。</span><span class="sxs-lookup"><span data-stu-id="c2351-133">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser we recommend that you use the correct syntax for the language in use.</span></span> <span data-ttu-id="c2351-134">例如，如果是 Microsoft C# 指令碼區塊，請使用 C# 註解語法。</span><span class="sxs-lookup"><span data-stu-id="c2351-134">For example, if you are in a Microsoft C# script block, use the C# comment syntax.</span></span>  
  
 <span data-ttu-id="c2351-135">提供給函式的引數及傳回值可具有任何類型。</span><span class="sxs-lookup"><span data-stu-id="c2351-135">The supplied arguments and return values to the function can be of any type.</span></span> <span data-ttu-id="c2351-136">因為 W3C XPath 類型是 Common Language Runtime (CLR) 類型的子集，所以當系統認為某類型不是 XPath 類型時，便會進行類型轉換。</span><span class="sxs-lookup"><span data-stu-id="c2351-136">Because the W3C XPath types are a subset of the common language runtime (CLR) types, type conversion takes place on types that are not considered to be an XPath type.</span></span> <span data-ttu-id="c2351-137">下表顯示對應的 W3C 類型與對等的 CLR 類型。</span><span class="sxs-lookup"><span data-stu-id="c2351-137">The following table shows the corresponding W3C types and the equivalent CLR type.</span></span>  
  
|<span data-ttu-id="c2351-138">W3C 類型</span><span class="sxs-lookup"><span data-stu-id="c2351-138">W3C type</span></span>|<span data-ttu-id="c2351-139">CLR 類型</span><span class="sxs-lookup"><span data-stu-id="c2351-139">CLR type</span></span>|  
|--------------|--------------|  
|`String`|<xref:System.String>|  
|`Boolean`|<xref:System.Boolean>|  
|`Number`|<xref:System.Double>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator>|  
  
 <span data-ttu-id="c2351-140">CLR 數字類型會轉換為 <xref:System.Double>。</span><span class="sxs-lookup"><span data-stu-id="c2351-140">CLR numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="c2351-141"><xref:System.DateTime> 類型會轉換為 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="c2351-141">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="c2351-142"><xref:System.Xml.XPath.IXPathNavigable> 類型會轉換為 <xref:System.Xml.XPath.XPathNavigator>。</span><span class="sxs-lookup"><span data-stu-id="c2351-142"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="c2351-143">**XPathNavigator[]** 會轉換為 <xref:System.Xml.XPath.XPathNodeIterator>。</span><span class="sxs-lookup"><span data-stu-id="c2351-143">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="c2351-144">所有其他類型都會擲回錯誤。</span><span class="sxs-lookup"><span data-stu-id="c2351-144">All other types throw an error.</span></span>  
  
### <a name="importing-namespaces-and-assemblies"></a><span data-ttu-id="c2351-145">匯入命名空間及組件</span><span class="sxs-lookup"><span data-stu-id="c2351-145">Importing Namespaces and Assemblies</span></span>  
 <span data-ttu-id="c2351-146"><xref:System.Xml.Xsl.XslCompiledTransform> 類別會預先定義一組預設 `msxsl:script` 項目所支援的命名空間及組件。</span><span class="sxs-lookup"><span data-stu-id="c2351-146">The <xref:System.Xml.Xsl.XslCompiledTransform> class predefines a set of assemblies and namespaces that are supported by default by the `msxsl:script` element.</span></span> <span data-ttu-id="c2351-147">不過，透過將組件及命名空間匯入 `msxsl:script` 區塊，也可以使用屬於不在預先定義清單上之命名空間的類別及成員。</span><span class="sxs-lookup"><span data-stu-id="c2351-147">However, you can use classes and members belonging to a namespace that is not on the predefined list by importing the assembly and namespace in `msxsl:script` block.</span></span>  
  
#### <a name="assemblies"></a><span data-ttu-id="c2351-148">組件</span><span class="sxs-lookup"><span data-stu-id="c2351-148">Assemblies</span></span>  
 <span data-ttu-id="c2351-149">預設會參考下列兩個組件：</span><span class="sxs-lookup"><span data-stu-id="c2351-149">The following two assemblies are referenced by default:</span></span>  
  
-   <span data-ttu-id="c2351-150">System.dll</span><span class="sxs-lookup"><span data-stu-id="c2351-150">System.dll</span></span>  
  
-   <span data-ttu-id="c2351-151">System.Xml.dll</span><span class="sxs-lookup"><span data-stu-id="c2351-151">System.Xml.dll</span></span>  
  
-   <span data-ttu-id="c2351-152">Microsoft.VisualBasic.dll (若指令碼語言為 VB)</span><span class="sxs-lookup"><span data-stu-id="c2351-152">Microsoft.VisualBasic.dll (when the script language is VB)</span></span>  
  
 <span data-ttu-id="c2351-153">您可以使用 `msxsl:assembly` 項目匯入其他組件。</span><span class="sxs-lookup"><span data-stu-id="c2351-153">You can import the additional assemblies using the `msxsl:assembly` element.</span></span> <span data-ttu-id="c2351-154">編譯樣式表時會併入該組件。</span><span class="sxs-lookup"><span data-stu-id="c2351-154">This includes the assembly when the style sheet is compiled.</span></span> <span data-ttu-id="c2351-155">`msxsl:assembly` 項目具有下列定義：</span><span class="sxs-lookup"><span data-stu-id="c2351-155">The `msxsl:assembly` element has the following definition:</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:assembly name="system.assemblyName" />  
  <msxsl:assembly href="path-name" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="c2351-156">`name` 屬性包含組件名稱，而 `href` 屬性則包含組件的路徑。</span><span class="sxs-lookup"><span data-stu-id="c2351-156">The `name` attribute contains the name of the assembly and the `href` attribute contains the path to the assembly.</span></span> <span data-ttu-id="c2351-157">組件名稱可為完整名稱 (如 "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089") 或簡短名稱 (如 "System.Web")。</span><span class="sxs-lookup"><span data-stu-id="c2351-157">The assembly name can be a full name, such as "System.Data, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b77a5c561934e089", or a short name, such as "System.Web".</span></span>  
  
#### <a name="namespaces"></a><span data-ttu-id="c2351-158">命名空間</span><span class="sxs-lookup"><span data-stu-id="c2351-158">Namespaces</span></span>  
 <span data-ttu-id="c2351-159">預設會包含下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="c2351-159">The following namespaces are included by default:</span></span>  
  
-   <span data-ttu-id="c2351-160">系統</span><span class="sxs-lookup"><span data-stu-id="c2351-160">System</span></span>  
  
-   <span data-ttu-id="c2351-161">System.Collection</span><span class="sxs-lookup"><span data-stu-id="c2351-161">System.Collection</span></span>  
  
-   <span data-ttu-id="c2351-162">System.Text</span><span class="sxs-lookup"><span data-stu-id="c2351-162">System.Text</span></span>  
  
-   <span data-ttu-id="c2351-163">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="c2351-163">System.Text.RegularExpressions</span></span>  
  
-   <span data-ttu-id="c2351-164">System.Xml</span><span class="sxs-lookup"><span data-stu-id="c2351-164">System.Xml</span></span>  
  
-   <span data-ttu-id="c2351-165">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="c2351-165">System.Xml.Xsl</span></span>  
  
-   <span data-ttu-id="c2351-166">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="c2351-166">System.Xml.XPath</span></span>  
  
-   <span data-ttu-id="c2351-167">Microsoft.VisualBasic (若指令碼語言為 VB)</span><span class="sxs-lookup"><span data-stu-id="c2351-167">Microsoft.VisualBasic (when the script language is VB)</span></span>  
  
 <span data-ttu-id="c2351-168">您可使用 `namespace` 屬性加入對其他命名空間的支援。</span><span class="sxs-lookup"><span data-stu-id="c2351-168">You can add support for additional namespaces using the `namespace` attribute.</span></span> <span data-ttu-id="c2351-169">屬性值是命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="c2351-169">The attribute value is the name of the namespace.</span></span>  
  
```xml  
<msxsl:script>  
  <msxsl:using namespace="system.namespaceName" />  
    <![CDATA[  
    // User code  
    ]]>  
</msxsl:script>  
```  
  
## <a name="example"></a><span data-ttu-id="c2351-170">範例</span><span class="sxs-lookup"><span data-stu-id="c2351-170">Example</span></span>  
 <span data-ttu-id="c2351-171">下列範例會使用內嵌指令碼來計算圓周 (假設已經知道其半徑)。</span><span class="sxs-lookup"><span data-stu-id="c2351-171">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
 [!code-csharp[XSLT_Script#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Script/CS/xslt_script.cs#1)]
 [!code-vb[XSLT_Script#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Script/VB/xslt_script.vb#1)]  
  
#### <a name="numberxml"></a><span data-ttu-id="c2351-172">number.xml</span><span class="sxs-lookup"><span data-stu-id="c2351-172">number.xml</span></span>  
 [!code-xml[XSLT_Script#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/number.xml#2)]  
  
#### <a name="calcxsl"></a><span data-ttu-id="c2351-173">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="c2351-173">calc.xsl</span></span>  
 [!code-xml[XSLT_Script#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Script/XML/calc.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="c2351-174">輸出</span><span class="sxs-lookup"><span data-stu-id="c2351-174">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2351-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2351-175">See also</span></span>

- [<span data-ttu-id="c2351-176">XSLT 轉換</span><span class="sxs-lookup"><span data-stu-id="c2351-176">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [<span data-ttu-id="c2351-177">動態原始程式碼的產生和編譯</span><span class="sxs-lookup"><span data-stu-id="c2351-177">Dynamic Source Code Generation and Compilation</span></span>](../../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)
