---
title: -langversion (C# 編譯器選項)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 81cf336f94815dd3f2c88995eb34ae03b8220097
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179925"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="619ca-102">-langversion (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="619ca-102">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="619ca-103">讓編譯器只接受所選擇 C# 語言規格中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="619ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="619ca-104">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="619ca-105">引數</span><span class="sxs-lookup"><span data-stu-id="619ca-105">Arguments</span></span>

 `option`  
 <span data-ttu-id="619ca-106">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="619ca-106">The following values are valid:</span></span>

|<span data-ttu-id="619ca-107">選項</span><span class="sxs-lookup"><span data-stu-id="619ca-107">Option</span></span>|<span data-ttu-id="619ca-108">意義</span><span class="sxs-lookup"><span data-stu-id="619ca-108">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="619ca-109">preview</span><span class="sxs-lookup"><span data-stu-id="619ca-109">preview</span></span>|<span data-ttu-id="619ca-110">編譯器會接受它可支援之最新預覽版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-110">The compiler accepts all valid language syntax from the latest preview version that it can support.</span></span>|
|<span data-ttu-id="619ca-111">latest</span><span class="sxs-lookup"><span data-stu-id="619ca-111">latest</span></span>|<span data-ttu-id="619ca-112">編譯器會接受它可支援之最新版本 (包括次要版本) 的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-112">The compiler accepts all valid language syntax from the latest version (including minor releases) that it can support.</span></span>|
|<span data-ttu-id="619ca-113">latestMajor</span><span class="sxs-lookup"><span data-stu-id="619ca-113">latestMajor</span></span>|<span data-ttu-id="619ca-114">編譯器會接受它可支援之最新主要版本的所有有效語言語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-114">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="619ca-115">8.0</span><span class="sxs-lookup"><span data-stu-id="619ca-115">8.0</span></span>|<span data-ttu-id="619ca-116">編譯器只會接受 C# 8.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-116">The compiler accepts only syntax that is included in C# 8.0 or lower.</span></span>|
|<span data-ttu-id="619ca-117">7.3</span><span class="sxs-lookup"><span data-stu-id="619ca-117">7.3</span></span>|<span data-ttu-id="619ca-118">編譯器只會接受 C# 7.3 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-118">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="619ca-119">7.2</span><span class="sxs-lookup"><span data-stu-id="619ca-119">7.2</span></span>|<span data-ttu-id="619ca-120">編譯器只會接受 C# 7.2 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-120">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="619ca-121">7.1</span><span class="sxs-lookup"><span data-stu-id="619ca-121">7.1</span></span>|<span data-ttu-id="619ca-122">編譯器只會接受 C# 7.1 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-122">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="619ca-123">7</span><span class="sxs-lookup"><span data-stu-id="619ca-123">7</span></span>|<span data-ttu-id="619ca-124">編譯器只會接受 C# 7.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-124">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="619ca-125">6</span><span class="sxs-lookup"><span data-stu-id="619ca-125">6</span></span>|<span data-ttu-id="619ca-126">編譯器只會接受 C# 6.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-126">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="619ca-127">5</span><span class="sxs-lookup"><span data-stu-id="619ca-127">5</span></span>|<span data-ttu-id="619ca-128">編譯器只會接受 C# 5.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-128">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="619ca-129">4</span><span class="sxs-lookup"><span data-stu-id="619ca-129">4</span></span>|<span data-ttu-id="619ca-130">編譯器只會接受 C# 4.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-130">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="619ca-131">3</span><span class="sxs-lookup"><span data-stu-id="619ca-131">3</span></span>|<span data-ttu-id="619ca-132">編譯器只會接受 C# 3.0 或更低版本中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-132">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="619ca-133">ISO-2</span><span class="sxs-lookup"><span data-stu-id="619ca-133">ISO-2</span></span>|<span data-ttu-id="619ca-134">編譯器只會接受 ISO/IEC 23270:2006 C# （2.0）中所包含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-134">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0).</span></span>|
|<span data-ttu-id="619ca-135">ISO-1</span><span class="sxs-lookup"><span data-stu-id="619ca-135">ISO-1</span></span>|<span data-ttu-id="619ca-136">編譯器只會接受 ISO/IEC 23270:2003 C# （1.0/1.2）中所包含的語法。</span><span class="sxs-lookup"><span data-stu-id="619ca-136">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2).</span></span>|

<span data-ttu-id="619ca-137">預設語言版本取決於您應用程式的目標 Framework，以及安裝的 SDK 或 Visual Studio 版本。</span><span class="sxs-lookup"><span data-stu-id="619ca-137">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="619ca-138">這些規則定義于設定[語言版本](../configure-language-version.md#defaults)一文。</span><span class="sxs-lookup"><span data-stu-id="619ca-138">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="619ca-139">備註</span><span class="sxs-lookup"><span data-stu-id="619ca-139">Remarks</span></span>

<span data-ttu-id="619ca-140">C# 應用程式所參考的中繼資料不限於 **-langversion** 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="619ca-140">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>
  
<span data-ttu-id="619ca-141">因為每個版本的 C# 編譯器都包含語言規格的延伸模組，所以 **-langversion** 不會提供舊版編譯器的相等功能。</span><span class="sxs-lookup"><span data-stu-id="619ca-141">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="619ca-142">此外，雖然 C# 版本更新通常會與主要 .NET Framework 版本一致，但是新語法和功能不需要繫結至該特定架構版本。</span><span class="sxs-lookup"><span data-stu-id="619ca-142">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="619ca-143">雖然新功能一定需要也要與 C# 修訂一起發行的新編譯器更新，但是每個特定功能都有自己的最低 .NET API 或通用語言執行平台需求，可讓它包含 NuGet 套件或其他程式庫以在舊版架構上執行。</span><span class="sxs-lookup"><span data-stu-id="619ca-143">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="619ca-144">不論使用的 **-langversion** 設定為何，您都會使用目前版本的通用語言執行平台來建立 .exe 或 .dll。</span><span class="sxs-lookup"><span data-stu-id="619ca-144">Regardless of which **-langversion** setting you use, you will use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="619ca-145">其中一個例外狀況是 Friend 組件和 [-moduleassemblyname (C# 編譯器選項)](./moduleassemblyname-compiler-option.md)，這些都是在 **-langversion:ISO-1** 下運作。</span><span class="sxs-lookup"><span data-stu-id="619ca-145">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>  

<span data-ttu-id="619ca-146">如需指定C#語言版本的其他方式，請參閱[ C#選取語言版本](../configure-language-version.md)一文。</span><span class="sxs-lookup"><span data-stu-id="619ca-146">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="619ca-147">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="619ca-147">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="619ca-148">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="619ca-148">C# language specification</span></span>

|<span data-ttu-id="619ca-149">Version</span><span class="sxs-lookup"><span data-stu-id="619ca-149">Version</span></span>|<span data-ttu-id="619ca-150">連結</span><span class="sxs-lookup"><span data-stu-id="619ca-150">Link</span></span>|<span data-ttu-id="619ca-151">描述</span><span class="sxs-lookup"><span data-stu-id="619ca-151">Description</span></span>|
|-------|----|-----------|
|<span data-ttu-id="619ca-152">C# 7.0 與更新版本</span><span class="sxs-lookup"><span data-stu-id="619ca-152">C# 7.0 and later</span></span>||<span data-ttu-id="619ca-153">目前無法使用</span><span class="sxs-lookup"><span data-stu-id="619ca-153">not currently available</span></span>|
|<span data-ttu-id="619ca-154">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="619ca-154">C# 6.0</span></span>|[<span data-ttu-id="619ca-155">連結</span><span class="sxs-lookup"><span data-stu-id="619ca-155">Link</span></span>](../language-specification/index.md)|<span data-ttu-id="619ca-156">C# 語言規格版本 6 - 非官方草稿：.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="619ca-156">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span>|
|<span data-ttu-id="619ca-157">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="619ca-157">C# 5.0</span></span>|[<span data-ttu-id="619ca-158">下載 PDF</span><span class="sxs-lookup"><span data-stu-id="619ca-158">Download PDF</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|<span data-ttu-id="619ca-159">標準 ECMA-334 第 5 版</span><span class="sxs-lookup"><span data-stu-id="619ca-159">Standard ECMA-334 5th Edition</span></span>|
|<span data-ttu-id="619ca-160">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="619ca-160">C# 3.0</span></span>|[<span data-ttu-id="619ca-161">下載 DOC</span><span class="sxs-lookup"><span data-stu-id="619ca-161">Download DOC</span></span>](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|<span data-ttu-id="619ca-162">C# 語言規格 3.0 版：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="619ca-162">C# Language Specification Version 3.0: Microsoft Corporation</span></span>|
|<span data-ttu-id="619ca-163">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="619ca-163">C# 2.0</span></span>|[<span data-ttu-id="619ca-164">下載 PDF</span><span class="sxs-lookup"><span data-stu-id="619ca-164">Download PDF</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|<span data-ttu-id="619ca-165">標準 ECMA-334 第 4 版</span><span class="sxs-lookup"><span data-stu-id="619ca-165">Standard ECMA-334 4th Edition</span></span>|
|<span data-ttu-id="619ca-166">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="619ca-166">C# 1.2</span></span>|[<span data-ttu-id="619ca-167">下載 DOC</span><span class="sxs-lookup"><span data-stu-id="619ca-167">Download DOC</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|<span data-ttu-id="619ca-168">C# 語言規格 1.2 版：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="619ca-168">C# Language Specification Version 1.2: Microsoft Corporation</span></span>|
|<span data-ttu-id="619ca-169">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="619ca-169">C# 1.0</span></span>|[<span data-ttu-id="619ca-170">下載 DOC</span><span class="sxs-lookup"><span data-stu-id="619ca-170">Download DOC</span></span>](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|<span data-ttu-id="619ca-171">C# 語言規格 1.0 版：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="619ca-171">C# Language Specification Version 1.0: Microsoft Corporation</span></span>|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="619ca-172">支援所有語言功能所需的最低 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="619ca-172">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="619ca-173">下表列出具有支援對應語言版本之C#編譯器的 SDK 的最低版本：</span><span class="sxs-lookup"><span data-stu-id="619ca-173">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

|<span data-ttu-id="619ca-174">C#版本</span><span class="sxs-lookup"><span data-stu-id="619ca-174">C# version</span></span>|<span data-ttu-id="619ca-175">最低 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="619ca-175">Minimum SDK version</span></span>|
|----------|-------------------|
|<span data-ttu-id="619ca-176">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="619ca-176">C# 8.0</span></span>| <span data-ttu-id="619ca-177">Microsoft Visual Studio/Build Tools 2019、16.3 版或 .NET Core 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="619ca-177">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span> |
|<span data-ttu-id="619ca-178">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="619ca-178">C# 7.3</span></span>| <span data-ttu-id="619ca-179">Microsoft Visual Studio/Build Tools 2017 15.7 版</span><span class="sxs-lookup"><span data-stu-id="619ca-179">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span> |
|<span data-ttu-id="619ca-180">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="619ca-180">C# 7.2</span></span>| <span data-ttu-id="619ca-181">Microsoft Visual Studio/Build Tools 2017 15.5 版</span><span class="sxs-lookup"><span data-stu-id="619ca-181">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span> |
|<span data-ttu-id="619ca-182">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="619ca-182">C# 7.1</span></span>| <span data-ttu-id="619ca-183">Microsoft Visual Studio/Build Tools 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="619ca-183">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span> |
|<span data-ttu-id="619ca-184">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="619ca-184">C# 7.0</span></span>| <span data-ttu-id="619ca-185">Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="619ca-185">Microsoft Visual Studio/Build Tools 2017</span></span> |
|<span data-ttu-id="619ca-186">C# 6</span><span class="sxs-lookup"><span data-stu-id="619ca-186">C# 6</span></span>| <span data-ttu-id="619ca-187">Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="619ca-187">Microsoft Visual Studio/Build Tools 2015</span></span> |
|<span data-ttu-id="619ca-188">C#第</span><span class="sxs-lookup"><span data-stu-id="619ca-188">C# 5</span></span>| <span data-ttu-id="619ca-189">Microsoft Visual Studio/Build Tools 2012 或配套的 .NET Framework 4.5 編譯器</span><span class="sxs-lookup"><span data-stu-id="619ca-189">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span> |
|<span data-ttu-id="619ca-190">C# 4</span><span class="sxs-lookup"><span data-stu-id="619ca-190">C# 4</span></span>| <span data-ttu-id="619ca-191">Microsoft Visual Studio/Build Tools 2010 或配套的 .NET Framework 4.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="619ca-191">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span> |
|<span data-ttu-id="619ca-192">C#第</span><span class="sxs-lookup"><span data-stu-id="619ca-192">C# 3</span></span>| <span data-ttu-id="619ca-193">Microsoft Visual Studio/Build Tools 2008 或配套的 .NET Framework 3.5 編譯器</span><span class="sxs-lookup"><span data-stu-id="619ca-193">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span> |
|<span data-ttu-id="619ca-194">C#2</span><span class="sxs-lookup"><span data-stu-id="619ca-194">C# 2</span></span>| <span data-ttu-id="619ca-195">Microsoft Visual Studio/Build Tools 2005 或配套的 .NET Framework 2.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="619ca-195">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span> |
|<span data-ttu-id="619ca-196">C#1.0/1。2</span><span class="sxs-lookup"><span data-stu-id="619ca-196">C# 1.0/1.2</span></span> | <span data-ttu-id="619ca-197">Microsoft Visual Studio/Build Tools .NET 2002 或配套的 .NET Framework 1.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="619ca-197">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="619ca-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="619ca-198">See also</span></span>

- [<span data-ttu-id="619ca-199">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="619ca-199">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="619ca-200">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="619ca-200">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
