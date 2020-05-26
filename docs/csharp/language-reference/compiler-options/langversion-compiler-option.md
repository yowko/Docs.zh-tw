---
title: -langversion (C# 編譯器選項)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 408b2fb1f19f872db675321601ebc1b0c921044b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802936"
---
# <a name="-langversion-c-compiler-options"></a><span data-ttu-id="78c2e-102">-langversion (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="78c2e-102">-langversion (C# Compiler Options)</span></span>

<span data-ttu-id="78c2e-103">讓編譯器只接受所選擇 C# 語言規格中所含的語法。</span><span class="sxs-lookup"><span data-stu-id="78c2e-103">Causes the compiler to accept only syntax that is included in the chosen C# language specification.</span></span>

## <a name="syntax"></a><span data-ttu-id="78c2e-104">語法</span><span class="sxs-lookup"><span data-stu-id="78c2e-104">Syntax</span></span>

```console
-langversion:option
```

## <a name="arguments"></a><span data-ttu-id="78c2e-105">引數</span><span class="sxs-lookup"><span data-stu-id="78c2e-105">Arguments</span></span>

`option`

<span data-ttu-id="78c2e-106">下列是有效值：</span><span class="sxs-lookup"><span data-stu-id="78c2e-106">The following values are valid:</span></span>

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

<span data-ttu-id="78c2e-107">預設語言版本取決於您應用程式的目標 Framework，以及安裝的 SDK 或 Visual Studio 版本。</span><span class="sxs-lookup"><span data-stu-id="78c2e-107">The default language version depends on the target framework for your application and the version of the SDK or Visual Studio installed.</span></span> <span data-ttu-id="78c2e-108">這些規則定義于設定[語言版本](../configure-language-version.md#defaults)一文。</span><span class="sxs-lookup"><span data-stu-id="78c2e-108">Those rules are defined in the [configuring the language version](../configure-language-version.md#defaults) article.</span></span>

## <a name="remarks"></a><span data-ttu-id="78c2e-109">備註</span><span class="sxs-lookup"><span data-stu-id="78c2e-109">Remarks</span></span>

<span data-ttu-id="78c2e-110">C# 應用程式所參考的中繼資料不限於 **-langversion** 編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="78c2e-110">Metadata referenced by your C# application is not subject to **-langversion** compiler option.</span></span>

<span data-ttu-id="78c2e-111">因為每個版本的 C# 編譯器都包含語言規格的延伸模組，所以 **-langversion** 不會提供舊版編譯器的相等功能。</span><span class="sxs-lookup"><span data-stu-id="78c2e-111">Because each version of the C# compiler contains extensions to the language specification, **-langversion** does not give you the equivalent functionality of an earlier version of the compiler.</span></span>

<span data-ttu-id="78c2e-112">此外，雖然 C# 版本更新通常會與主要 .NET Framework 版本一致，但是新語法和功能不需要繫結至該特定架構版本。</span><span class="sxs-lookup"><span data-stu-id="78c2e-112">Additionally, while C# version updates generally coincide with major .NET Framework releases, the new syntax and features are not necessarily tied to that specific framework version.</span></span> <span data-ttu-id="78c2e-113">雖然新功能一定需要也要與 C# 修訂一起發行的新編譯器更新，但是每個特定功能都有自己的最低 .NET API 或通用語言執行平台需求，可讓它包含 NuGet 套件或其他程式庫以在舊版架構上執行。</span><span class="sxs-lookup"><span data-stu-id="78c2e-113">While the new features definitely require a new compiler update that is also released alongside the C# revision, each specific feature has its own minimum .NET API or common language runtime requirements that may allow it to run on downlevel frameworks by including NuGet packages or other libraries.</span></span>

<span data-ttu-id="78c2e-114">不論您使用的是哪一種**langversion**設定，請使用目前版本的 common language runtime 來建立 .exe 或 .dll。</span><span class="sxs-lookup"><span data-stu-id="78c2e-114">Regardless of which **-langversion** setting you use, use the current version of the common language runtime to create your .exe or .dll.</span></span> <span data-ttu-id="78c2e-115">其中一個例外狀況是 Friend 組件和 [-moduleassemblyname (C# 編譯器選項)](./moduleassemblyname-compiler-option.md)，這些都是在 **-langversion:ISO-1** 下運作。</span><span class="sxs-lookup"><span data-stu-id="78c2e-115">One exception is friend assemblies and [-moduleassemblyname (C# Compiler Option)](./moduleassemblyname-compiler-option.md), which work under **-langversion:ISO-1**.</span></span>

<span data-ttu-id="78c2e-116">如需指定 c # 語言版本的其他方式，請參閱[選取 c # 語言版本](../configure-language-version.md)一文。</span><span class="sxs-lookup"><span data-stu-id="78c2e-116">For other ways to specify the C# language version, see the [Select the C# language version](../configure-language-version.md) article.</span></span>

<span data-ttu-id="78c2e-117">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="78c2e-117">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="78c2e-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="78c2e-118">C# language specification</span></span>

| <span data-ttu-id="78c2e-119">版本</span><span class="sxs-lookup"><span data-stu-id="78c2e-119">Version</span></span>          | <span data-ttu-id="78c2e-120">連結</span><span class="sxs-lookup"><span data-stu-id="78c2e-120">Link</span></span>                       | <span data-ttu-id="78c2e-121">描述</span><span class="sxs-lookup"><span data-stu-id="78c2e-121">Description</span></span>                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| <span data-ttu-id="78c2e-122">C# 7.0 與更新版本</span><span class="sxs-lookup"><span data-stu-id="78c2e-122">C# 7.0 and later</span></span> |                            | <span data-ttu-id="78c2e-123">目前無法使用</span><span class="sxs-lookup"><span data-stu-id="78c2e-123">Not currently available</span></span>                                                 |
| <span data-ttu-id="78c2e-124">C# 6.0</span><span class="sxs-lookup"><span data-stu-id="78c2e-124">C# 6.0</span></span>           | <span data-ttu-id="78c2e-125">[連結][csharp-6]</span><span class="sxs-lookup"><span data-stu-id="78c2e-125">[Link][csharp-6]</span></span>           | <span data-ttu-id="78c2e-126">C# 語言規格版本 6 - 非官方草稿：.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="78c2e-126">C# Language Specification Version 6 - Unofficial Draft: .NET Foundation</span></span> |
| <span data-ttu-id="78c2e-127">C# 5.0</span><span class="sxs-lookup"><span data-stu-id="78c2e-127">C# 5.0</span></span>           | <span data-ttu-id="78c2e-128">[下載 PDF][csharp-5]</span><span class="sxs-lookup"><span data-stu-id="78c2e-128">[Download PDF][csharp-5]</span></span>   | <span data-ttu-id="78c2e-129">標準 ECMA-334 第 5 版</span><span class="sxs-lookup"><span data-stu-id="78c2e-129">Standard ECMA-334 5th Edition</span></span>                                           |
| <span data-ttu-id="78c2e-130">C# 3.0</span><span class="sxs-lookup"><span data-stu-id="78c2e-130">C# 3.0</span></span>           | <span data-ttu-id="78c2e-131">[下載 DOC][csharp-3]</span><span class="sxs-lookup"><span data-stu-id="78c2e-131">[Download DOC][csharp-3]</span></span>   | <span data-ttu-id="78c2e-132">C# 語言規格版本 3.0：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="78c2e-132">C# Language Specification Version 3.0: Microsoft Corporation</span></span>            |
| <span data-ttu-id="78c2e-133">C# 2.0</span><span class="sxs-lookup"><span data-stu-id="78c2e-133">C# 2.0</span></span>           | <span data-ttu-id="78c2e-134">[下載 PDF][csharp-2]</span><span class="sxs-lookup"><span data-stu-id="78c2e-134">[Download PDF][csharp-2]</span></span>   | <span data-ttu-id="78c2e-135">標準 ECMA-334 第 4 版</span><span class="sxs-lookup"><span data-stu-id="78c2e-135">Standard ECMA-334 4th Edition</span></span>                                           |
| <span data-ttu-id="78c2e-136">C# 1.2</span><span class="sxs-lookup"><span data-stu-id="78c2e-136">C# 1.2</span></span>           | <span data-ttu-id="78c2e-137">[下載 DOC][csharp-1.2]</span><span class="sxs-lookup"><span data-stu-id="78c2e-137">[Download DOC][csharp-1.2]</span></span> | <span data-ttu-id="78c2e-138">C# 語言規格版本 1.2：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="78c2e-138">C# Language Specification Version 1.2: Microsoft Corporation</span></span>            |
| <span data-ttu-id="78c2e-139">C# 1.0</span><span class="sxs-lookup"><span data-stu-id="78c2e-139">C# 1.0</span></span>           | <span data-ttu-id="78c2e-140">[下載 DOC][csharp-1]</span><span class="sxs-lookup"><span data-stu-id="78c2e-140">[Download DOC][csharp-1]</span></span>   | <span data-ttu-id="78c2e-141">C# 語言規格版本 1.0：Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="78c2e-141">C# Language Specification Version 1.0: Microsoft Corporation</span></span>            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a><span data-ttu-id="78c2e-142">支援所有語言功能所需的最低 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="78c2e-142">Minimum SDK version needed to support all language features</span></span>

<span data-ttu-id="78c2e-143">下表列出 SDK 的最低版本，以及支援對應語言版本的 c # 編譯器：</span><span class="sxs-lookup"><span data-stu-id="78c2e-143">The following table lists the minimum versions of the SDK with the C# compiler that supports the corresponding language version:</span></span>

| <span data-ttu-id="78c2e-144">C # 版本</span><span class="sxs-lookup"><span data-stu-id="78c2e-144">C# version</span></span> | <span data-ttu-id="78c2e-145">最低 SDK 版本</span><span class="sxs-lookup"><span data-stu-id="78c2e-145">Minimum SDK version</span></span>                                                                  |
|------------|--------------------------------------------------------------------------------------|
| <span data-ttu-id="78c2e-146">C# 8.0</span><span class="sxs-lookup"><span data-stu-id="78c2e-146">C# 8.0</span></span>     | <span data-ttu-id="78c2e-147">Microsoft Visual Studio/Build Tools 2019、16.3 版或 .NET Core 3.0 SDK</span><span class="sxs-lookup"><span data-stu-id="78c2e-147">Microsoft Visual Studio/Build Tools 2019, version 16.3, or .NET Core 3.0 SDK</span></span>         |
| <span data-ttu-id="78c2e-148">C# 7.3</span><span class="sxs-lookup"><span data-stu-id="78c2e-148">C# 7.3</span></span>     | <span data-ttu-id="78c2e-149">Microsoft Visual Studio/Build Tools 2017 15.7 版</span><span class="sxs-lookup"><span data-stu-id="78c2e-149">Microsoft Visual Studio/Build Tools 2017, version 15.7</span></span>                               |
| <span data-ttu-id="78c2e-150">C# 7.2</span><span class="sxs-lookup"><span data-stu-id="78c2e-150">C# 7.2</span></span>     | <span data-ttu-id="78c2e-151">Microsoft Visual Studio/Build Tools 2017 15.5 版</span><span class="sxs-lookup"><span data-stu-id="78c2e-151">Microsoft Visual Studio/Build Tools 2017, version 15.5</span></span>                               |
| <span data-ttu-id="78c2e-152">C# 7.1</span><span class="sxs-lookup"><span data-stu-id="78c2e-152">C# 7.1</span></span>     | <span data-ttu-id="78c2e-153">Microsoft Visual Studio/Build Tools 2017 15.3 版</span><span class="sxs-lookup"><span data-stu-id="78c2e-153">Microsoft Visual Studio/Build Tools 2017, version 15.3</span></span>                               |
| <span data-ttu-id="78c2e-154">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="78c2e-154">C# 7.0</span></span>     | <span data-ttu-id="78c2e-155">Microsoft Visual Studio/Build Tools 2017</span><span class="sxs-lookup"><span data-stu-id="78c2e-155">Microsoft Visual Studio/Build Tools 2017</span></span>                                             |
| <span data-ttu-id="78c2e-156">C# 6</span><span class="sxs-lookup"><span data-stu-id="78c2e-156">C# 6</span></span>       | <span data-ttu-id="78c2e-157">Microsoft Visual Studio/Build Tools 2015</span><span class="sxs-lookup"><span data-stu-id="78c2e-157">Microsoft Visual Studio/Build Tools 2015</span></span>                                             |
| <span data-ttu-id="78c2e-158">C # 5</span><span class="sxs-lookup"><span data-stu-id="78c2e-158">C# 5</span></span>       | <span data-ttu-id="78c2e-159">Microsoft Visual Studio/Build Tools 2012 或配套的 .NET Framework 4.5 編譯器</span><span class="sxs-lookup"><span data-stu-id="78c2e-159">Microsoft Visual Studio/Build Tools 2012 or bundled .NET Framework 4.5 compiler</span></span>      |
| <span data-ttu-id="78c2e-160">C# 4</span><span class="sxs-lookup"><span data-stu-id="78c2e-160">C# 4</span></span>       | <span data-ttu-id="78c2e-161">Microsoft Visual Studio/Build Tools 2010 或配套的 .NET Framework 4.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="78c2e-161">Microsoft Visual Studio/Build Tools 2010 or bundled .NET Framework 4.0 compiler</span></span>      |
| <span data-ttu-id="78c2e-162">C # 3</span><span class="sxs-lookup"><span data-stu-id="78c2e-162">C# 3</span></span>       | <span data-ttu-id="78c2e-163">Microsoft Visual Studio/Build Tools 2008 或配套的 .NET Framework 3.5 編譯器</span><span class="sxs-lookup"><span data-stu-id="78c2e-163">Microsoft Visual Studio/Build Tools 2008 or bundled .NET Framework 3.5 compiler</span></span>      |
| <span data-ttu-id="78c2e-164">C # 2</span><span class="sxs-lookup"><span data-stu-id="78c2e-164">C# 2</span></span>       | <span data-ttu-id="78c2e-165">Microsoft Visual Studio/Build Tools 2005 或配套的 .NET Framework 2.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="78c2e-165">Microsoft Visual Studio/Build Tools 2005 or bundled .NET Framework 2.0 compiler</span></span>      |
| <span data-ttu-id="78c2e-166">C # 1.0/1。2</span><span class="sxs-lookup"><span data-stu-id="78c2e-166">C# 1.0/1.2</span></span> | <span data-ttu-id="78c2e-167">Microsoft Visual Studio/Build Tools .NET 2002 或配套的 .NET Framework 1.0 編譯器</span><span class="sxs-lookup"><span data-stu-id="78c2e-167">Microsoft Visual Studio/Build Tools .NET 2002 or bundled .NET Framework 1.0 compiler</span></span> |

## <a name="see-also"></a><span data-ttu-id="78c2e-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78c2e-168">See also</span></span>

- [<span data-ttu-id="78c2e-169">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="78c2e-169">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="78c2e-170">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="78c2e-170">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
