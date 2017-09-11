---
title: "常見屬性 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 1dca50ce4e31bd62436f18096e4ea6830e22e87c
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="common-attributes-c"></a><span data-ttu-id="96687-102">常見屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="96687-102">Common Attributes (C#)</span></span>
<span data-ttu-id="96687-103">本主題描述最常在 C# 程式中使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="96687-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
-   [<span data-ttu-id="96687-104">全域屬性</span><span class="sxs-lookup"><span data-stu-id="96687-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="96687-105">Obsolete 屬性</span><span class="sxs-lookup"><span data-stu-id="96687-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="96687-106">條件式屬性</span><span class="sxs-lookup"><span data-stu-id="96687-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="96687-107">呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="96687-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
##  <span data-ttu-id="96687-108"><a name="Global"></a> 全域屬性</span><span class="sxs-lookup"><span data-stu-id="96687-108"><a name="Global"></a> Global Attributes</span></span>  
 <span data-ttu-id="96687-109">大部分屬性會套用至特定語言項目 (例如類別或方法)；不過，有些屬性是全域屬性，其套用至整個組件或模組。</span><span class="sxs-lookup"><span data-stu-id="96687-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="96687-110">例如，<xref:System.Reflection.AssemblyVersionAttribute> 屬性可以用來將版本資訊內嵌到組件，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="96687-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="96687-111">全域屬性會出現在原始程式碼的任何最上層 `using` 指示詞後面，以及任何類型、模組或命名空間宣告前面。</span><span class="sxs-lookup"><span data-stu-id="96687-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="96687-112">全域屬性可以出現在多個原始程式檔中，但必須使用單一編譯階段編譯檔案。</span><span class="sxs-lookup"><span data-stu-id="96687-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="96687-113">在 C# 專案中，全域屬性會放在 AssemblyInfo.cs 檔案中。</span><span class="sxs-lookup"><span data-stu-id="96687-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="96687-114">組件屬性是提供組件相關資訊的值。</span><span class="sxs-lookup"><span data-stu-id="96687-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="96687-115">它們的分類如下：</span><span class="sxs-lookup"><span data-stu-id="96687-115">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="96687-116">組件識別屬性</span><span class="sxs-lookup"><span data-stu-id="96687-116">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="96687-117">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="96687-117">Informational attributes</span></span>  
  
-   <span data-ttu-id="96687-118">組件資訊清單屬性</span><span class="sxs-lookup"><span data-stu-id="96687-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="96687-119">組件識別屬性</span><span class="sxs-lookup"><span data-stu-id="96687-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="96687-120">三個具有強式名稱 (如果適用) 的屬性會判斷組件的識別：名稱、版本與文化特性。</span><span class="sxs-lookup"><span data-stu-id="96687-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="96687-121">這些屬性會形成組件的完整名稱，且在程式碼中參考組件時需要用到。</span><span class="sxs-lookup"><span data-stu-id="96687-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="96687-122">您可以使用屬性來設定組件的版本和文化特性。</span><span class="sxs-lookup"><span data-stu-id="96687-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="96687-123">不過，名稱值乃是根據包含組件資訊清單的檔案來由編譯器、[組件資訊對話方塊](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box) 中的 Visual Studio IDE 或在建立組件時的組件連結器 (Al.exe) 所設定。</span><span class="sxs-lookup"><span data-stu-id="96687-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="96687-124"><xref:System.Reflection.AssemblyFlagsAttribute> 屬性指定是否可以讓組件的多個複本並存。</span><span class="sxs-lookup"><span data-stu-id="96687-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="96687-125">下表顯示識別屬性。</span><span class="sxs-lookup"><span data-stu-id="96687-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="96687-126">屬性</span><span class="sxs-lookup"><span data-stu-id="96687-126">Attribute</span></span>|<span data-ttu-id="96687-127">用途</span><span class="sxs-lookup"><span data-stu-id="96687-127">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="96687-128"><xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="96687-128"><xref:System.Reflection.AssemblyName></span></span>|<span data-ttu-id="96687-129">完整描述組件的識別。</span><span class="sxs-lookup"><span data-stu-id="96687-129">Fully describes the identity of an assembly.</span></span>|  
|<span data-ttu-id="96687-130"><xref:System.Reflection.AssemblyVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-130"><xref:System.Reflection.AssemblyVersionAttribute></span></span>|<span data-ttu-id="96687-131">指定組件的版本。</span><span class="sxs-lookup"><span data-stu-id="96687-131">Specifies the version of an assembly.</span></span>|  
|<span data-ttu-id="96687-132"><xref:System.Reflection.AssemblyCultureAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-132"><xref:System.Reflection.AssemblyCultureAttribute></span></span>|<span data-ttu-id="96687-133">指定組件所支援的文化特性。</span><span class="sxs-lookup"><span data-stu-id="96687-133">Specifies which culture the assembly supports.</span></span>|  
|<span data-ttu-id="96687-134"><xref:System.Reflection.AssemblyFlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-134"><xref:System.Reflection.AssemblyFlagsAttribute></span></span>|<span data-ttu-id="96687-135">指定是否支援在相同電腦上、相同處理程序中或相同應用程式定義域中並存執行組件。</span><span class="sxs-lookup"><span data-stu-id="96687-135">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="96687-136">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="96687-136">Informational Attributes</span></span>  
 <span data-ttu-id="96687-137">您可以使用資訊屬性，以提供組件其他的公司或產品資訊。</span><span class="sxs-lookup"><span data-stu-id="96687-137">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="96687-138">下表顯示 <xref:System.Reflection?displayProperty=fullName> 命名空間中定義的資訊屬性。</span><span class="sxs-lookup"><span data-stu-id="96687-138">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="96687-139">屬性</span><span class="sxs-lookup"><span data-stu-id="96687-139">Attribute</span></span>|<span data-ttu-id="96687-140">用途</span><span class="sxs-lookup"><span data-stu-id="96687-140">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="96687-141"><xref:System.Reflection.AssemblyProductAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-141"><xref:System.Reflection.AssemblyProductAttribute></span></span>|<span data-ttu-id="96687-142">定義自訂屬性，以指定組件資訊清單的產品名稱。</span><span class="sxs-lookup"><span data-stu-id="96687-142">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<span data-ttu-id="96687-143"><xref:System.Reflection.AssemblyTrademarkAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-143"><xref:System.Reflection.AssemblyTrademarkAttribute></span></span>|<span data-ttu-id="96687-144">定義自訂屬性，以指定組件資訊清單的商標。</span><span class="sxs-lookup"><span data-stu-id="96687-144">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<span data-ttu-id="96687-145"><xref:System.Reflection.AssemblyInformationalVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-145"><xref:System.Reflection.AssemblyInformationalVersionAttribute></span></span>|<span data-ttu-id="96687-146">定義自訂屬性，以指定組件資訊清單的資訊版本。</span><span class="sxs-lookup"><span data-stu-id="96687-146">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<span data-ttu-id="96687-147"><xref:System.Reflection.AssemblyCompanyAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-147"><xref:System.Reflection.AssemblyCompanyAttribute></span></span>|<span data-ttu-id="96687-148">定義自訂屬性，以指定組件資訊清單的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="96687-148">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<span data-ttu-id="96687-149"><xref:System.Reflection.AssemblyCopyrightAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-149"><xref:System.Reflection.AssemblyCopyrightAttribute></span></span>|<span data-ttu-id="96687-150">定義自訂屬性，以指定組件資訊清單的版權。</span><span class="sxs-lookup"><span data-stu-id="96687-150">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<span data-ttu-id="96687-151"><xref:System.Reflection.AssemblyFileVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-151"><xref:System.Reflection.AssemblyFileVersionAttribute></span></span>|<span data-ttu-id="96687-152">指示編譯器使用 Win32 檔案版本資源的特定版本號碼。</span><span class="sxs-lookup"><span data-stu-id="96687-152">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<span data-ttu-id="96687-153"><xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-153"><xref:System.CLSCompliantAttribute></span></span>|<span data-ttu-id="96687-154">表示組件是否符合 Common Language Specification (CLS) 規範。</span><span class="sxs-lookup"><span data-stu-id="96687-154">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="96687-155">組件資訊清單屬性。</span><span class="sxs-lookup"><span data-stu-id="96687-155">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="96687-156">您可以使用組件資訊清單屬性，在組件資訊清單中提供資訊。</span><span class="sxs-lookup"><span data-stu-id="96687-156">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="96687-157">這包括標題、描述、預設別名和組態。</span><span class="sxs-lookup"><span data-stu-id="96687-157">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="96687-158">下表顯示 <xref:System.Reflection?displayProperty=fullName> 命名空間中定義的組件資訊清單屬性。</span><span class="sxs-lookup"><span data-stu-id="96687-158">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="96687-159">屬性</span><span class="sxs-lookup"><span data-stu-id="96687-159">Attribute</span></span>|<span data-ttu-id="96687-160">用途</span><span class="sxs-lookup"><span data-stu-id="96687-160">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="96687-161"><xref:System.Reflection.AssemblyTitleAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-161"><xref:System.Reflection.AssemblyTitleAttribute></span></span>|<span data-ttu-id="96687-162">定義自訂屬性，以指定組件資訊清單的組件標題。</span><span class="sxs-lookup"><span data-stu-id="96687-162">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<span data-ttu-id="96687-163"><xref:System.Reflection.AssemblyDescriptionAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-163"><xref:System.Reflection.AssemblyDescriptionAttribute></span></span>|<span data-ttu-id="96687-164">定義自訂屬性，以指定組件資訊清單的組件描述。</span><span class="sxs-lookup"><span data-stu-id="96687-164">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<span data-ttu-id="96687-165"><xref:System.Reflection.AssemblyConfigurationAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-165"><xref:System.Reflection.AssemblyConfigurationAttribute></span></span>|<span data-ttu-id="96687-166">定義自訂屬性，以指定組件資訊清單的組件設定 (例如零售或偵錯)。</span><span class="sxs-lookup"><span data-stu-id="96687-166">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<span data-ttu-id="96687-167"><xref:System.Reflection.AssemblyDefaultAliasAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-167"><xref:System.Reflection.AssemblyDefaultAliasAttribute></span></span>|<span data-ttu-id="96687-168">定義組件資訊清單的易記預設別名。</span><span class="sxs-lookup"><span data-stu-id="96687-168">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <span data-ttu-id="96687-169"><a name="Obsolete"></a> Obsolete 屬性</span><span class="sxs-lookup"><span data-stu-id="96687-169"><a name="Obsolete"></a> Obsolete Attribute</span></span>  
 <span data-ttu-id="96687-170">`Obsolete` 屬性會將程式實體標記為不再建議使用的標記。</span><span class="sxs-lookup"><span data-stu-id="96687-170">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="96687-171">每次使用標記為已淘汰的實體都會接著產生警告或錯誤 (視屬性的設定方式而定)。</span><span class="sxs-lookup"><span data-stu-id="96687-171">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="96687-172">例如: </span><span class="sxs-lookup"><span data-stu-id="96687-172">For example:</span></span>  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 <span data-ttu-id="96687-173">在此範例中，`Obsolete` 屬性會套用至 `A` 類別和 `B.OldMethod` 方法。</span><span class="sxs-lookup"><span data-stu-id="96687-173">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="96687-174">因為套用至 `B.OldMethod` 的屬性建構函式的第二個引數設為 `true`，所以這個方法會造成編譯器錯誤，而使用 `A` 類別則只會產生警告。</span><span class="sxs-lookup"><span data-stu-id="96687-174">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="96687-175">不過，呼叫 `B.NewMethod` 不會產生任何警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="96687-175">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="96687-176">提供為屬性建構函式的第一個引數的字串將會顯示為警告或錯誤的一部分。</span><span class="sxs-lookup"><span data-stu-id="96687-176">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="96687-177">例如，當您將它與先前的定義搭配使用時，下列程式碼會產生兩個警告和一個錯誤︰</span><span class="sxs-lookup"><span data-stu-id="96687-177">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="96687-178">會產生 `A` 類別的兩個警告︰一個用於宣告類別參考，一個則用於類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="96687-178">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="96687-179">可以使用沒有引數的 `Obsolete` 屬性，但包括項目為何已淘汰以及建議改使用之項目的說明。</span><span class="sxs-lookup"><span data-stu-id="96687-179">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="96687-180">`Obsolete` 屬性是單次使用屬性，並且可以套用至任何允許屬性的實體。</span><span class="sxs-lookup"><span data-stu-id="96687-180">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="96687-181">`Obsolete` 是 <xref:System.ObsoleteAttribute> 的別名。</span><span class="sxs-lookup"><span data-stu-id="96687-181">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <span data-ttu-id="96687-182"><a name="Conditional"></a> 條件式屬性</span><span class="sxs-lookup"><span data-stu-id="96687-182"><a name="Conditional"></a> Conditional Attribute</span></span>  
 <span data-ttu-id="96687-183">`Conditional` 屬性會根據前置處理識別碼來執行方法。</span><span class="sxs-lookup"><span data-stu-id="96687-183">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="96687-184">`Conditional` 屬性是 <xref:System.Diagnostics.ConditionalAttribute> 的別名，而且可以套用至方法或屬性類別。</span><span class="sxs-lookup"><span data-stu-id="96687-184">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="96687-185">在此範例中，`Conditional` 會套用至方法，以啟用或停用程式特定診斷資訊的顯示︰</span><span class="sxs-lookup"><span data-stu-id="96687-185">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 <span data-ttu-id="96687-186">如果未定義 `TRACE_ON` 識別碼，則不會顯示任何追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="96687-186">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="96687-187">`Conditional` 屬性通常與 `DEBUG` 識別碼搭配使用，以啟用偵錯組建 (而非版本組建) 的追蹤和記錄功能，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="96687-187">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="96687-188">呼叫標記為條件的方法時，所指定前置處理符號的存在與否會決定包含還是省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="96687-188">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="96687-189">如果定義符號，則會包括呼叫；否則會省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="96687-189">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="96687-190">使用 `Conditional` 是 `#if…#endif` 區塊內封入方法的更乾淨、更明確且不容易出錯的替代方式，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="96687-190">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="96687-191">條件式方法必須是類別或結構宣告中的方法，而且不能有傳回值。</span><span class="sxs-lookup"><span data-stu-id="96687-191">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="96687-192">使用多個識別碼</span><span class="sxs-lookup"><span data-stu-id="96687-192">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="96687-193">如果方法有多個 `Conditional` 屬性，則在定義至少一個條件式符號時會包括方法的呼叫 (換句話說，會使用 OR 運算子以邏輯方式將符號連結在一起)。</span><span class="sxs-lookup"><span data-stu-id="96687-193">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="96687-194">在此範例中，如果有 `A` 或 `B`，則會導致方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="96687-194">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="96687-195">若要達到使用 AND 運算子以邏輯方式連結符號的效果，您可以定義序列條件式方法。</span><span class="sxs-lookup"><span data-stu-id="96687-195">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="96687-196">例如，只有在同時定義 `A` 和 `B` 時，才會執行下面的第二個方法：</span><span class="sxs-lookup"><span data-stu-id="96687-196">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```csharp  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="96687-197">搭配使用條件式與屬性類別</span><span class="sxs-lookup"><span data-stu-id="96687-197">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="96687-198">`Conditional` 屬性也可以套用至屬性類別定義。</span><span class="sxs-lookup"><span data-stu-id="96687-198">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="96687-199">在此範例中，如果定義 DEBUG，則自訂屬性 `Documentation` 只會將資訊新增至中繼資料。</span><span class="sxs-lookup"><span data-stu-id="96687-199">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
##  <span data-ttu-id="96687-200"><a name="CallerInfo"></a> 呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="96687-200"><a name="CallerInfo"></a> Caller Info Attributes</span></span>  
 <span data-ttu-id="96687-201">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="96687-201">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="96687-202">您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="96687-202">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="96687-203">若要取得成員呼叫端資訊，請使用套用至選擇性參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="96687-203">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="96687-204">每個選擇性參數都會指定預設值。</span><span class="sxs-lookup"><span data-stu-id="96687-204">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="96687-205">下表列出 <xref:System.Runtime.CompilerServices?displayProperty=fullName> 命名空間中定義的「呼叫端資訊」屬性：</span><span class="sxs-lookup"><span data-stu-id="96687-205">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="96687-206">屬性</span><span class="sxs-lookup"><span data-stu-id="96687-206">Attribute</span></span>|<span data-ttu-id="96687-207">描述</span><span class="sxs-lookup"><span data-stu-id="96687-207">Description</span></span>|<span data-ttu-id="96687-208">類型</span><span class="sxs-lookup"><span data-stu-id="96687-208">Type</span></span>|  
|---|---|---|  
|<span data-ttu-id="96687-209"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-209"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span></span>|<span data-ttu-id="96687-210">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="96687-210">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="96687-211">這是編譯時期的路徑。</span><span class="sxs-lookup"><span data-stu-id="96687-211">This is the path at compile time.</span></span>|`String`|  
|<span data-ttu-id="96687-212"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-212"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span></span>|<span data-ttu-id="96687-213">原始程式檔中呼叫方法的行號。</span><span class="sxs-lookup"><span data-stu-id="96687-213">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<span data-ttu-id="96687-214"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span><span class="sxs-lookup"><span data-stu-id="96687-214"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span></span>|<span data-ttu-id="96687-215">呼叫端的方法名稱或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="96687-215">Method name or property name of the caller.</span></span> <span data-ttu-id="96687-216">如需詳細資訊，請參閱[呼叫端資訊 (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="96687-216">For more information, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="96687-217">如需「呼叫端資訊」屬性的詳細資訊，請參閱[呼叫端資訊 (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="96687-217">For more information about the Caller Info attributes, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96687-218">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96687-218">See Also</span></span>  
 <span data-ttu-id="96687-219"><xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="96687-219"><xref:System.Reflection></span></span>   
 <span data-ttu-id="96687-220"><xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="96687-220"><xref:System.Attribute></span></span>   
<span data-ttu-id="96687-221"> [C# 程式設計指南](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="96687-221"> [C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="96687-222"> [屬性](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="96687-222"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="96687-223"> [反射 (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="96687-223"> [Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="96687-224"> [使用反射存取屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="96687-224"> [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
