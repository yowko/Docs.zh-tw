---
title: C# 編譯器選項
ms.date: 07/20/2015
f1_keywords:
- cs.build.options
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
ms.openlocfilehash: a305daee2349341527b529c7556cc6fa84cc9fd2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="c-compiler-options"></a><span data-ttu-id="30846-102">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="30846-102">C# Compiler Options</span></span>
<span data-ttu-id="30846-103">編譯器會產生可執行檔 (.exe)、動態連結程式庫 (.dll) 或程式碼模組 (.netmodule)。</span><span class="sxs-lookup"><span data-stu-id="30846-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>  
  
 <span data-ttu-id="30846-104">每個編譯器選項都能以兩種形式使用︰**-option** 和 **/option**。</span><span class="sxs-lookup"><span data-stu-id="30846-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="30846-105">本文件只呈現 **-option** 形式。</span><span class="sxs-lookup"><span data-stu-id="30846-105">The documentation only shows the **-option** form.</span></span>  
  
 <span data-ttu-id="30846-106">在 Visual Studio 中，您可以在 web.config 檔案中設定編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="30846-106">In Visual Studio, you set compiler options in the web.config file.</span></span> <span data-ttu-id="30846-107">如需詳細資訊，請參閱 [\<compiler> 元素](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)。</span><span class="sxs-lookup"><span data-stu-id="30846-107">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30846-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="30846-108">In This Section</span></span>  
 [<span data-ttu-id="30846-109">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="30846-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 <span data-ttu-id="30846-110">有關從命令列建置 Visual C# 應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="30846-110">Information about building a Visual C# application from the command line.</span></span>  
  
 [<span data-ttu-id="30846-111">如何：為 Visual Studio 命令列設定環境變數</span><span class="sxs-lookup"><span data-stu-id="30846-111">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 <span data-ttu-id="30846-112">提供執行 vsvars32.bat 來啟用命令列建置的步驟。</span><span class="sxs-lookup"><span data-stu-id="30846-112">Provides steps for running vsvars32.bat  to enable command-line builds.</span></span>  
  
 [<span data-ttu-id="30846-113">依分類列出的 C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="30846-113">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 <span data-ttu-id="30846-114">依分類列出編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="30846-114">A categorical listing of the compiler options.</span></span>  
  
 [<span data-ttu-id="30846-115">依字母順序列出 C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="30846-115">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 <span data-ttu-id="30846-116">依字母順序列出編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="30846-116">An alphabetical listing of the compiler options.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="30846-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="30846-117">Related Sections</span></span>  
 [<span data-ttu-id="30846-118">專案設計工具、建置頁</span><span class="sxs-lookup"><span data-stu-id="30846-118">Build Page, Project Designer</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)  
 <span data-ttu-id="30846-119">設定可控制如何編譯專案、建置及偵錯的屬性。</span><span class="sxs-lookup"><span data-stu-id="30846-119">Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="30846-120">包含有關在 Visual C# 專案中自訂建置步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="30846-120">Includes information about custom build steps in Visual C# projects.</span></span>  
  
 [<span data-ttu-id="30846-121">預設和自訂建置</span><span class="sxs-lookup"><span data-stu-id="30846-121">Default and Custom Builds</span></span>](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 <span data-ttu-id="30846-122">有關建置類型和組態的資訊。</span><span class="sxs-lookup"><span data-stu-id="30846-122">Information on build types and configurations.</span></span>  
  
 [<span data-ttu-id="30846-123">準備和管理建置</span><span class="sxs-lookup"><span data-stu-id="30846-123">Preparing and Managing Builds</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="30846-124">在 Visual Studio 開發環境內建置的程序。</span><span class="sxs-lookup"><span data-stu-id="30846-124">Procedures for building within the Visual Studio development environment.</span></span>
