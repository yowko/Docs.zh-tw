---
title: "屬性概觀 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0464de06390a9899cbe312b16cbad41d0b6639eb
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="2da26-102">屬性概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2da26-102">Attributes overview (Visual Basic)</span></span>
<span data-ttu-id="2da26-103">屬性提供一種功能強大的方法，可將中繼資料或宣告資訊關聯至程式碼 (組建、型別、方法、屬性等)。</span><span class="sxs-lookup"><span data-stu-id="2da26-103">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="2da26-104">將屬性關聯至程式實體之後，就能在執行階段使用稱為「反映」的技術來查詢該屬性。</span><span class="sxs-lookup"><span data-stu-id="2da26-104">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="2da26-105">如需詳細資訊，請參閱[反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="2da26-105">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
 <span data-ttu-id="2da26-106">屬性 (Attribute) 包含下列屬性 (Property)：</span><span class="sxs-lookup"><span data-stu-id="2da26-106">Attributes have the following properties:</span></span>  
  
-   <span data-ttu-id="2da26-107">屬性會將中繼資料新增至您的程式。</span><span class="sxs-lookup"><span data-stu-id="2da26-107">Attributes add metadata to your program.</span></span> <span data-ttu-id="2da26-108">「中繼資料」是在程式中定義的型別相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2da26-108">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="2da26-109">所有的 .NET 組件都包含一組指定的中繼資料，來描述組件中所定義的型別和型別成員。</span><span class="sxs-lookup"><span data-stu-id="2da26-109">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="2da26-110">您可以新增自訂屬性來指定所需的任何其他資訊。</span><span class="sxs-lookup"><span data-stu-id="2da26-110">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="2da26-111">如需詳細資訊，請參閱[建立自訂屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="2da26-111">For more information, see, [Creating Custom Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md).</span></span>  
  
-   <span data-ttu-id="2da26-112">您可以將一或多個屬性 (Attribute) 套用至整個組件、模組或較小的程式元素，例如類別和屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="2da26-112">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>  
  
-   <span data-ttu-id="2da26-113">屬性 (Attribute) 可以利用與方法與屬性 (Property) 相同的方式來接受引數。</span><span class="sxs-lookup"><span data-stu-id="2da26-113">Attributes can accept arguments in the same way as methods and properties.</span></span>  
  
-   <span data-ttu-id="2da26-114">您的程式可以使用反映，來檢查自己的中繼資料或其他程式的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2da26-114">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="2da26-115">如需詳細資訊，請參閱[使用反映存取屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)。</span><span class="sxs-lookup"><span data-stu-id="2da26-115">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="using-attributes"></a><span data-ttu-id="2da26-116">使用屬性</span><span class="sxs-lookup"><span data-stu-id="2da26-116">Using Attributes</span></span>  
 <span data-ttu-id="2da26-117">屬性可以放置於大多數的任意宣告中，但特定的屬性可能會限制它適用的宣告型別。</span><span class="sxs-lookup"><span data-stu-id="2da26-117">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="2da26-118">在 Visual Basic 中，會使用角括弧 (\< >) 將屬性括起來。</span><span class="sxs-lookup"><span data-stu-id="2da26-118">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="2da26-119">它必須出現在同一行中要套用它的元素正前方。</span><span class="sxs-lookup"><span data-stu-id="2da26-119">It must appear immediately before the element to which it is applied, on the same line.</span></span>  
  
 <span data-ttu-id="2da26-120">在此範例中，會使用 <xref:System.SerializableAttribute> 屬性來將特定的特性套用至類別：</span><span class="sxs-lookup"><span data-stu-id="2da26-120">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>  
  
```vb  
<System.Serializable()> Public Class SampleClass  
    ' Objects of this type can be serialized.  
End Class  
```  
  
 <span data-ttu-id="2da26-121">具有 <xref:System.Runtime.InteropServices.DllImportAttribute> 屬性的方法宣告如下：</span><span class="sxs-lookup"><span data-stu-id="2da26-121">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
<System.Runtime.InteropServices.DllImport("user32.dll")>   
Sub SampleMethod()  
End Sub  
```  
  
 <span data-ttu-id="2da26-122">一個宣告中可以放置一個以上的屬性：</span><span class="sxs-lookup"><span data-stu-id="2da26-122">More than one attribute can be placed on a declaration:</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
```  
  
```vb  
Sub MethodA(<[In](), Out()> ByVal x As Double)  
End Sub  
Sub MethodB(<Out(), [In]()> ByVal x As Double)  
End Sub  
```  
  
 <span data-ttu-id="2da26-123">可以針對特定實體多次指定某些屬性。</span><span class="sxs-lookup"><span data-stu-id="2da26-123">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="2da26-124"><xref:System.Diagnostics.ConditionalAttribute> 就是這種多次使用屬性的一個例子：</span><span class="sxs-lookup"><span data-stu-id="2da26-124">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>  
  
```vb  
<Conditional("DEBUG"), Conditional("TEST1")>   
Sub TraceMethod()  
End Sub  
```  
  
> [!NOTE]
>  <span data-ttu-id="2da26-125">依照慣例，所有的屬性名稱都會以 "Attribute" 這個字結尾，以便與 .NET Framework 中的其他項目有所區別。</span><span class="sxs-lookup"><span data-stu-id="2da26-125">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="2da26-126">不過，您在程式碼中使用屬性時，不需要指定屬性的後置詞。</span><span class="sxs-lookup"><span data-stu-id="2da26-126">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="2da26-127">例如，`[DllImport]` 相當於 `[DllImportAttribute]`，但 `DllImportAttribute` 是屬性在 .NET Framework 中的實際名稱。</span><span class="sxs-lookup"><span data-stu-id="2da26-127">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>  
  
### <a name="attribute-parameters"></a><span data-ttu-id="2da26-128">屬性參數</span><span class="sxs-lookup"><span data-stu-id="2da26-128">Attribute Parameters</span></span>  
 <span data-ttu-id="2da26-129">許多屬性的參數可以是位置、未命名或具名的參數。</span><span class="sxs-lookup"><span data-stu-id="2da26-129">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="2da26-130">任何位置參數都必須以特定順序指定，而且不能省略；具名參數是選擇性且可依任何順序指定。</span><span class="sxs-lookup"><span data-stu-id="2da26-130">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="2da26-131">位置參數會先指定。</span><span class="sxs-lookup"><span data-stu-id="2da26-131">Positional parameters are specified first.</span></span> <span data-ttu-id="2da26-132">例如，這三個屬性是相等的：</span><span class="sxs-lookup"><span data-stu-id="2da26-132">For example, these three attributes are equivalent:</span></span>  
  
```vb  
<DllImport("user32.dll")>  
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>  
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>  
```  
  
 <span data-ttu-id="2da26-133">第一個參數 (DLL 名稱) 是位置參數，一律會先出現；其他的則為具名參數。</span><span class="sxs-lookup"><span data-stu-id="2da26-133">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="2da26-134">在此案例中，這兩個具名參數預設為 false，因此可以省略。</span><span class="sxs-lookup"><span data-stu-id="2da26-134">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="2da26-135">請參閱個別屬性的文件，以取得預設參數值的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2da26-135">Refer to the individual attribute's documentation for information on default parameter values.</span></span>  
  
### <a name="attribute-targets"></a><span data-ttu-id="2da26-136">屬性目標</span><span class="sxs-lookup"><span data-stu-id="2da26-136">Attribute Targets</span></span>  
 <span data-ttu-id="2da26-137">屬性的「目標」是要套用該屬性的實體。</span><span class="sxs-lookup"><span data-stu-id="2da26-137">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="2da26-138">例如，屬性可套用至類別、特定的方法或整個組件。</span><span class="sxs-lookup"><span data-stu-id="2da26-138">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="2da26-139">根據預設，屬性會套用到位於它正後方的元素。</span><span class="sxs-lookup"><span data-stu-id="2da26-139">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="2da26-140">但是，舉例來說，您也可以明確地識別是否要將屬性套用到方法、它的參數或它的傳回值。</span><span class="sxs-lookup"><span data-stu-id="2da26-140">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>  
  
 <span data-ttu-id="2da26-141">若要明確地識別屬性目標，請使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="2da26-141">To explicitly identify an attribute target, use the following syntax:</span></span>  
  
```vb  
<target : attribute-list>  
```  
  
 <span data-ttu-id="2da26-142">下表顯示可能的 `target` 值清單。</span><span class="sxs-lookup"><span data-stu-id="2da26-142">The list of possible `target` values is shown in the following table.</span></span>  
  
|<span data-ttu-id="2da26-143">目標值</span><span class="sxs-lookup"><span data-stu-id="2da26-143">Target value</span></span>|<span data-ttu-id="2da26-144">適用於</span><span class="sxs-lookup"><span data-stu-id="2da26-144">Applies to</span></span>|  
|------------------|----------------|  
|`assembly`|<span data-ttu-id="2da26-145">整個組件</span><span class="sxs-lookup"><span data-stu-id="2da26-145">Entire assembly</span></span>|  
|`module`|<span data-ttu-id="2da26-146">目前的組件模組 (這與 Visual Basic 模組不同)</span><span class="sxs-lookup"><span data-stu-id="2da26-146">Current assembly module (which is different from a Visual Basic Module)</span></span>|  
  
 <span data-ttu-id="2da26-147">下列範例示範如何將屬性套用到組件和模組。</span><span class="sxs-lookup"><span data-stu-id="2da26-147">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="2da26-148">如需詳細資訊，請參閱[通用屬性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="2da26-148">For more information, see [Common Attributes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
```vb  
Imports System.Reflection  
<Assembly: AssemblyTitleAttribute("Production assembly 4"),   
Module: CLSCompliant(True)>   
```  
  
## <a name="common-uses-for-attributes"></a><span data-ttu-id="2da26-149">屬性的常見用法</span><span class="sxs-lookup"><span data-stu-id="2da26-149">Common Uses for Attributes</span></span>  
 <span data-ttu-id="2da26-150">下列清單包含一些程式碼中常見的屬性用法：</span><span class="sxs-lookup"><span data-stu-id="2da26-150">The following list includes a few of the common uses of attributes in code:</span></span>  
  
-   <span data-ttu-id="2da26-151">在 Web 服務中使用 `WebMethod` 屬性標示方法，以表示此方法應該可以透過 SOAP 通訊協定來呼叫。</span><span class="sxs-lookup"><span data-stu-id="2da26-151">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="2da26-152">如需詳細資訊，請參閱<xref:System.Web.Services.WebMethodAttribute>。</span><span class="sxs-lookup"><span data-stu-id="2da26-152">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
-   <span data-ttu-id="2da26-153">描述在與原生程式碼交互作用時，如何封送處理方法參數。</span><span class="sxs-lookup"><span data-stu-id="2da26-153">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="2da26-154">如需詳細資訊，請參閱<xref:System.Runtime.InteropServices.MarshalAsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="2da26-154">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>  
  
-   <span data-ttu-id="2da26-155">描述適用於類別、方法和介面的 COM 屬性。</span><span class="sxs-lookup"><span data-stu-id="2da26-155">Describing the COM properties for classes, methods, and interfaces.</span></span>  
  
-   <span data-ttu-id="2da26-156">使用 <xref:System.Runtime.InteropServices.DllImportAttribute> 類別呼叫 Unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="2da26-156">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>  
  
-   <span data-ttu-id="2da26-157">針對標題、版本、描述或商標等方面來描述您的組件。</span><span class="sxs-lookup"><span data-stu-id="2da26-157">Describing your assembly in terms of title, version, description, or trademark.</span></span>  
  
-   <span data-ttu-id="2da26-158">描述要將類別的哪些成員序列化以取得持續性。</span><span class="sxs-lookup"><span data-stu-id="2da26-158">Describing which members of a class to serialize for persistence.</span></span>  
  
-   <span data-ttu-id="2da26-159">描述如何基於 XML 序列化目的，在類別成員與 XML 節點之間進行對應。</span><span class="sxs-lookup"><span data-stu-id="2da26-159">Describing how to map between class members and XML nodes for XML serialization.</span></span>  
  
-   <span data-ttu-id="2da26-160">描述方法的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="2da26-160">Describing the security requirements for methods.</span></span>  
  
-   <span data-ttu-id="2da26-161">指定用來強制執行安全性的特性。</span><span class="sxs-lookup"><span data-stu-id="2da26-161">Specifying characteristics used to enforce security.</span></span>  
  
-   <span data-ttu-id="2da26-162">控制由 Just-In-Time (JIT) 編譯器所進行的最佳化，讓程式碼保持易於偵錯。</span><span class="sxs-lookup"><span data-stu-id="2da26-162">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>  
  
-   <span data-ttu-id="2da26-163">取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="2da26-163">Obtaining information about the caller to a method.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2da26-164">相關章節</span><span class="sxs-lookup"><span data-stu-id="2da26-164">Related Sections</span></span>  
 <span data-ttu-id="2da26-165">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="2da26-165">For more information, see:</span></span>  
  
-   [<span data-ttu-id="2da26-166">建立自訂屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2da26-166">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [<span data-ttu-id="2da26-167">使用反映存取屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2da26-167">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [<span data-ttu-id="2da26-168">如何：使用屬性建立 C/C++ 等位 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2da26-168">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [<span data-ttu-id="2da26-169">通用屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2da26-169">Common Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [<span data-ttu-id="2da26-170">呼叫端資訊 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2da26-170">Caller Information (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a><span data-ttu-id="2da26-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2da26-171">See Also</span></span>  
 <span data-ttu-id="2da26-172">[Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2da26-172">[Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2da26-173">[反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="2da26-173">[Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
 [<span data-ttu-id="2da26-174">屬性</span><span class="sxs-lookup"><span data-stu-id="2da26-174">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)

