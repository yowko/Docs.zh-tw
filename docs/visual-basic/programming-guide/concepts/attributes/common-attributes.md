---
title: "常見屬性 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9adb5cb378701c8d06a3fa28bad44dc857026b5a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="a6e81-102">常見屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6e81-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="a6e81-103">本主題說明 Visual Basic 程式中最常用的屬性。</span><span class="sxs-lookup"><span data-stu-id="a6e81-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="a6e81-104">全域屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="a6e81-105">過時的屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="a6e81-106">條件式屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="a6e81-107">呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="a6e81-108">Visual Basic 屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <span data-ttu-id="a6e81-109"><a name="Global"></a>全域屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-109"><a name="Global"></a> Global Attributes</span></span>  
 <span data-ttu-id="a6e81-110">大部分的屬性會套用至特定語言項目，例如類別或方法。不過，有些屬性是全域 — 它們適用於整個組件或模組。</span><span class="sxs-lookup"><span data-stu-id="a6e81-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="a6e81-111">例如，<xref:System.Reflection.AssemblyVersionAttribute>屬性可以用來內嵌為組件，就像這樣的版本資訊︰</xref:System.Reflection.AssemblyVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="a6e81-112">之後，任何全域屬性會出現在原始碼最上層`Imports`陳述式之前的任何型別、 模組或命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="a6e81-112">Global attributes appear in the source code after any top-level`Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="a6e81-113">全域屬性可以出現在多個原始程式檔，但必須在單一編譯階段編譯檔案。</span><span class="sxs-lookup"><span data-stu-id="a6e81-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="a6e81-114">Visual Basic 專案中，全域屬性通常會放在 AssemblyInfo.vb 檔案 （檔案時自動建立 Visual Studio 中建立專案）。</span><span class="sxs-lookup"><span data-stu-id="a6e81-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="a6e81-115">組件屬性是提供組件相關資訊的值。</span><span class="sxs-lookup"><span data-stu-id="a6e81-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="a6e81-116">它們可分成下列類別︰</span><span class="sxs-lookup"><span data-stu-id="a6e81-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="a6e81-117">組件的識別屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="a6e81-118">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="a6e81-119">組件資訊清單屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="a6e81-120">組件識別屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="a6e81-121">（以強式名稱，如果適用的話） 的三個屬性會決定組件的識別︰ 名稱、 版本和文化特性。</span><span class="sxs-lookup"><span data-stu-id="a6e81-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="a6e81-122">這些屬性會形成組件的完整名稱，並在程式碼中參考它時所需。</span><span class="sxs-lookup"><span data-stu-id="a6e81-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="a6e81-123">您可以設定組件的版本和文化特性使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="a6e81-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="a6e81-124">不過，編譯器，Visual Studio IDE 中設定的名稱值[組件資訊對話方塊](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box)，或組件連結器 (Al.exe) 建立組件時，根據包含組件資訊清單的檔案。</span><span class="sxs-lookup"><span data-stu-id="a6e81-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="a6e81-125"><xref:System.Reflection.AssemblyFlagsAttribute>屬性會指定是否可以並存組件的多個副本。</xref:System.Reflection.AssemblyFlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="a6e81-126">下表顯示識別屬性。</span><span class="sxs-lookup"><span data-stu-id="a6e81-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="a6e81-127">屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-127">Attribute</span></span>|<span data-ttu-id="a6e81-128">用途</span><span class="sxs-lookup"><span data-stu-id="a6e81-128">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="a6e81-129"><xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="a6e81-129"><xref:System.Reflection.AssemblyName></span></span>|<span data-ttu-id="a6e81-130">完整描述組件的識別。</span><span class="sxs-lookup"><span data-stu-id="a6e81-130">Fully describes the identity of an assembly.</span></span>|  
