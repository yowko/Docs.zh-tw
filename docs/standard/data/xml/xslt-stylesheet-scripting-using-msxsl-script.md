---
title: 使用 &lt;msxsl:script&gt; 的 XSLT 樣式表指令碼
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 68c98b3b4effbe7cea1a3c4443d2222e6bbcd43c
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2018
ms.locfileid: "46584249"
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a><span data-ttu-id="8b39a-102">使用 &lt;msxsl:script&gt; 的 XSLT 樣式表指令碼</span><span class="sxs-lookup"><span data-stu-id="8b39a-102">XSLT Stylesheet Scripting Using &lt;msxsl:script&gt;</span></span>
<span data-ttu-id="8b39a-103"><xref:System.Xml.Xsl.XslTransform> 類別支援使用 `script` 項目的內嵌指令碼。</span><span class="sxs-lookup"><span data-stu-id="8b39a-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b39a-104"><xref:System.Xml.Xsl.XslTransform> 類別在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已過時。</span><span class="sxs-lookup"><span data-stu-id="8b39a-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="8b39a-105">您可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 類別來執行可延伸樣式表語言轉換 (XSLT)。</span><span class="sxs-lookup"><span data-stu-id="8b39a-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="8b39a-106">如需詳細資訊，請參閱[使用 XslCompiledTransform 類別](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[從 XslTransform 類別移轉](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)。</span><span class="sxs-lookup"><span data-stu-id="8b39a-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="8b39a-107"><xref:System.Xml.Xsl.XslTransform> 類別支援使用 `script` 項目的內嵌指令碼。</span><span class="sxs-lookup"><span data-stu-id="8b39a-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="8b39a-108">載入樣式表時，任何已定義的函式都會被包裝在類別定義內，而編譯成 Microsoft Intermediate Language (MSIL)，因此不會降低效能。</span><span class="sxs-lookup"><span data-stu-id="8b39a-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="8b39a-109">`<msxsl:script>` 項目的定義如下：</span><span class="sxs-lookup"><span data-stu-id="8b39a-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="8b39a-110">其中 `msxsl` 是繫結至命名空間 `urn:schemas-microsoft-com:xslt` 的前置詞。</span><span class="sxs-lookup"><span data-stu-id="8b39a-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="8b39a-111">`language` 屬性並非必要項目，但若指定，則其值必須為下列其中一個值：C#、VB、JScript、JavaScript、VisualBasic 或 CSharp。</span><span class="sxs-lookup"><span data-stu-id="8b39a-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: C#, VB, JScript, JavaScript, VisualBasic, or CSharp.</span></span> <span data-ttu-id="8b39a-112">如果沒有指定的話，語言預設為 JScript。</span><span class="sxs-lookup"><span data-stu-id="8b39a-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="8b39a-113">`language-name` 不區分大小寫，因此 'JavaScript' 和 'javascript' 是一樣的。</span><span class="sxs-lookup"><span data-stu-id="8b39a-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="8b39a-114">`implements-prefix` 屬性是必要的。</span><span class="sxs-lookup"><span data-stu-id="8b39a-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="8b39a-115">這個屬性用來宣告命名空間，並把它與指令碼區塊產生關聯。</span><span class="sxs-lookup"><span data-stu-id="8b39a-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="8b39a-116">這個屬性的值是表示命名空間的前置詞。</span><span class="sxs-lookup"><span data-stu-id="8b39a-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="8b39a-117">這個命名空間可以被定義在樣式表內的某處。</span><span class="sxs-lookup"><span data-stu-id="8b39a-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="8b39a-118">因為 `msxsl:script` 項目屬於命名空間 `urn:schemas-microsoft-com:xslt`，所以樣式表必須包含命名空間宣告 `xmlns:msxsl=urn:schemas-microsoft-com:xslt`。</span><span class="sxs-lookup"><span data-stu-id="8b39a-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="8b39a-119">如果指令碼的呼叫端沒有 <xref:System.Security.Permissions.SecurityPermissionFlag> 存取使用權限，則永遠不會編譯樣式表中的指令碼，且無法呼叫 <xref:System.Xml.Xsl.XslTransform.Load%2A>。</span><span class="sxs-lookup"><span data-stu-id="8b39a-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="8b39a-120">如果呼叫者端擁有 `UnmanagedCode` 使用權限，則會編譯指令碼，但是所允許的作業則取決於載入時所提供的辨識項。</span><span class="sxs-lookup"><span data-stu-id="8b39a-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="8b39a-121">如果使用其中一個採用 <xref:System.Xml.Xsl.XslTransform.Load%2A> 或 <xref:System.Xml.XmlReader> 的 <xref:System.Xml.XPath.XPathNavigator> 方法來載入樣式表，則必須使用將 <xref:System.Xml.Xsl.XslTransform.Load%2A> 參數做為它的其中一個引數的 <xref:System.Security.Policy.Evidence> 多載。</span><span class="sxs-lookup"><span data-stu-id="8b39a-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="8b39a-122">若要提供辨識項，呼叫端必須具有 <xref:System.Security.Permissions.SecurityPermissionFlag> 使用權限，才可提供指令碼組件的 `Evidence`。</span><span class="sxs-lookup"><span data-stu-id="8b39a-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="8b39a-123">如果呼叫端沒有這項使用權限，則可以將 `Evidence` 參數設為 `null`。</span><span class="sxs-lookup"><span data-stu-id="8b39a-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="8b39a-124">這樣 <xref:System.Xml.Xsl.XslTransform.Load%2A> 函式會在尋找指令碼時失敗。</span><span class="sxs-lookup"><span data-stu-id="8b39a-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="8b39a-125">`ControlEvidence` 使用權限被認為是功能非常強的使用權限，只能授與高度信任的程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b39a-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="8b39a-126">若要從組件中取得辨識項，請使用 `this.GetType().Assembly.Evidence`。</span><span class="sxs-lookup"><span data-stu-id="8b39a-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="8b39a-127">若要從統一資源識別元 (URI) 取得辨識項，請使用 `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`。</span><span class="sxs-lookup"><span data-stu-id="8b39a-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="8b39a-128">如果使用的是採用 <xref:System.Xml.Xsl.XslTransform.Load%2A> 但不含 <xref:System.Xml.XmlResolver> 的 `Evidence` 方法，則組件的安全性區域會預設為「完全信任」。</span><span class="sxs-lookup"><span data-stu-id="8b39a-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="8b39a-129">如需詳細資訊，請參閱 <xref:System.Security.SecurityZone> 和[具名使用權限集合](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3)。</span><span class="sxs-lookup"><span data-stu-id="8b39a-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="8b39a-130">函式可在 `msxsl:script` 項目內進行宣告。</span><span class="sxs-lookup"><span data-stu-id="8b39a-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="8b39a-131">下表顯示根據預設所支援的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8b39a-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="8b39a-132">您可以使用所列之命名空間以外的類別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="8b39a-133">不過這些類別必須是完整限定。</span><span class="sxs-lookup"><span data-stu-id="8b39a-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="8b39a-134">預設的命名空間</span><span class="sxs-lookup"><span data-stu-id="8b39a-134">Default Namespaces</span></span>|<span data-ttu-id="8b39a-135">描述</span><span class="sxs-lookup"><span data-stu-id="8b39a-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="8b39a-136">系統</span><span class="sxs-lookup"><span data-stu-id="8b39a-136">System</span></span>|<span data-ttu-id="8b39a-137">系統類別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-137">System class.</span></span>|  
|<span data-ttu-id="8b39a-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="8b39a-138">System.Collection</span></span>|<span data-ttu-id="8b39a-139">集合類別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-139">Collection classes.</span></span>|  
|<span data-ttu-id="8b39a-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="8b39a-140">System.Text</span></span>|<span data-ttu-id="8b39a-141">文字類別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-141">Text classes.</span></span>|  
|<span data-ttu-id="8b39a-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="8b39a-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="8b39a-143">規則運算式類別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="8b39a-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="8b39a-144">System.Xml</span></span>|<span data-ttu-id="8b39a-145">核心 XML 類別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-145">Core XML classes.</span></span>|  
|<span data-ttu-id="8b39a-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="8b39a-146">System.Xml.Xsl</span></span>|<span data-ttu-id="8b39a-147">XSLT 類別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-147">XSLT classes.</span></span>|  
|<span data-ttu-id="8b39a-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="8b39a-148">System.Xml.XPath</span></span>|<span data-ttu-id="8b39a-149">XML 路徑語言 (XPath) 類別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="8b39a-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="8b39a-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="8b39a-151">Microsoft Visual Basic 指令碼的類別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="8b39a-152">宣告函式時，函式是包含在指令碼區塊內。</span><span class="sxs-lookup"><span data-stu-id="8b39a-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="8b39a-153">樣式表可以包含多個指令碼區塊，而每一個都會各自獨立運作。</span><span class="sxs-lookup"><span data-stu-id="8b39a-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="8b39a-154">這表示如果您在指令碼區塊內執行，您無法呼叫在另一個指令碼區塊內所定義的函式，除非它被宣告成有相同的命名空間和相同的指令碼語言。</span><span class="sxs-lookup"><span data-stu-id="8b39a-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="8b39a-155">因為每一個指令碼區塊都可以使用本身的語言，且這些區塊是根據該語言剖析器的文法規則進行剖析，因此您必須針對使用中的語言使用正確的語法。</span><span class="sxs-lookup"><span data-stu-id="8b39a-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="8b39a-156">例如，如果是在 C# 指令碼區塊中，則在區塊中使用 XML 註解節點 `<!-- an XML comment -->` 就會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8b39a-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="8b39a-157">指令碼函式所定義之提供的引數和傳回值，必須屬於全球資訊網協會 (W3C) XPath 或 XSLT 的其中一種型別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="8b39a-158">下表列出對應的 W3C 型別、對等的 .NET Framework 類別 (型別)，以及 W3C 型別是 XPath 還是 XSLT 型別。</span><span class="sxs-lookup"><span data-stu-id="8b39a-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="8b39a-159">類型</span><span class="sxs-lookup"><span data-stu-id="8b39a-159">Type</span></span>|<span data-ttu-id="8b39a-160">對等的 .NET Framework 類別 (型別)</span><span class="sxs-lookup"><span data-stu-id="8b39a-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="8b39a-161">XPath 型別或 XSLT 型別</span><span class="sxs-lookup"><span data-stu-id="8b39a-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="8b39a-162">String</span><span class="sxs-lookup"><span data-stu-id="8b39a-162">String</span></span>|<span data-ttu-id="8b39a-163">System.String</span><span class="sxs-lookup"><span data-stu-id="8b39a-163">System.String</span></span>|<span data-ttu-id="8b39a-164">XPath</span><span class="sxs-lookup"><span data-stu-id="8b39a-164">XPath</span></span>|  
|<span data-ttu-id="8b39a-165">Boolean</span><span class="sxs-lookup"><span data-stu-id="8b39a-165">Boolean</span></span>|<span data-ttu-id="8b39a-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="8b39a-166">System.Boolean</span></span>|<span data-ttu-id="8b39a-167">XPath</span><span class="sxs-lookup"><span data-stu-id="8b39a-167">XPath</span></span>|  
|<span data-ttu-id="8b39a-168">number</span><span class="sxs-lookup"><span data-stu-id="8b39a-168">Number</span></span>|<span data-ttu-id="8b39a-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="8b39a-169">System.Double</span></span>|<span data-ttu-id="8b39a-170">XPath</span><span class="sxs-lookup"><span data-stu-id="8b39a-170">XPath</span></span>|  
|<span data-ttu-id="8b39a-171">Result Tree Fragment</span><span class="sxs-lookup"><span data-stu-id="8b39a-171">Result Tree Fragment</span></span>|<span data-ttu-id="8b39a-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="8b39a-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="8b39a-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="8b39a-173">XSLT</span></span>|  
|<span data-ttu-id="8b39a-174">Node Set</span><span class="sxs-lookup"><span data-stu-id="8b39a-174">Node Set</span></span>|<span data-ttu-id="8b39a-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="8b39a-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="8b39a-176">XPath</span><span class="sxs-lookup"><span data-stu-id="8b39a-176">XPath</span></span>|  
  
 <span data-ttu-id="8b39a-177">如果指令碼函式使用下列其中一個數字型別：Int16、UInt16、Int32、UInt32、Int64、UInt64、Single 或 Decimal，則會將這些型別強制成 Double (其對應至 W3C XPath 型別數值)。</span><span class="sxs-lookup"><span data-stu-id="8b39a-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="8b39a-178">所有其他型別會透過呼叫 `ToString` 方法而強制轉成字串。</span><span class="sxs-lookup"><span data-stu-id="8b39a-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="8b39a-179">如果指令碼函式使用前述以外的型別，或將樣式表載入 <xref:System.Xml.Xsl.XslTransform> 物件時未編譯函式，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8b39a-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="8b39a-180">使用 `msxsl:script` 項目時，無論所使用的語言為何，都強烈建議將指令碼置於 CDATA 區段內。</span><span class="sxs-lookup"><span data-stu-id="8b39a-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="8b39a-181">例如，下例 XML 顯示您的程式碼所在的 CDATA 區段的範本。</span><span class="sxs-lookup"><span data-stu-id="8b39a-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="8b39a-182">建議將所有指令碼內容置於 CDATA 區段內，因為指定之語言的運算子、識別項或分隔符號有可能會被錯譯為 XML。</span><span class="sxs-lookup"><span data-stu-id="8b39a-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="8b39a-183">下列範例顯示在指令碼中使用邏輯 AND 運算子。</span><span class="sxs-lookup"><span data-stu-id="8b39a-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp>  
    public string book(string abc, string xyz)  
    {  if ((abc== abc)&&(abc== xyz)) return bar+xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="8b39a-184">這將擲回例外狀況，因為未逸出連字號。</span><span class="sxs-lookup"><span data-stu-id="8b39a-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="8b39a-185">會將這份文件載入為 XML，且對 `msxsl:script` 項目標記之間的文字並未採取特別的處置。</span><span class="sxs-lookup"><span data-stu-id="8b39a-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b39a-186">範例</span><span class="sxs-lookup"><span data-stu-id="8b39a-186">Example</span></span>  
 <span data-ttu-id="8b39a-187">下列範例會使用內嵌指令碼來計算圓周 (假設已經知道其半徑)。</span><span class="sxs-lookup"><span data-stu-id="8b39a-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.               
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub   
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main() {  
  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.               
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }   
}  
```  
  
## <a name="input"></a><span data-ttu-id="8b39a-188">輸入</span><span class="sxs-lookup"><span data-stu-id="8b39a-188">Input</span></span>  
 <span data-ttu-id="8b39a-189">number.xml</span><span class="sxs-lookup"><span data-stu-id="8b39a-189">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="8b39a-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="8b39a-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius){  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">    
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>   
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="8b39a-191">輸出</span><span class="sxs-lookup"><span data-stu-id="8b39a-191">Output</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b39a-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b39a-192">See also</span></span>

- [<span data-ttu-id="8b39a-193">XslTransform 類別實作 XSLT 處理器</span><span class="sxs-lookup"><span data-stu-id="8b39a-193">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
