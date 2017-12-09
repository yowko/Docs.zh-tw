---
title: "常見屬性 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4781e7ee60017455796d460d8d7bddb9f7c49676
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="35141-102">常見屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35141-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="35141-103">本主題說明在 Visual Basic 程式中最常用的屬性。</span><span class="sxs-lookup"><span data-stu-id="35141-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="35141-104">全域屬性</span><span class="sxs-lookup"><span data-stu-id="35141-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="35141-105">Obsolete 屬性</span><span class="sxs-lookup"><span data-stu-id="35141-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="35141-106">條件式屬性</span><span class="sxs-lookup"><span data-stu-id="35141-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="35141-107">呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="35141-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="35141-108">Visual Basic 屬性</span><span class="sxs-lookup"><span data-stu-id="35141-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <a name="Global"></a> <span data-ttu-id="35141-109">全域屬性</span><span class="sxs-lookup"><span data-stu-id="35141-109">Global Attributes</span></span>  
 <span data-ttu-id="35141-110">大部分屬性會套用至特定語言項目 (例如類別或方法)；不過，有些屬性是全域屬性，其套用至整個組件或模組。</span><span class="sxs-lookup"><span data-stu-id="35141-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="35141-111">例如，<xref:System.Reflection.AssemblyVersionAttribute> 屬性可以用來將版本資訊內嵌到組件，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="35141-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="35141-112">之後，任何全域屬性會出現在原始碼最上層`Imports`陳述式之前的任何類型、 模組或命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="35141-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="35141-113">全域屬性可以出現在多個原始程式檔中，但必須使用單一編譯階段編譯檔案。</span><span class="sxs-lookup"><span data-stu-id="35141-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="35141-114">Visual Basic 專案中，通常會處於 AssemblyInfo.vb 檔案 （檔案時自動建立 Visual Studio 中建立的專案） 的全域屬性。</span><span class="sxs-lookup"><span data-stu-id="35141-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="35141-115">組件屬性是提供組件相關資訊的值。</span><span class="sxs-lookup"><span data-stu-id="35141-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="35141-116">它們的分類如下：</span><span class="sxs-lookup"><span data-stu-id="35141-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="35141-117">組件識別屬性</span><span class="sxs-lookup"><span data-stu-id="35141-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="35141-118">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="35141-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="35141-119">組件資訊清單屬性</span><span class="sxs-lookup"><span data-stu-id="35141-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="35141-120">組件識別屬性</span><span class="sxs-lookup"><span data-stu-id="35141-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="35141-121">三個具有強式名稱 (如果適用) 的屬性會判斷組件的識別：名稱、版本與文化特性。</span><span class="sxs-lookup"><span data-stu-id="35141-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="35141-122">這些屬性會形成組件的完整名稱，且在程式碼中參考組件時需要用到。</span><span class="sxs-lookup"><span data-stu-id="35141-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="35141-123">您可以使用屬性來設定組件的版本和文化特性。</span><span class="sxs-lookup"><span data-stu-id="35141-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="35141-124">不過，名稱值乃是根據包含組件資訊清單的檔案來由編譯器、[組件資訊對話方塊](/visualstudio/ide/reference/assembly-information-dialog-box) 中的 Visual Studio IDE 或在建立組件時的組件連結器 (Al.exe) 所設定。</span><span class="sxs-lookup"><span data-stu-id="35141-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="35141-125"><xref:System.Reflection.AssemblyFlagsAttribute> 屬性指定組件的多個複本是否可以並存。</span><span class="sxs-lookup"><span data-stu-id="35141-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="35141-126">下表顯示識別屬性。</span><span class="sxs-lookup"><span data-stu-id="35141-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="35141-127">屬性</span><span class="sxs-lookup"><span data-stu-id="35141-127">Attribute</span></span>|<span data-ttu-id="35141-128">用途</span><span class="sxs-lookup"><span data-stu-id="35141-128">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="35141-129">完整描述組件的識別。</span><span class="sxs-lookup"><span data-stu-id="35141-129">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="35141-130">指定組件的版本。</span><span class="sxs-lookup"><span data-stu-id="35141-130">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="35141-131">指定組件所支援的文化特性。</span><span class="sxs-lookup"><span data-stu-id="35141-131">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="35141-132">指定是否支援在相同電腦上、相同處理程序中或相同應用程式定義域中並存執行組件。</span><span class="sxs-lookup"><span data-stu-id="35141-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="35141-133">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="35141-133">Informational Attributes</span></span>  
 <span data-ttu-id="35141-134">您可以使用資訊屬性，以提供組件其他的公司或產品資訊。</span><span class="sxs-lookup"><span data-stu-id="35141-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="35141-135">下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊屬性。</span><span class="sxs-lookup"><span data-stu-id="35141-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="35141-136">屬性</span><span class="sxs-lookup"><span data-stu-id="35141-136">Attribute</span></span>|<span data-ttu-id="35141-137">用途</span><span class="sxs-lookup"><span data-stu-id="35141-137">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="35141-138">定義自訂屬性，以指定組件資訊清單的產品名稱。</span><span class="sxs-lookup"><span data-stu-id="35141-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="35141-139">定義自訂屬性，以指定組件資訊清單的商標。</span><span class="sxs-lookup"><span data-stu-id="35141-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="35141-140">定義自訂屬性，以指定組件資訊清單的資訊版本。</span><span class="sxs-lookup"><span data-stu-id="35141-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="35141-141">定義自訂屬性，以指定組件資訊清單的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="35141-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="35141-142">定義自訂屬性，以指定組件資訊清單的版權。</span><span class="sxs-lookup"><span data-stu-id="35141-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="35141-143">指示編譯器使用 Win32 檔案版本資源的特定版本號碼。</span><span class="sxs-lookup"><span data-stu-id="35141-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="35141-144">表示組件是否符合 Common Language Specification (CLS) 規範。</span><span class="sxs-lookup"><span data-stu-id="35141-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="35141-145">組件資訊清單屬性。</span><span class="sxs-lookup"><span data-stu-id="35141-145">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="35141-146">您可以使用組件資訊清單屬性，在組件資訊清單中提供資訊。</span><span class="sxs-lookup"><span data-stu-id="35141-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="35141-147">這包括標題、描述、預設別名和組態。</span><span class="sxs-lookup"><span data-stu-id="35141-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="35141-148">下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊清單屬性。</span><span class="sxs-lookup"><span data-stu-id="35141-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="35141-149">屬性</span><span class="sxs-lookup"><span data-stu-id="35141-149">Attribute</span></span>|<span data-ttu-id="35141-150">用途</span><span class="sxs-lookup"><span data-stu-id="35141-150">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="35141-151">定義自訂屬性，以指定組件資訊清單的組件標題。</span><span class="sxs-lookup"><span data-stu-id="35141-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="35141-152">定義自訂屬性，以指定組件資訊清單的組件描述。</span><span class="sxs-lookup"><span data-stu-id="35141-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="35141-153">定義自訂屬性，以指定組件資訊清單的組件設定 (例如零售或偵錯)。</span><span class="sxs-lookup"><span data-stu-id="35141-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="35141-154">定義組件資訊清單的易記預設別名。</span><span class="sxs-lookup"><span data-stu-id="35141-154">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a> <span data-ttu-id="35141-155">Obsolete 屬性</span><span class="sxs-lookup"><span data-stu-id="35141-155">Obsolete Attribute</span></span>  
 <span data-ttu-id="35141-156">`Obsolete` 屬性會將程式實體標記為不再建議使用的標記。</span><span class="sxs-lookup"><span data-stu-id="35141-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="35141-157">每次使用標記為已淘汰的實體都會接著產生警告或錯誤 (視屬性的設定方式而定)。</span><span class="sxs-lookup"><span data-stu-id="35141-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="35141-158">例如: </span><span class="sxs-lookup"><span data-stu-id="35141-158">For example:</span></span>  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="35141-159">在此範例中，`Obsolete` 屬性會套用至 `A` 類別和 `B.OldMethod` 方法。</span><span class="sxs-lookup"><span data-stu-id="35141-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="35141-160">因為套用至 `B.OldMethod` 的屬性建構函式的第二個引數設為 `true`，所以這個方法會造成編譯器錯誤，而使用 `A` 類別則只會產生警告。</span><span class="sxs-lookup"><span data-stu-id="35141-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="35141-161">不過，呼叫 `B.NewMethod` 不會產生任何警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="35141-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="35141-162">提供為屬性建構函式的第一個引數的字串將會顯示為警告或錯誤的一部分。</span><span class="sxs-lookup"><span data-stu-id="35141-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="35141-163">例如，當您將它與先前的定義搭配使用時，下列程式碼會產生兩個警告和一個錯誤︰</span><span class="sxs-lookup"><span data-stu-id="35141-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="35141-164">會產生 `A` 類別的兩個警告︰一個用於宣告類別參考，一個則用於類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="35141-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="35141-165">可以使用沒有引數的 `Obsolete` 屬性，但包括項目為何已淘汰以及建議改使用之項目的說明。</span><span class="sxs-lookup"><span data-stu-id="35141-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="35141-166">`Obsolete` 屬性是單次使用屬性，並且可以套用至任何允許屬性的實體。</span><span class="sxs-lookup"><span data-stu-id="35141-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="35141-167">`Obsolete` 是 <xref:System.ObsoleteAttribute> 的別名。</span><span class="sxs-lookup"><span data-stu-id="35141-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a> <span data-ttu-id="35141-168">條件式屬性</span><span class="sxs-lookup"><span data-stu-id="35141-168">Conditional Attribute</span></span>  
 <span data-ttu-id="35141-169">`Conditional` 屬性會根據前置處理識別碼來執行方法。</span><span class="sxs-lookup"><span data-stu-id="35141-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="35141-170">`Conditional` 屬性是 <xref:System.Diagnostics.ConditionalAttribute> 的別名，而且可以套用至方法或屬性類別。</span><span class="sxs-lookup"><span data-stu-id="35141-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="35141-171">在此範例中，`Conditional` 會套用至方法，以啟用或停用程式特定診斷資訊的顯示︰</span><span class="sxs-lookup"><span data-stu-id="35141-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="35141-172">如果未定義 `TRACE_ON` 識別碼，則不會顯示任何追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="35141-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="35141-173">`Conditional` 屬性通常與 `DEBUG` 識別碼搭配使用，以啟用偵錯組建 (而非版本組建) 的追蹤和記錄功能，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="35141-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="35141-174">呼叫標記為條件的方法時，所指定前置處理符號的存在與否會決定包含還是省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="35141-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="35141-175">如果定義符號，則會包括呼叫；否則會省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="35141-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="35141-176">使用 `Conditional` 是 `#if…#endif` 區塊內封入方法的更乾淨、更明確且不容易出錯的替代方式，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="35141-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="35141-177">條件式方法必須是類別或結構宣告中的方法，而且不能有傳回值。</span><span class="sxs-lookup"><span data-stu-id="35141-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="35141-178">使用多個識別碼</span><span class="sxs-lookup"><span data-stu-id="35141-178">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="35141-179">如果方法有多個 `Conditional` 屬性，則在定義至少一個條件式符號時會包括方法的呼叫 (換句話說，會使用 OR 運算子以邏輯方式將符號連結在一起)。</span><span class="sxs-lookup"><span data-stu-id="35141-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="35141-180">在此範例中，如果有 `A` 或 `B`，則會導致方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="35141-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="35141-181">若要達到使用 AND 運算子以邏輯方式連結符號的效果，您可以定義序列條件式方法。</span><span class="sxs-lookup"><span data-stu-id="35141-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="35141-182">例如，只有在同時定義 `A` 和 `B` 時，才會執行下面的第二個方法：</span><span class="sxs-lookup"><span data-stu-id="35141-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="35141-183">搭配使用條件式與屬性類別</span><span class="sxs-lookup"><span data-stu-id="35141-183">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="35141-184">`Conditional` 屬性也可以套用至屬性類別定義。</span><span class="sxs-lookup"><span data-stu-id="35141-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="35141-185">在此範例中，如果定義 DEBUG，則自訂屬性 `Documentation` 只會將資訊新增至中繼資料。</span><span class="sxs-lookup"><span data-stu-id="35141-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <a name="CallerInfo"></a> <span data-ttu-id="35141-186">呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="35141-186">Caller Info Attributes</span></span>  
 <span data-ttu-id="35141-187">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="35141-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="35141-188">您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="35141-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="35141-189">若要取得成員呼叫端資訊，請使用套用至選擇性參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="35141-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="35141-190">每個選擇性參數都會指定預設值。</span><span class="sxs-lookup"><span data-stu-id="35141-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="35141-191">下表列出 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中定義的 Caller Info 屬性：</span><span class="sxs-lookup"><span data-stu-id="35141-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="35141-192">屬性</span><span class="sxs-lookup"><span data-stu-id="35141-192">Attribute</span></span>|<span data-ttu-id="35141-193">描述</span><span class="sxs-lookup"><span data-stu-id="35141-193">Description</span></span>|<span data-ttu-id="35141-194">類型</span><span class="sxs-lookup"><span data-stu-id="35141-194">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="35141-195">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="35141-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="35141-196">這是編譯時期的路徑。</span><span class="sxs-lookup"><span data-stu-id="35141-196">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="35141-197">原始程式檔中呼叫方法的行號。</span><span class="sxs-lookup"><span data-stu-id="35141-197">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="35141-198">呼叫端的方法名稱或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="35141-198">Method name or property name of the caller.</span></span> <span data-ttu-id="35141-199">如需詳細資訊，請參閱[呼叫端資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="35141-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="35141-200">如需 Caller Info 屬性的詳細資訊，請參閱[呼叫端資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="35141-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <a name="VB"></a><span data-ttu-id="35141-201">Visual Basic 屬性</span><span class="sxs-lookup"><span data-stu-id="35141-201">Visual Basic Attributes</span></span>  
 <span data-ttu-id="35141-202">下表列出 Visual Basic 特有的屬性。</span><span class="sxs-lookup"><span data-stu-id="35141-202">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="35141-203">屬性</span><span class="sxs-lookup"><span data-stu-id="35141-203">Attribute</span></span>|<span data-ttu-id="35141-204">用途</span><span class="sxs-lookup"><span data-stu-id="35141-204">Purpose</span></span>|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="35141-205">表示編譯器應該為 COM 物件公開的類別。</span><span class="sxs-lookup"><span data-stu-id="35141-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="35141-206">允許存取使用只限定性條件該模組所需的模組成員。</span><span class="sxs-lookup"><span data-stu-id="35141-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="35141-207">使用結構中指定固定長度字串的大小，使用檔案輸入和輸出函式。</span><span class="sxs-lookup"><span data-stu-id="35141-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="35141-208">使用結構中指定固定陣列的大小，使用檔案輸入和輸出函式。</span><span class="sxs-lookup"><span data-stu-id="35141-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="35141-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="35141-209">COMClassAttribute</span></span>  
 <span data-ttu-id="35141-210">使用`COMClassAttribute`簡化從 Visual Basic 建立 COM 元件的程序。</span><span class="sxs-lookup"><span data-stu-id="35141-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="35141-211">COM 物件會從.NET Framework 組件，並沒有差異很大`COMClassAttribute`，您必須遵循一些步驟來產生 Visual basic 的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="35141-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="35141-212">針對類別標記為`COMClassAttribute`，編譯器會自動執行其中許多步驟。</span><span class="sxs-lookup"><span data-stu-id="35141-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="35141-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="35141-213">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="35141-214">使用`HideModuleNameAttribute`以允許存取的使用只限定性條件該模組所需的模組成員。</span><span class="sxs-lookup"><span data-stu-id="35141-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="35141-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="35141-215">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="35141-216">使用`VBFixedStringAttribute`強制 Visual Basic 來建立固定長度字串。</span><span class="sxs-lookup"><span data-stu-id="35141-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="35141-217">根據預設的可變長度的字串是，將字串儲存至檔案時，此屬性才有用。</span><span class="sxs-lookup"><span data-stu-id="35141-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="35141-218">下列程式碼示範：</span><span class="sxs-lookup"><span data-stu-id="35141-218">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="35141-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="35141-219">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="35141-220">使用`VBFixedArrayAttribute`來宣告陣列的大小固定的。</span><span class="sxs-lookup"><span data-stu-id="35141-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="35141-221">例如 Visual Basic 字串陣列是預設的可變長度。</span><span class="sxs-lookup"><span data-stu-id="35141-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="35141-222">這個屬性會序列化，或將資料寫入至檔案時很有用。</span><span class="sxs-lookup"><span data-stu-id="35141-222">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35141-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35141-223">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="35141-224">Visual Basic 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="35141-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="35141-225">屬性</span><span class="sxs-lookup"><span data-stu-id="35141-225">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="35141-226">反映 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35141-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="35141-227">使用反映存取屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35141-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