|<span data-ttu-id="a6e81-131"><xref:System.Reflection.AssemblyVersionAttribute></xref:System.Reflection.AssemblyVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-131"><xref:System.Reflection.AssemblyVersionAttribute></span></span>|<span data-ttu-id="a6e81-132">指定組件的版本。</span><span class="sxs-lookup"><span data-stu-id="a6e81-132">Specifies the version of an assembly.</span></span>|  
|<span data-ttu-id="a6e81-133"><xref:System.Reflection.AssemblyCultureAttribute></xref:System.Reflection.AssemblyCultureAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-133"><xref:System.Reflection.AssemblyCultureAttribute></span></span>|<span data-ttu-id="a6e81-134">指定組件所支援的文化特性。</span><span class="sxs-lookup"><span data-stu-id="a6e81-134">Specifies which culture the assembly supports.</span></span>|  
|<span data-ttu-id="a6e81-135"><xref:System.Reflection.AssemblyFlagsAttribute></xref:System.Reflection.AssemblyFlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-135"><xref:System.Reflection.AssemblyFlagsAttribute></span></span>|<span data-ttu-id="a6e81-136">指定組件是否支援在同一部電腦，在相同的程序，或在相同的應用程式定義域中的並存執行。</span><span class="sxs-lookup"><span data-stu-id="a6e81-136">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="a6e81-137">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-137">Informational Attributes</span></span>  
 <span data-ttu-id="a6e81-138">您可以使用資訊屬性，以提供組件其他的公司或產品資訊。</span><span class="sxs-lookup"><span data-stu-id="a6e81-138">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="a6e81-139">下表顯示資訊的屬性中定義<xref:System.Reflection?displayProperty=fullName>命名空間。</xref:System.Reflection?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a6e81-139">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="a6e81-140">屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-140">Attribute</span></span>|<span data-ttu-id="a6e81-141">用途</span><span class="sxs-lookup"><span data-stu-id="a6e81-141">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="a6e81-142"><xref:System.Reflection.AssemblyProductAttribute></xref:System.Reflection.AssemblyProductAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-142"><xref:System.Reflection.AssemblyProductAttribute></span></span>|<span data-ttu-id="a6e81-143">定義自訂屬性來指定組件資訊清單的產品名稱。</span><span class="sxs-lookup"><span data-stu-id="a6e81-143">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<span data-ttu-id="a6e81-144"><xref:System.Reflection.AssemblyTrademarkAttribute></xref:System.Reflection.AssemblyTrademarkAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-144"><xref:System.Reflection.AssemblyTrademarkAttribute></span></span>|<span data-ttu-id="a6e81-145">定義自訂屬性來指定組件資訊清單的商標。</span><span class="sxs-lookup"><span data-stu-id="a6e81-145">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<span data-ttu-id="a6e81-146"><xref:System.Reflection.AssemblyInformationalVersionAttribute></xref:System.Reflection.AssemblyInformationalVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-146"><xref:System.Reflection.AssemblyInformationalVersionAttribute></span></span>|<span data-ttu-id="a6e81-147">定義自訂屬性來指定組件資訊清單的資訊版本。</span><span class="sxs-lookup"><span data-stu-id="a6e81-147">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<span data-ttu-id="a6e81-148"><xref:System.Reflection.AssemblyCompanyAttribute></xref:System.Reflection.AssemblyCompanyAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-148"><xref:System.Reflection.AssemblyCompanyAttribute></span></span>|<span data-ttu-id="a6e81-149">定義自訂屬性來指定組件資訊清單的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="a6e81-149">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<span data-ttu-id="a6e81-150"><xref:System.Reflection.AssemblyCopyrightAttribute></xref:System.Reflection.AssemblyCopyrightAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-150"><xref:System.Reflection.AssemblyCopyrightAttribute></span></span>|<span data-ttu-id="a6e81-151">定義自訂屬性來指定組件資訊清單的著作權。</span><span class="sxs-lookup"><span data-stu-id="a6e81-151">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<span data-ttu-id="a6e81-152"><xref:System.Reflection.AssemblyFileVersionAttribute></xref:System.Reflection.AssemblyFileVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-152"><xref:System.Reflection.AssemblyFileVersionAttribute></span></span>|<span data-ttu-id="a6e81-153">會指示編譯器使用 Win32 檔案版本資源的特定版本號碼。</span><span class="sxs-lookup"><span data-stu-id="a6e81-153">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<span data-ttu-id="a6e81-154"><xref:System.CLSCompliantAttribute></xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-154"><xref:System.CLSCompliantAttribute></span></span>|<span data-ttu-id="a6e81-155">表示組件是否使用 Common Language Specification (CLS) 相容。</span><span class="sxs-lookup"><span data-stu-id="a6e81-155">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="a6e81-156">組件資訊清單屬性。</span><span class="sxs-lookup"><span data-stu-id="a6e81-156">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="a6e81-157">您可以使用組件資訊清單屬性在組件資訊清單中提供資訊。</span><span class="sxs-lookup"><span data-stu-id="a6e81-157">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="a6e81-158">這包括標題、 描述、 預設別名和組態。</span><span class="sxs-lookup"><span data-stu-id="a6e81-158">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="a6e81-159">下表顯示組件資訊清單屬性定義於<xref:System.Reflection?displayProperty=fullName>命名空間。</xref:System.Reflection?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a6e81-159">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="a6e81-160">屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-160">Attribute</span></span>|<span data-ttu-id="a6e81-161">用途</span><span class="sxs-lookup"><span data-stu-id="a6e81-161">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="a6e81-162"><xref:System.Reflection.AssemblyTitleAttribute></xref:System.Reflection.AssemblyTitleAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-162"><xref:System.Reflection.AssemblyTitleAttribute></span></span>|<span data-ttu-id="a6e81-163">定義自訂屬性來指定組件資訊清單的組件標題。</span><span class="sxs-lookup"><span data-stu-id="a6e81-163">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<span data-ttu-id="a6e81-164"><xref:System.Reflection.AssemblyDescriptionAttribute></xref:System.Reflection.AssemblyDescriptionAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-164"><xref:System.Reflection.AssemblyDescriptionAttribute></span></span>|<span data-ttu-id="a6e81-165">定義自訂屬性來指定組件資訊清單的組件描述。</span><span class="sxs-lookup"><span data-stu-id="a6e81-165">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<span data-ttu-id="a6e81-166"><xref:System.Reflection.AssemblyConfigurationAttribute></xref:System.Reflection.AssemblyConfigurationAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-166"><xref:System.Reflection.AssemblyConfigurationAttribute></span></span>|<span data-ttu-id="a6e81-167">定義自訂屬性來指定 （例如正式版本或偵錯） 的組件組態的組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="a6e81-167">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<span data-ttu-id="a6e81-168"><xref:System.Reflection.AssemblyDefaultAliasAttribute></xref:System.Reflection.AssemblyDefaultAliasAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-168"><xref:System.Reflection.AssemblyDefaultAliasAttribute></span></span>|<span data-ttu-id="a6e81-169">定義組件資訊清單的好記的預設別名</span><span class="sxs-lookup"><span data-stu-id="a6e81-169">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <span data-ttu-id="a6e81-170"><a name="Obsolete"></a>過時的屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-170"><a name="Obsolete"></a> Obsolete Attribute</span></span>  
 <span data-ttu-id="a6e81-171">`Obsolete`屬性標記為不再建議使用的程式實體。</span><span class="sxs-lookup"><span data-stu-id="a6e81-171">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="a6e81-172">每次使用的實體標記為過時接著會產生警告或錯誤，視屬性的設定方式而定。</span><span class="sxs-lookup"><span data-stu-id="a6e81-172">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="a6e81-173">例如: </span><span class="sxs-lookup"><span data-stu-id="a6e81-173">For example:</span></span>  
  
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
  
 <span data-ttu-id="a6e81-174">在此範例中`Obsolete`屬性套用至類別`A`和方法`B.OldMethod`。</span><span class="sxs-lookup"><span data-stu-id="a6e81-174">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="a6e81-175">因為屬性建構函式的第二個引數套用至`B.OldMethod`設為`true`，這個方法會造成編譯器錯誤，而使用類別`A`將只是產生警告。</span><span class="sxs-lookup"><span data-stu-id="a6e81-175">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="a6e81-176">呼叫`B.NewMethod`，不過，會產生任何警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="a6e81-176">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="a6e81-177">提供為屬性建構函式的第一個引數的字串將顯示為警告或錯誤的一部分。</span><span class="sxs-lookup"><span data-stu-id="a6e81-177">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="a6e81-178">例如，當您使用先前的定義，下列程式碼會產生兩個警告和一個錯誤︰</span><span class="sxs-lookup"><span data-stu-id="a6e81-178">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="a6e81-179">類別的兩個警告`A`產生︰ 一個用於類別參考宣告，一個類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="a6e81-179">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="a6e81-180">`Obsolete`屬性可以用不含引數，但說明的原因包括項目已經過時，建議改用。</span><span class="sxs-lookup"><span data-stu-id="a6e81-180">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="a6e81-181">`Obsolete`屬性的單一用途的屬性，並可套用至任何允許屬性的實體。</span><span class="sxs-lookup"><span data-stu-id="a6e81-181">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="a6e81-182">`Obsolete`<xref:System.ObsoleteAttribute>.</xref:System.ObsoleteAttribute>的別名</span><span class="sxs-lookup"><span data-stu-id="a6e81-182">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <span data-ttu-id="a6e81-183"><a name="Conditional"></a>條件式屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-183"><a name="Conditional"></a> Conditional Attribute</span></span>  
 <span data-ttu-id="a6e81-184">`Conditional`屬性，讓方法的執行取決於前置處理識別項。</span><span class="sxs-lookup"><span data-stu-id="a6e81-184">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="a6e81-185">`Conditional`屬性為其別名<xref:System.Diagnostics.ConditionalAttribute>，而且可以套用至方法或屬性類別</xref:System.Diagnostics.ConditionalAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-185">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="a6e81-186">在此範例中，`Conditional`套用至方法，以啟用或停用程式特定的診斷資訊的顯示︰</span><span class="sxs-lookup"><span data-stu-id="a6e81-186">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="a6e81-187">如果`TRACE_ON`識別碼未定義時，將會顯示任何追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="a6e81-187">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="a6e81-188">`Conditional`屬性通常用於`DEBUG`識別碼可啟用追蹤和記錄功能偵錯組建，但是不能在發行組建，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="a6e81-188">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="a6e81-189">呼叫方法，標示為條件時，所指定的前置處理符號存在會決定包含或省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="a6e81-189">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="a6e81-190">如果定義的符號時，呼叫就是包含在內。否則，呼叫會省略。</span><span class="sxs-lookup"><span data-stu-id="a6e81-190">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="a6e81-191">使用`Conditional`是更乾淨更優雅且較不容易出錯的替代方案封入方法內`#if…#endif`區塊，就像這樣︰</span><span class="sxs-lookup"><span data-stu-id="a6e81-191">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="a6e81-192">條件式方法必須是類別或結構的宣告中的方法，並不能傳回的值。</span><span class="sxs-lookup"><span data-stu-id="a6e81-192">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="a6e81-193">使用多個識別項</span><span class="sxs-lookup"><span data-stu-id="a6e81-193">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="a6e81-194">如果方法具有多個`Conditional`屬性、 方法的呼叫會包括至少一個條件式的符號定義 （亦即，符號會以邏輯方式連結在一起使用 OR 運算子）。</span><span class="sxs-lookup"><span data-stu-id="a6e81-194">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="a6e81-195">在此範例中的其中一個存在`A`或`B`方法呼叫會導致︰</span><span class="sxs-lookup"><span data-stu-id="a6e81-195">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="a6e81-196">若要達到以邏輯方式將符號連結使用 AND 運算子的效果，您可以定義序列的條件式方法。</span><span class="sxs-lookup"><span data-stu-id="a6e81-196">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="a6e81-197">例如，下列第二個方法才會執行這兩個`A`和`B`所定義︰</span><span class="sxs-lookup"><span data-stu-id="a6e81-197">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="a6e81-198">使用條件式屬性類別</span><span class="sxs-lookup"><span data-stu-id="a6e81-198">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="a6e81-199">`Conditional`屬性也可以套用至屬性的類別定義。</span><span class="sxs-lookup"><span data-stu-id="a6e81-199">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="a6e81-200">在此範例中，自訂屬性`Documentation`只將資訊加入中繼資料如果定義偵錯。</span><span class="sxs-lookup"><span data-stu-id="a6e81-200">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
