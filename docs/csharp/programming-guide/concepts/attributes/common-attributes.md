---
title: 常見屬性 (C#)
ms.date: 07/20/2015
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
ms.openlocfilehash: 771460f8547252448be1b74526ec2babb719c3fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="common-attributes-c"></a><span data-ttu-id="3c5df-102">常見屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="3c5df-102">Common Attributes (C#)</span></span>
<span data-ttu-id="3c5df-103">本主題描述最常在 C# 程式中使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="3c5df-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
-   [<span data-ttu-id="3c5df-104">全域屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="3c5df-105">Obsolete 屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="3c5df-106">條件式屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="3c5df-107">呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
##  <a name="Global"></a> <span data-ttu-id="3c5df-108">全域屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-108">Global Attributes</span></span>  
 <span data-ttu-id="3c5df-109">大部分屬性會套用至特定語言項目 (例如類別或方法)；不過，有些屬性是全域屬性，其套用至整個組件或模組。</span><span class="sxs-lookup"><span data-stu-id="3c5df-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="3c5df-110">例如，<xref:System.Reflection.AssemblyVersionAttribute> 屬性可以用來將版本資訊內嵌到組件，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="3c5df-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="3c5df-111">全域屬性會出現在原始程式碼的任何最上層 `using` 指示詞後面，以及任何類型、模組或命名空間宣告前面。</span><span class="sxs-lookup"><span data-stu-id="3c5df-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="3c5df-112">全域屬性可以出現在多個原始程式檔中，但必須使用單一編譯階段編譯檔案。</span><span class="sxs-lookup"><span data-stu-id="3c5df-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="3c5df-113">在 C# 專案中，全域屬性會放在 AssemblyInfo.cs 檔案中。</span><span class="sxs-lookup"><span data-stu-id="3c5df-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="3c5df-114">組件屬性是提供組件相關資訊的值。</span><span class="sxs-lookup"><span data-stu-id="3c5df-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="3c5df-115">它們的分類如下：</span><span class="sxs-lookup"><span data-stu-id="3c5df-115">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="3c5df-116">組件識別屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-116">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="3c5df-117">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-117">Informational attributes</span></span>  
  
-   <span data-ttu-id="3c5df-118">組件資訊清單屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="3c5df-119">組件識別屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="3c5df-120">三個具有強式名稱 (如果適用) 的屬性會判斷組件的識別：名稱、版本與文化特性。</span><span class="sxs-lookup"><span data-stu-id="3c5df-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="3c5df-121">這些屬性會形成組件的完整名稱，且在程式碼中參考組件時需要用到。</span><span class="sxs-lookup"><span data-stu-id="3c5df-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="3c5df-122">您可以使用屬性來設定組件的版本和文化特性。</span><span class="sxs-lookup"><span data-stu-id="3c5df-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="3c5df-123">不過，名稱值乃是根據包含組件資訊清單的檔案來由編譯器、[組件資訊對話方塊](/visualstudio/ide/reference/assembly-information-dialog-box) 中的 Visual Studio IDE 或在建立組件時的組件連結器 (Al.exe) 所設定。</span><span class="sxs-lookup"><span data-stu-id="3c5df-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="3c5df-124"><xref:System.Reflection.AssemblyFlagsAttribute> 屬性指定組件的多個複本是否可以並存。</span><span class="sxs-lookup"><span data-stu-id="3c5df-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="3c5df-125">下表顯示識別屬性。</span><span class="sxs-lookup"><span data-stu-id="3c5df-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="3c5df-126">屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-126">Attribute</span></span>|<span data-ttu-id="3c5df-127">用途</span><span class="sxs-lookup"><span data-stu-id="3c5df-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="3c5df-128">完整描述組件的識別。</span><span class="sxs-lookup"><span data-stu-id="3c5df-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="3c5df-129">指定組件的版本。</span><span class="sxs-lookup"><span data-stu-id="3c5df-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="3c5df-130">指定組件所支援的文化特性。</span><span class="sxs-lookup"><span data-stu-id="3c5df-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="3c5df-131">指定是否支援在相同電腦上、相同處理程序中或相同應用程式定義域中並存執行組件。</span><span class="sxs-lookup"><span data-stu-id="3c5df-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="3c5df-132">資訊屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-132">Informational Attributes</span></span>  
 <span data-ttu-id="3c5df-133">您可以使用資訊屬性，以提供組件其他的公司或產品資訊。</span><span class="sxs-lookup"><span data-stu-id="3c5df-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="3c5df-134">下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊屬性。</span><span class="sxs-lookup"><span data-stu-id="3c5df-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="3c5df-135">屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-135">Attribute</span></span>|<span data-ttu-id="3c5df-136">用途</span><span class="sxs-lookup"><span data-stu-id="3c5df-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="3c5df-137">定義自訂屬性，以指定組件資訊清單的產品名稱。</span><span class="sxs-lookup"><span data-stu-id="3c5df-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="3c5df-138">定義自訂屬性，以指定組件資訊清單的商標。</span><span class="sxs-lookup"><span data-stu-id="3c5df-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="3c5df-139">定義自訂屬性，以指定組件資訊清單的資訊版本。</span><span class="sxs-lookup"><span data-stu-id="3c5df-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="3c5df-140">定義自訂屬性，以指定組件資訊清單的公司名稱。</span><span class="sxs-lookup"><span data-stu-id="3c5df-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="3c5df-141">定義自訂屬性，以指定組件資訊清單的版權。</span><span class="sxs-lookup"><span data-stu-id="3c5df-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="3c5df-142">指示編譯器使用 Win32 檔案版本資源的特定版本號碼。</span><span class="sxs-lookup"><span data-stu-id="3c5df-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="3c5df-143">表示組件是否符合 Common Language Specification (CLS) 規範。</span><span class="sxs-lookup"><span data-stu-id="3c5df-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="3c5df-144">組件資訊清單屬性。</span><span class="sxs-lookup"><span data-stu-id="3c5df-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="3c5df-145">您可以使用組件資訊清單屬性，在組件資訊清單中提供資訊。</span><span class="sxs-lookup"><span data-stu-id="3c5df-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="3c5df-146">這包括標題、描述、預設別名和組態。</span><span class="sxs-lookup"><span data-stu-id="3c5df-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="3c5df-147">下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊清單屬性。</span><span class="sxs-lookup"><span data-stu-id="3c5df-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="3c5df-148">屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-148">Attribute</span></span>|<span data-ttu-id="3c5df-149">用途</span><span class="sxs-lookup"><span data-stu-id="3c5df-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="3c5df-150">定義自訂屬性，以指定組件資訊清單的組件標題。</span><span class="sxs-lookup"><span data-stu-id="3c5df-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="3c5df-151">定義自訂屬性，以指定組件資訊清單的組件描述。</span><span class="sxs-lookup"><span data-stu-id="3c5df-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="3c5df-152">定義自訂屬性，以指定組件資訊清單的組件設定 (例如零售或偵錯)。</span><span class="sxs-lookup"><span data-stu-id="3c5df-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="3c5df-153">定義組件資訊清單的易記預設別名。</span><span class="sxs-lookup"><span data-stu-id="3c5df-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a> <span data-ttu-id="3c5df-154">Obsolete 屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-154">Obsolete Attribute</span></span>  
 <span data-ttu-id="3c5df-155">`Obsolete` 屬性會將程式實體標記為不再建議使用的標記。</span><span class="sxs-lookup"><span data-stu-id="3c5df-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="3c5df-156">每次使用標記為已淘汰的實體都會接著產生警告或錯誤 (視屬性的設定方式而定)。</span><span class="sxs-lookup"><span data-stu-id="3c5df-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="3c5df-157">例如: </span><span class="sxs-lookup"><span data-stu-id="3c5df-157">For example:</span></span>  
  
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
  
 <span data-ttu-id="3c5df-158">在此範例中，`Obsolete` 屬性會套用至 `A` 類別和 `B.OldMethod` 方法。</span><span class="sxs-lookup"><span data-stu-id="3c5df-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="3c5df-159">因為套用至 `B.OldMethod` 的屬性建構函式的第二個引數設為 `true`，所以這個方法會造成編譯器錯誤，而使用 `A` 類別則只會產生警告。</span><span class="sxs-lookup"><span data-stu-id="3c5df-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="3c5df-160">不過，呼叫 `B.NewMethod` 不會產生任何警告或錯誤。</span><span class="sxs-lookup"><span data-stu-id="3c5df-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="3c5df-161">提供為屬性建構函式的第一個引數的字串將會顯示為警告或錯誤的一部分。</span><span class="sxs-lookup"><span data-stu-id="3c5df-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="3c5df-162">例如，當您將它與先前的定義搭配使用時，下列程式碼會產生兩個警告和一個錯誤︰</span><span class="sxs-lookup"><span data-stu-id="3c5df-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="3c5df-163">會產生 `A` 類別的兩個警告︰一個用於宣告類別參考，一個則用於類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="3c5df-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="3c5df-164">可以使用沒有引數的 `Obsolete` 屬性，但包括項目為何已淘汰以及建議改使用之項目的說明。</span><span class="sxs-lookup"><span data-stu-id="3c5df-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="3c5df-165">`Obsolete` 屬性是單次使用屬性，並且可以套用至任何允許屬性的實體。</span><span class="sxs-lookup"><span data-stu-id="3c5df-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="3c5df-166">`Obsolete` 是 <xref:System.ObsoleteAttribute> 的別名。</span><span class="sxs-lookup"><span data-stu-id="3c5df-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a> <span data-ttu-id="3c5df-167">條件式屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-167">Conditional Attribute</span></span>  
 <span data-ttu-id="3c5df-168">`Conditional` 屬性會根據前置處理識別碼來執行方法。</span><span class="sxs-lookup"><span data-stu-id="3c5df-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="3c5df-169">`Conditional` 屬性是 <xref:System.Diagnostics.ConditionalAttribute> 的別名，而且可以套用至方法或屬性類別。</span><span class="sxs-lookup"><span data-stu-id="3c5df-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="3c5df-170">在此範例中，`Conditional` 會套用至方法，以啟用或停用程式特定診斷資訊的顯示︰</span><span class="sxs-lookup"><span data-stu-id="3c5df-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="3c5df-171">如果未定義 `TRACE_ON` 識別碼，則不會顯示任何追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="3c5df-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="3c5df-172">`Conditional` 屬性通常與 `DEBUG` 識別碼搭配使用，以啟用偵錯組建 (而非版本組建) 的追蹤和記錄功能，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="3c5df-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="3c5df-173">呼叫標記為條件的方法時，所指定前置處理符號的存在與否會決定包含還是省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="3c5df-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="3c5df-174">如果定義符號，則會包括呼叫；否則會省略呼叫。</span><span class="sxs-lookup"><span data-stu-id="3c5df-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="3c5df-175">使用 `Conditional` 是 `#if…#endif` 區塊內封入方法的更乾淨、更明確且不容易出錯的替代方式，與下面類似：</span><span class="sxs-lookup"><span data-stu-id="3c5df-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="3c5df-176">條件式方法必須是類別或結構宣告中的方法，而且不能有傳回值。</span><span class="sxs-lookup"><span data-stu-id="3c5df-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="3c5df-177">使用多個識別碼</span><span class="sxs-lookup"><span data-stu-id="3c5df-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="3c5df-178">如果方法有多個 `Conditional` 屬性，則在定義至少一個條件式符號時會包括方法的呼叫 (換句話說，會使用 OR 運算子以邏輯方式將符號連結在一起)。</span><span class="sxs-lookup"><span data-stu-id="3c5df-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="3c5df-179">在此範例中，如果有 `A` 或 `B`，則會導致方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="3c5df-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="3c5df-180">若要達到使用 AND 運算子以邏輯方式連結符號的效果，您可以定義序列條件式方法。</span><span class="sxs-lookup"><span data-stu-id="3c5df-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="3c5df-181">例如，只有在同時定義 `A` 和 `B` 時，才會執行下面的第二個方法：</span><span class="sxs-lookup"><span data-stu-id="3c5df-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="3c5df-182">搭配使用條件式與屬性類別</span><span class="sxs-lookup"><span data-stu-id="3c5df-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="3c5df-183">`Conditional` 屬性也可以套用至屬性類別定義。</span><span class="sxs-lookup"><span data-stu-id="3c5df-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="3c5df-184">在此範例中，如果定義 DEBUG，則自訂屬性 `Documentation` 只會將資訊新增至中繼資料。</span><span class="sxs-lookup"><span data-stu-id="3c5df-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
##  <a name="CallerInfo"></a> <span data-ttu-id="3c5df-185">呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-185">Caller Info Attributes</span></span>  
 <span data-ttu-id="3c5df-186">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="3c5df-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="3c5df-187">您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="3c5df-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="3c5df-188">若要取得成員呼叫端資訊，請使用套用至選擇性參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="3c5df-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="3c5df-189">每個選擇性參數都會指定預設值。</span><span class="sxs-lookup"><span data-stu-id="3c5df-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="3c5df-190">下表列出 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中定義的 Caller Info 屬性：</span><span class="sxs-lookup"><span data-stu-id="3c5df-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="3c5df-191">屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-191">Attribute</span></span>|<span data-ttu-id="3c5df-192">描述</span><span class="sxs-lookup"><span data-stu-id="3c5df-192">Description</span></span>|<span data-ttu-id="3c5df-193">類型</span><span class="sxs-lookup"><span data-stu-id="3c5df-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="3c5df-194">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="3c5df-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="3c5df-195">這是編譯時期的路徑。</span><span class="sxs-lookup"><span data-stu-id="3c5df-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="3c5df-196">原始程式檔中呼叫方法的行號。</span><span class="sxs-lookup"><span data-stu-id="3c5df-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="3c5df-197">呼叫端的方法名稱或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="3c5df-197">Method name or property name of the caller.</span></span> <span data-ttu-id="3c5df-198">如需詳細資訊，請參閱[呼叫端資訊 (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="3c5df-198">For more information, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="3c5df-199">如需「呼叫端資訊」屬性的詳細資訊，請參閱[呼叫端資訊 (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)。</span><span class="sxs-lookup"><span data-stu-id="3c5df-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5df-200">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c5df-200">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="3c5df-201">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3c5df-201">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3c5df-202">屬性</span><span class="sxs-lookup"><span data-stu-id="3c5df-202">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="3c5df-203">反映 (C#)</span><span class="sxs-lookup"><span data-stu-id="3c5df-203">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="3c5df-204">使用反射存取屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="3c5df-204">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
