---
title: "-langversion (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034958b14c54540aa175a23067d47bd5d850bab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-c-compiler-options"></a><span data-ttu-id="1ae9b-102">/langversion (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="1ae9b-102">/langversion (C# Compiler Options)</span></span>
<span data-ttu-id="1ae9b-103">讓編譯器只接受所選擇 C# 語言規格中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae9b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ae9b-104">Syntax</span></span>  
  
```console  
/langversion:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="1ae9b-105">引數</span><span class="sxs-lookup"><span data-stu-id="1ae9b-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="1ae9b-106">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="1ae9b-106">The following values are valid:</span></span>  
  
|<span data-ttu-id="1ae9b-107">選項</span><span class="sxs-lookup"><span data-stu-id="1ae9b-107">Option</span></span>|<span data-ttu-id="1ae9b-108">意義</span><span class="sxs-lookup"><span data-stu-id="1ae9b-108">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="1ae9b-109">default</span><span class="sxs-lookup"><span data-stu-id="1ae9b-109">default</span></span>|<span data-ttu-id="1ae9b-110">編譯器會接受它可支援的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-110">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="1ae9b-111"><sup id="TDefault">[Default](#FDefault)</sup></span><span class="sxs-lookup"><span data-stu-id="1ae9b-111"><sup id="TDefault">[Default](#FDefault)</sup></span></span>| 
|<span data-ttu-id="1ae9b-112">ISO-1</span><span class="sxs-lookup"><span data-stu-id="1ae9b-112">ISO-1</span></span>|<span data-ttu-id="1ae9b-113">編譯器只會接受 ISO/IEC 23270:2003 C# (1.0/1.1) <sup id="TISO1">[ISO1](#FISO1)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-113">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.1) <sup id="TISO1">[ISO1](#FISO1)</sup></span></span>|  
|<span data-ttu-id="1ae9b-114">ISO-2</span><span class="sxs-lookup"><span data-stu-id="1ae9b-114">ISO-2</span></span>|<span data-ttu-id="1ae9b-115">編譯器只會接受 ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-115">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup></span></span>|
|<span data-ttu-id="1ae9b-116">3</span><span class="sxs-lookup"><span data-stu-id="1ae9b-116">3</span></span>|<span data-ttu-id="1ae9b-117">編譯器只會接受 C# 3.0 或較低 <sup id="TCS3">[CS3](#FCS3)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-117">The compiler accepts only syntax that is included in C# 3.0 or lower <sup id="TCS3">[CS3](#FCS3)</sup></span></span>|
|<span data-ttu-id="1ae9b-118">4</span><span class="sxs-lookup"><span data-stu-id="1ae9b-118">4</span></span>|<span data-ttu-id="1ae9b-119">編譯器只會接受 C# 4.0 或較低 <sup id="TCS4">[CS4](#FCS4)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-119">The compiler accepts only syntax that is included in C# 4.0 or lower <sup id="TCS4">[CS4](#FCS4)</sup></span></span>|
|<span data-ttu-id="1ae9b-120">5</span><span class="sxs-lookup"><span data-stu-id="1ae9b-120">5</span></span>|<span data-ttu-id="1ae9b-121">編譯器只會接受 C# 5.0 或較低 <sup id="TCS5">[CS5](#FCS5)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-121">The compiler accepts only syntax that is included in C# 5.0 or lower <sup id="TCS5">[CS5](#FCS5)</sup></span></span>|
|<span data-ttu-id="1ae9b-122">6</span><span class="sxs-lookup"><span data-stu-id="1ae9b-122">6</span></span>|<span data-ttu-id="1ae9b-123">編譯器只會接受 C# 6.0 或較低 <sup id="TCS6">[CS6](#FCS6)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-123">The compiler accepts only syntax that is included in C# 6.0 or lower <sup id="TCS6">[CS6](#FCS6)</sup></span></span>|
|<span data-ttu-id="1ae9b-124">7</span><span class="sxs-lookup"><span data-stu-id="1ae9b-124">7</span></span>|<span data-ttu-id="1ae9b-125">編譯器只會接受 C# 7.0 或較低 <sup id="TCS7">[CS7](#FCS7)</sup> 中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-125">The compiler accepts only syntax that is included in C# 7.0 or lower <sup id="TCS7">[CS7](#FCS7)</sup></span></span>|
|<span data-ttu-id="1ae9b-126">latest</span><span class="sxs-lookup"><span data-stu-id="1ae9b-126">latest</span></span>|<span data-ttu-id="1ae9b-127">編譯器會接受它可支援的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-127">The compiler accepts all valid language syntax that it can support.</span></span> <span data-ttu-id="1ae9b-128"><sup id="TLatest">[Latest](#FLatest)</sup></span><span class="sxs-lookup"><span data-stu-id="1ae9b-128"><sup id="TLatest">[Latest](#FLatest)</sup></span></span>|
<!--- Uncomment and move these above
|latest| once they're officially released
|7.1|The compiler accepts only syntax that is included in C# 7.1 or lower <sup id="TCS71">[CS71](#FCS71)</sup>|
|7.2|The compiler accepts only syntax that is included in C# 7.2 or lower <sup id="TCS71">[CS72](#FCS72)</sup>|
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS71">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a><span data-ttu-id="1ae9b-129">備註</span><span class="sxs-lookup"><span data-stu-id="1ae9b-129">Remarks</span></span>  
 <span data-ttu-id="1ae9b-130">C# 應用程式所參考的中繼資料不限於 **/langversion** 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-130">Metadata referenced by your C# application is not subject to **/langversion** compiler option.</span></span>  
  
 <span data-ttu-id="1ae9b-131">因為每個版本的 C# 編譯器包含語言規格的延伸模組，所以 **/langversion** 不會提供舊版編譯器的相等功能。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-131">Because each version of the C# compiler contains extensions to the language specification, **/langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>  
 
 <span data-ttu-id="1ae9b-132">此外，雖然 C# 版本更新通常會與主要 .Net Framework 版本一致，但是新語法和功能不需要繫結至該特定架構版本。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-132">Additionally, while C# version updates generally coincide with major .Net Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="1ae9b-133">雖然新功能一定需要也要與 C# 修訂一起發行的新編譯器更新，但是每個特定功能都有自己的最低 .Net API 或 Common Language Runtime 需求，可讓它包含 NuGet 套件或其他程式庫以在舊版架構上執行。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-133">While the new features will definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .Net API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>
  
 <span data-ttu-id="1ae9b-134">不論使用的 **/langversion** 設定為何，您都會使用目前版本的 Common Language Runtime 來建立 .exe 或 .dll。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-134">Regardless of which **/langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="1ae9b-135">其中一個例外狀況是 Friend 組件和 [/moduleassemblyname (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)，這些都是在 **/langversion:ISO-1** 下運作。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-135">One exception is friend assemblies and [/moduleassemblyname (C# Compiler Option)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), which work under **/langversion:ISO-1**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1ae9b-136">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="1ae9b-136">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="1ae9b-137">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-137">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="1ae9b-138">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-138">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="1ae9b-139">按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-139">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="1ae9b-140">修改 [語言版本] 屬性。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-140">Modify the **Language Version** property.</span></span>  
  
 <span data-ttu-id="1ae9b-141">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="1ae9b-141">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>  
    
## <a name="see-also"></a><span data-ttu-id="1ae9b-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ae9b-142">See Also</span></span>  
 [<span data-ttu-id="1ae9b-143">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="1ae9b-143">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="1ae9b-144">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="1ae9b-144">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a><span data-ttu-id="1ae9b-145">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1ae9b-145">C# Language Specification</span></span>
 <span data-ttu-id="1ae9b-146">[C# 語言規格參考](../../../csharp/language-reference/language-specification/index.md)：.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="1ae9b-146">[C# Language Specification Reference](../../../csharp/language-reference/language-specification/index.md) : .NET Foundation</span></span>  
 <span data-ttu-id="1ae9b-147">C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) 資訊技術 -- C# 語言規格：ISO 目錄</span><span class="sxs-lookup"><span data-stu-id="1ae9b-147">C# 1.0/1.1 [ISO/IEC 23270:2003](https://www.iso.org/standard/36768.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="1ae9b-148">C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) 資訊技術 -- C# 語言規格：ISO 目錄</span><span class="sxs-lookup"><span data-stu-id="1ae9b-148">C# 2.0 [ISO/IEC 23270:2006](https://www.iso.org/standard/42926.html) Information technology -- C# Language Specification : ISO Catalogue</span></span>  
 <span data-ttu-id="1ae9b-149">C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://go.microsoft.com/fwlink/?LinkId=144406) PDF 格式的 ISO/IEC 23270:2006：ISO 自由可用標準</span><span class="sxs-lookup"><span data-stu-id="1ae9b-149">C# 2.0 [c042926_ISO_IEC_23270_2006(E).zip](http://go.microsoft.com/fwlink/?LinkId=144406) ISO/IEC 23270:2006 in PDF format : ISO Freely Available Standards</span></span>  
 <span data-ttu-id="1ae9b-150">C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# 語言規格版本 3.0：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="1ae9b-150">C# 3.0 [CSharp Language Specification.doc](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc) C# Language Specification Version 3.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="1ae9b-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) 標準 ECMA-334 第 4 版</span><span class="sxs-lookup"><span data-stu-id="1ae9b-151">C# 4.0 [Ecma-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf) Standard ECMA-334 4th Edition</span></span>    
 <span data-ttu-id="1ae9b-152">C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# 語言規格版本 5.0：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="1ae9b-152">C# 5.0 [CSharp Language Specification.docx](https://www.microsoft.com/download/details.aspx?id=7029) C# Language Specification Version 5.0 : Microsoft Corporation</span></span>  
 <span data-ttu-id="1ae9b-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# 語言規格版本 6 - 非官方草稿：.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="1ae9b-153">C# 6.0 [README.md](https://github.com/dotnet/csharplang/blob/master/spec/README.md) C# Language Specification Version 6 - Unofficial Draft : .NET Foundation</span></span>  
 <span data-ttu-id="1ae9b-154">C# 7.0 (目前無法使用)</span><span class="sxs-lookup"><span data-stu-id="1ae9b-154">C# 7.0 (not currently available)</span></span>  

<!--- Uncomment and add to the above when they become officially released
 C# 7.1 (spec is not yet finished)  
 C# 7.2 (spec is not yet finished)  
 C# 8.0 (spec is not yet finished)  
-->

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a><span data-ttu-id="1ae9b-155">支援所有語言功能所需的最低編譯器版本</span><span class="sxs-lookup"><span data-stu-id="1ae9b-155">Minimum compiler version needed to support all language features</span></span>   
<span data-ttu-id="1ae9b-156">[↩](#TDefault)<a name="FDefault">預設</a>、<a name="FISO1">ISO1</a>：Microsoft Visual Studio/Build Tools .Net 2002 或配套 .Net Framework 1.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="1ae9b-156">[↩](#TDefault)<a name="FDefault">Default</a>, <a name="FISO1">ISO1</a>: Microsoft Visual Studio/Build Tools .Net 2002 or bundled .Net Framework 1.0 compiler</span></span>     
<span data-ttu-id="1ae9b-157">[↩](#TISO2)<a name="FISO2">ISO2</a>：Microsoft Visual Studio/Build Tools 2005 或配套 .Net Framework 2.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="1ae9b-157">[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/Build Tools 2005 or bundled .Net Framework 2.0 compiler</span></span>    
<span data-ttu-id="1ae9b-158">[↩](#TCS3)<a name="FCS3">CS3</a>：Microsoft Visual Studio/Build Tools 2008 或配套 .Net Framework 3.5 編譯器</span><span class="sxs-lookup"><span data-stu-id="1ae9b-158">[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/Build Tools 2008 or bundled .Net Framework 3.5 compiler</span></span>    
<span data-ttu-id="1ae9b-159">[↩](#TCS4)<a name="FCS4">CS4</a>：Microsoft Visual Studio/Build Tools 2010 或配套 .Net Framework 4.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="1ae9b-159">[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/Build Tools 2010 or bundled .Net Framework 4.0 compiler</span></span>    
<span data-ttu-id="1ae9b-160">[↩](#TCS5)<a name="FCS5">CS5</a>：Microsoft Visual Studio/Build Tools 2012 或配套 .Net Framework 4.5 編譯器</span><span class="sxs-lookup"><span data-stu-id="1ae9b-160">[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/Build Tools 2012 or bundled .Net Framework 4.5 compiler</span></span>    
<span data-ttu-id="1ae9b-161">[↩](#TCS6)<a name="FCS6">CS6</a>：Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="1ae9b-161">[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/Build Tools 2015</span></span>    
<span data-ttu-id="1ae9b-162">[↩](#TCS7)<a name="FCS7">CS7</a>、<a name="FLatest">Latest</a>：Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="1ae9b-162">[↩](#TCS7)<a name="FCS7">CS7</a>, <a name="FLatest">Latest</a>: Microsoft Visual Studio/Build Tools 2017</span></span>   

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/Build Tools 20??    
[↩](#TCS8)<a name="FCS71">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