##  <span data-ttu-id="a6e81-201"><a name="CallerInfo"></a>呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-201"><a name="CallerInfo"></a> Caller Info Attributes</span></span>  
 <span data-ttu-id="a6e81-202">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="a6e81-202">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="a6e81-203">您可以取得原始程式碼的檔案路徑、 原始程式碼和呼叫端的成員名稱中的行號。</span><span class="sxs-lookup"><span data-stu-id="a6e81-203">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="a6e81-204">若要取得成員呼叫端資訊，您可以使用套用至選擇性參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="a6e81-204">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="a6e81-205">每個選擇性參數指定預設值。</span><span class="sxs-lookup"><span data-stu-id="a6e81-205">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="a6e81-206">下表列出中所定義的 Caller Info 屬性<xref:System.Runtime.CompilerServices?displayProperty=fullName>命名空間︰</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a6e81-206">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="a6e81-207">屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-207">Attribute</span></span>|<span data-ttu-id="a6e81-208">描述</span><span class="sxs-lookup"><span data-stu-id="a6e81-208">Description</span></span>|<span data-ttu-id="a6e81-209">類型</span><span class="sxs-lookup"><span data-stu-id="a6e81-209">Type</span></span>|  
|---|---|---|  
|<span data-ttu-id="a6e81-210"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-210"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span></span>|<span data-ttu-id="a6e81-211">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="a6e81-211">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="a6e81-212">這是在編譯時期的路徑。</span><span class="sxs-lookup"><span data-stu-id="a6e81-212">This is the path at compile time.</span></span>|`String`|  
|<span data-ttu-id="a6e81-213"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-213"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span></span>|<span data-ttu-id="a6e81-214">呼叫此方法的原始程式檔中的行號。</span><span class="sxs-lookup"><span data-stu-id="a6e81-214">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<span data-ttu-id="a6e81-215"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-215"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span></span>|<span data-ttu-id="a6e81-216">方法名稱或呼叫端的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="a6e81-216">Method name or property name of the caller.</span></span> <span data-ttu-id="a6e81-217">如需詳細資訊，請參閱[呼叫端資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="a6e81-217">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="a6e81-218">如需 Caller Info 屬性的詳細資訊，請參閱[呼叫端資訊 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="a6e81-218">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <span data-ttu-id="a6e81-219"><a name="VB"></a>Visual Basic 屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-219"><a name="VB"></a> Visual Basic Attributes</span></span>  
 <span data-ttu-id="a6e81-220">下表列出可針對 Visual Basic 的屬性。</span><span class="sxs-lookup"><span data-stu-id="a6e81-220">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="a6e81-221">屬性</span><span class="sxs-lookup"><span data-stu-id="a6e81-221">Attribute</span></span>|<span data-ttu-id="a6e81-222">用途</span><span class="sxs-lookup"><span data-stu-id="a6e81-222">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="a6e81-223"><xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-223"><xref:Microsoft.VisualBasic.ComClassAttribute></span></span>|<span data-ttu-id="a6e81-224">指示編譯器應該為 COM 物件公開的類別。</span><span class="sxs-lookup"><span data-stu-id="a6e81-224">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<span data-ttu-id="a6e81-225"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></xref:Microsoft.VisualBasic.HideModuleNameAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-225"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></span></span>|<span data-ttu-id="a6e81-226">可讓您使用只限定性條件所需的模組存取模組成員。</span><span class="sxs-lookup"><span data-stu-id="a6e81-226">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<span data-ttu-id="a6e81-227"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></xref:Microsoft.VisualBasic.VBFixedStringAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-227"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></span></span>|<span data-ttu-id="a6e81-228">使用結構中指定的固定長度字串大小，檔案輸入和輸出函式。</span><span class="sxs-lookup"><span data-stu-id="a6e81-228">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<span data-ttu-id="a6e81-229"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-229"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span></span>|<span data-ttu-id="a6e81-230">使用結構中指定固定陣列的大小，檔案輸入和輸出函式。</span><span class="sxs-lookup"><span data-stu-id="a6e81-230">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="a6e81-231">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="a6e81-231">COMClassAttribute</span></span>  
 <span data-ttu-id="a6e81-232">使用`COMClassAttribute`來簡化從 Visual Basic 建立 COM 元件的程序。</span><span class="sxs-lookup"><span data-stu-id="a6e81-232">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="a6e81-233">COM 物件會從.NET Framework 組件，而大幅不同`COMClassAttribute`，您必須遵循幾個步驟來產生 Visual basic 的 COM 物件。</span><span class="sxs-lookup"><span data-stu-id="a6e81-233">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="a6e81-234">對於類別標記與`COMClassAttribute`，編譯器會自動執行許多這些步驟。</span><span class="sxs-lookup"><span data-stu-id="a6e81-234">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="a6e81-235">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="a6e81-235">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="a6e81-236">使用`HideModuleNameAttribute`以允許存取的使用只限定性條件模組所需的模組成員。</span><span class="sxs-lookup"><span data-stu-id="a6e81-236">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="a6e81-237">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="a6e81-237">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="a6e81-238">使用`VBFixedStringAttribute`強制 Visual Basic 來建立固定長度字串。</span><span class="sxs-lookup"><span data-stu-id="a6e81-238">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="a6e81-239">字串具有可變長度，根據預設，並將字串儲存至檔案時，這個屬性很有用。</span><span class="sxs-lookup"><span data-stu-id="a6e81-239">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="a6e81-240">下列程式碼示範︰</span><span class="sxs-lookup"><span data-stu-id="a6e81-240">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="a6e81-241">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="a6e81-241">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="a6e81-242">使用`VBFixedArrayAttribute`來宣告為固定大小的陣列。</span><span class="sxs-lookup"><span data-stu-id="a6e81-242">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="a6e81-243">像 Visual Basic 字串陣列是預設的可變長度。</span><span class="sxs-lookup"><span data-stu-id="a6e81-243">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="a6e81-244">這個屬性會序列化，或將資料寫入至檔案時很有用。</span><span class="sxs-lookup"><span data-stu-id="a6e81-244">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e81-245">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6e81-245">See Also</span></span>  
 <span data-ttu-id="a6e81-246"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="a6e81-246"><xref:System.Reflection></span></span>   
 <span data-ttu-id="a6e81-247"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="a6e81-247"><xref:System.Attribute></span></span>   
<span data-ttu-id="a6e81-248"> [Visual Basic 程式設計指南](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a6e81-248"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="a6e81-249"> [屬性](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="a6e81-249"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="a6e81-250"> [反映 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="a6e81-250"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="a6e81-251"> [使用反映 (Visual Basic) 存取屬性](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="a6e81-251"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
