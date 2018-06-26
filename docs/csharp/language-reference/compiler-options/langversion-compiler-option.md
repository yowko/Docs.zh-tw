---
title: -langversion (C# 編譯器選項)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 2a9501c883fec7478932b22ea2cdcad70865e0fd
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696282"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="bc0ab-102">-langversion (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="bc0ab-102">-langversion (C# Compiler Options)</span></span>
<span data-ttu-id="bc0ab-103">讓編譯器只接受所選擇 C# 語言規格中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc0ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc0ab-104">Syntax</span></span>  
  
```console  
-langversion:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="bc0ab-105">引數</span><span class="sxs-lookup"><span data-stu-id="bc0ab-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="bc0ab-106">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="bc0ab-106">The following values are valid:</span></span>  
  
|<span data-ttu-id="bc0ab-107">選項</span><span class="sxs-lookup"><span data-stu-id="bc0ab-107">Option</span></span>|<span data-ttu-id="bc0ab-108">意義</span><span class="sxs-lookup"><span data-stu-id="bc0ab-108">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="bc0ab-109">default</span><span class="sxs-lookup"><span data-stu-id="bc0ab-109">default</span></span>|<span data-ttu-id="bc0ab-110">編譯器會接受它可支援之最新主要版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-110">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="bc0ab-111">ISO-1</span><span class="sxs-lookup"><span data-stu-id="bc0ab-111">ISO-1</span></span>|<span data-ttu-id="bc0ab-112">編譯器只會接受 ISO/IEC 23270:2003 C# (1.0/1.2) <sup id="TISO1">[ISO1](#FISO1)</sup> 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="bc0ab-112">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2) <sup id="TISO1">[ISO1](#FISO1)</sup></span></span>|  
|<span data-ttu-id="bc0ab-113">ISO-2</span><span class="sxs-lookup"><span data-stu-id="bc0ab-113">ISO-2</span></span>|<span data-ttu-id="bc0ab-114">編譯器只會接受 ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-114">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span></span>|
|<span data-ttu-id="bc0ab-115">3</span><span class="sxs-lookup"><span data-stu-id="bc0ab-115">3</span></span>|<span data-ttu-id="bc0ab-116">編譯器只會接受 C# 3.0 或較低 <sup id="TCS3">[CS3](#FCS3)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-116">The compiler accepts only syntax that is included in C# 3.0 or lower <sup id="TCS3">[CS3](#FCS3)</sup></span></span>|
|<span data-ttu-id="bc0ab-117">4</span><span class="sxs-lookup"><span data-stu-id="bc0ab-117">4</span></span>|<span data-ttu-id="bc0ab-118">編譯器只會接受 C# 4.0 或較低 <sup id="TCS4">[CS4](#FCS4)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-118">The compiler accepts only syntax that is included in C# 4.0 or lower <sup id="TCS4">[CS4](#FCS4)</sup></span></span>|
|<span data-ttu-id="bc0ab-119">5</span><span class="sxs-lookup"><span data-stu-id="bc0ab-119">5</span></span>|<span data-ttu-id="bc0ab-120">編譯器只會接受 C# 5.0 或較低 <sup id="TCS5">[CS5](#FCS5)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-120">The compiler accepts only syntax that is included in C# 5.0 or lower <sup id="TCS5">[CS5](#FCS5)</sup></span></span>|
|<span data-ttu-id="bc0ab-121">6</span><span class="sxs-lookup"><span data-stu-id="bc0ab-121">6</span></span>|<span data-ttu-id="bc0ab-122">編譯器只會接受 C# 6.0 或較低 <sup id="TCS6">[CS6](#FCS6)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-122">The compiler accepts only syntax that is included in C# 6.0 or lower <sup id="TCS6">[CS6](#FCS6)</sup></span></span>|
|<span data-ttu-id="bc0ab-123">7</span><span class="sxs-lookup"><span data-stu-id="bc0ab-123">7</span></span>|<span data-ttu-id="bc0ab-124">編譯器只會接受 C# 7.0 或較低 <sup id="TCS7">[CS7](#FCS7)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-124">The compiler accepts only syntax that is included in C# 7.0 or lower <sup id="TCS7">[CS7](#FCS7)</sup></span></span>|
|<span data-ttu-id="bc0ab-125">7.1</span><span class="sxs-lookup"><span data-stu-id="bc0ab-125">7.1</span></span>|<span data-ttu-id="bc0ab-126">編譯器只會接受 C# 7.1 或較低 <sup id="TCS71">[CS71](#FCS71)</sup> 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="bc0ab-126">The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup></span></span>|
|<span data-ttu-id="bc0ab-127">7.2</span><span class="sxs-lookup"><span data-stu-id="bc0ab-127">7.2</span></span>|<span data-ttu-id="bc0ab-128">編譯器只會接受 C# 7.2 或較低 <sup id="TCS72">[CS72](#FCS72)</sup> 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="bc0ab-128">The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS72">[CS72](#FCS72)</sup></span></span>|
|<span data-ttu-id="bc0ab-129">7.3</span><span class="sxs-lookup"><span data-stu-id="bc0ab-129">7.3</span></span>|<span data-ttu-id="bc0ab-130">編譯器只會接受 C# 7.3 或較低 <sup id="TCS73">[CS73](#FCS73)</sup> 中所含的語法</span><span class="sxs-lookup"><span data-stu-id="bc0ab-130">The compiler accepts only syntax that is included in C# 7.3 or lower <sup id="TCS73">[CS73](#FCS73)</sup></span></span>|
|<span data-ttu-id="bc0ab-131">latest</span><span class="sxs-lookup"><span data-stu-id="bc0ab-131">latest</span></span>|<span data-ttu-id="bc0ab-132">編譯器會接受它可支援的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-132">The compiler accepts all valid language syntax that it can support.</span></span>|

<!--- Uncomment and move these above
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS8">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a><span data-ttu-id="bc0ab-133">備註</span><span class="sxs-lookup"><span data-stu-id="bc0ab-133">Remarks</span></span>  
 <span data-ttu-id="bc0ab-134">C# 應用程式所參考的中繼資料不限於 **-langversion** 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-134">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>  
  
 <span data-ttu-id="bc0ab-135">因為每個版本的 C# 編譯器都包含語言規格的延伸模組，所以 **-langversion** 不會提供舊版編譯器的相等功能。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-135">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>  
 
 <span data-ttu-id="bc0ab-136">此外，雖然 C# 版本更新通常會與主要 .NET Framework 版本一致，但是新語法和功能不需要繫結至該特定架構版本。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-136">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="bc0ab-137">雖然新功能一定需要也要與 C# 修訂一起發行的新編譯器更新，但是每個特定功能都有自己的最低 .NET API 或通用語言執行平台需求，可讓它包含 NuGet 套件或其他程式庫以在舊版架構上執行。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-137">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>
  
 <span data-ttu-id="bc0ab-138">不論使用的 **-langversion** 設定為何，您都會使用目前版本的通用語言執行平台來建立 .exe 或 .dll。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-138">Regardless of which **-langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="bc0ab-139">其中一個例外狀況是 Friend 組件和 [-moduleassemblyname (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)，這些都是在 **-langversion:ISO-1** 下運作。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-139">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>  
 
 <span data-ttu-id="bc0ab-140">如需其他方式來指定 C# 語言版本，請參閱[選取 C# 語言版本](../configure-language-version.md)主題。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-140">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) topic.</span></span>
  
 <span data-ttu-id="bc0ab-141">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="bc0ab-141">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="bc0ab-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="bc0ab-142">See Also</span></span>  
 [<span data-ttu-id="bc0ab-143">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="bc0ab-143">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="bc0ab-144">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="bc0ab-144">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a><span data-ttu-id="bc0ab-145">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="bc0ab-145">C# Language Specification</span></span>

|<span data-ttu-id="bc0ab-146">版本</span><span class="sxs-lookup"><span data-stu-id="bc0ab-146">Version</span></span>|<span data-ttu-id="bc0ab-147">連結</span><span class="sxs-lookup"><span data-stu-id="bc0ab-147">Link</span></span>|<span data-ttu-id="bc0ab-148">描述</span><span class="sxs-lookup"><span data-stu-id="bc0ab-148">Description</span></span>|
|-------|----|-----------|
|<span data-ttu-id="bc0ab-149">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="bc0ab-149">C# 1.0</span></span>|[<span data-ttu-id="bc0ab-150">下載 DOC</span><span class="sxs-lookup"><span data-stu-id="bc0ab-150">Download DOC</span></span>](http://download.microsoft.com/download/a/9/e/a9e229b9-fee5-4c3e-8476-917dee385062/csharp%20language%20specification%20v1.0.doc)|<span data-ttu-id="bc0ab-151">C# 語言規格版本 1.0：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bc0ab-151">C# Language Specification Version 1.0: Microsoft Corporation</span></span>|
|<span data-ttu-id="bc0ab-152">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="bc0ab-152">C# 1.2</span></span>|[<span data-ttu-id="bc0ab-153">下載 DOC</span><span class="sxs-lookup"><span data-stu-id="bc0ab-153">Download DOC</span></span>](http://download.microsoft.com/download/5/e/5/5e58be0a-b02b-41ac-a4a3-7a22286214ff/csharp%20language%20specification%20v1.2.doc)|<span data-ttu-id="bc0ab-154">C# 語言規格版本 1.2：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bc0ab-154">C# Language Specification Version 1.2: Microsoft Corporation</span></span>|
|<span data-ttu-id="bc0ab-155">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="bc0ab-155">C# 2.0</span></span>|[<span data-ttu-id="bc0ab-156">下載 PDF</span><span class="sxs-lookup"><span data-stu-id="bc0ab-156">Download PDF</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/Ecma-334%204th%20edition%20June%202006.pdf)|<span data-ttu-id="bc0ab-157">標準 ECMA-334 第 4 版</span><span class="sxs-lookup"><span data-stu-id="bc0ab-157">Standard ECMA-334 4th Edition</span></span>|
|<span data-ttu-id="bc0ab-158">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="bc0ab-158">C# 3.0</span></span>|[<span data-ttu-id="bc0ab-159">下載 DOC</span><span class="sxs-lookup"><span data-stu-id="bc0ab-159">Download DOC</span></span>](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|<span data-ttu-id="bc0ab-160">C# 語言規格版本 3.0：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bc0ab-160">C# Language Specification Version 3.0: Microsoft Corporation</span></span>|
|<span data-ttu-id="bc0ab-161">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="bc0ab-161">C# 5.0</span></span>|[<span data-ttu-id="bc0ab-162">下載 PDF</span><span class="sxs-lookup"><span data-stu-id="bc0ab-162">Download PDF</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf)|<span data-ttu-id="bc0ab-163">標準 ECMA-334 第 5 版</span><span class="sxs-lookup"><span data-stu-id="bc0ab-163">Standard ECMA-334 5th Edition</span></span>|
|<span data-ttu-id="bc0ab-164">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="bc0ab-164">C# 6.0</span></span>|[<span data-ttu-id="bc0ab-165">連結</span><span class="sxs-lookup"><span data-stu-id="bc0ab-165">Link</span></span>](../language-specification/index.md)|<span data-ttu-id="bc0ab-166">C# 語言規格版本 6 - 非官方草稿：.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="bc0ab-166">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span>|
|<span data-ttu-id="bc0ab-167">C# 7.0 與更新版本</span><span class="sxs-lookup"><span data-stu-id="bc0ab-167">C# 7.0 and later</span></span>||<span data-ttu-id="bc0ab-168">目前無法使用</span><span class="sxs-lookup"><span data-stu-id="bc0ab-168">not currently available</span></span>|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a><span data-ttu-id="bc0ab-169">支援所有語言功能所需的最低編譯器版本</span><span class="sxs-lookup"><span data-stu-id="bc0ab-169">Minimum compiler version needed to support all language features</span></span>   
<span data-ttu-id="bc0ab-170">[↩](#TISO1)<a name="FISO1">ISO1</a>：Microsoft Visual Studio/Build Tools .Net 2002 或配套 .Net Framework 1.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="bc0ab-170">[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 or bundled .Net Framework 1.0 compiler</span></span>     
<span data-ttu-id="bc0ab-171">[↩](#TISO2)<a name="FISO2">ISO2</a>：Microsoft Visual Studio/Build Tools 2005 或配套 .Net Framework 2.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="bc0ab-171">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 or bundled .Net Framework 2.0 compiler</span></span>    
<span data-ttu-id="bc0ab-172">[↩](#TCS3)<a name="FCS3">CS3</a>：Microsoft Visual Studio/Build Tools 2008 或配套 .Net Framework 3.5 編譯器</span><span class="sxs-lookup"><span data-stu-id="bc0ab-172">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 or bundled .Net Framework 3.5 compiler</span></span>    
<span data-ttu-id="bc0ab-173">[↩](#TCS4)<a name="FCS4">CS4</a>：Microsoft Visual Studio/Build Tools 2010 或配套 .Net Framework 4.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="bc0ab-173">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 or bundled .Net Framework 4.0 compiler</span></span>    
<span data-ttu-id="bc0ab-174">[↩](#TCS5)<a name="FCS5">CS5</a>：Microsoft Visual Studio/Build Tools 2012 或配套 .Net Framework 4.5 編譯器</span><span class="sxs-lookup"><span data-stu-id="bc0ab-174">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 or bundled .Net Framework 4.5 compiler</span></span>    
<span data-ttu-id="bc0ab-175">[↩](#TCS6)<a name="FCS6">CS6</a>：Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="bc0ab-175">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span></span>    
<span data-ttu-id="bc0ab-176">[↩](#TCS7)<a name="FCS7">CS7</a>：Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="bc0ab-176">[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/Build Tools 2017</span></span>   
<span data-ttu-id="bc0ab-177">[↩](#TCS71)<a name="FCS71">CS71</a>：Microsoft Visual Studio/Build Tools 2017，15.3 版</span><span class="sxs-lookup"><span data-stu-id="bc0ab-177">[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>    
<span data-ttu-id="bc0ab-178">[↩](#TCS72)<a name="FCS72">CS72</a>：Microsoft Visual Studio/Build Tools 2017，15.5 版</span><span class="sxs-lookup"><span data-stu-id="bc0ab-178">[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>    
<span data-ttu-id="bc0ab-179">[↩](#TCS73)<a name="FCS73">CS73</a>：Microsoft Visual Studio/Build Tools 2017，15.7 版</span><span class="sxs-lookup"><span data-stu-id="bc0ab-179">[↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>    

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS8)<a name="FCS8">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
