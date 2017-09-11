---
title: "C# 編譯器選項"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.options
dev_langs:
- CSharp
helpviewer_keywords:
- compiler options [C#]
- csc.exe
- cl.exe compiler, C# options
- Visual C# compiler
- Visual C#, compiler options
ms.assetid: d3403556-1816-4546-a782-e8223a772e44
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 02cfb7708959057de593506db55e4f31f5ab4fd0
ms.openlocfilehash: 7c5f5274a5685e50fb7f1d06771b0340200d1c3f
ms.contentlocale: zh-tw
ms.lasthandoff: 08/28/2017

---
# <a name="c-compiler-options"></a><span data-ttu-id="18b81-102">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="18b81-102">C# Compiler Options</span></span>
<span data-ttu-id="18b81-103">編譯器會產生可執行檔 (.exe)、動態連結程式庫 (.dll) 或程式碼模組 (.netmodule)。</span><span class="sxs-lookup"><span data-stu-id="18b81-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>  
  
 <span data-ttu-id="18b81-104">每個編譯器選項都能以兩種形式使用︰**-option** 和 **/option**。</span><span class="sxs-lookup"><span data-stu-id="18b81-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="18b81-105">本文件只顯示 **/option** 形式。</span><span class="sxs-lookup"><span data-stu-id="18b81-105">The documentation only shows the **/option** form.</span></span>  
  
 <span data-ttu-id="18b81-106">在 Visual Web Developer 2008 中，您可以在 web.config 檔案中設定編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="18b81-106">In Visual Web Developer 2008, you set compiler options in the web.config file.</span></span> <span data-ttu-id="18b81-107">如需詳細資訊，請參閱 [\<compiler> 元素](https://msdn.microsoft.com/library/y9x69bzw)。</span><span class="sxs-lookup"><span data-stu-id="18b81-107">For more information, see [\<compiler> Element](https://msdn.microsoft.com/library/y9x69bzw).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="18b81-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="18b81-108">In This Section</span></span>  
 [<span data-ttu-id="18b81-109">使用 csc.exe 建置命令列</span><span class="sxs-lookup"><span data-stu-id="18b81-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 <span data-ttu-id="18b81-110">有關從命令列建置 Visual C# 應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="18b81-110">Information about building a Visual C# application from the command line.</span></span>  
  
 [<span data-ttu-id="18b81-111">如何：為 Visual Studio 命令列設定環境變數</span><span class="sxs-lookup"><span data-stu-id="18b81-111">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 <span data-ttu-id="18b81-112">提供執行 vsvars32.bat 來啟用命令列建置的步驟。</span><span class="sxs-lookup"><span data-stu-id="18b81-112">Provides steps for running vsvars32.bat  to enable command-line builds.</span></span>  
  
 [<span data-ttu-id="18b81-113">依分類列出的 C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="18b81-113">C# Compiler Options Listed by Category</span></span>](../../../csharp/language-reference/compiler-options/listed-by-category.md)  
 <span data-ttu-id="18b81-114">依分類列出編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="18b81-114">A categorical listing of the compiler options.</span></span>  
  
 [<span data-ttu-id="18b81-115">依字母順序列出 C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="18b81-115">C# Compiler Options Listed Alphabetically</span></span>](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)  
 <span data-ttu-id="18b81-116">依字母順序列出編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="18b81-116">An alphabetical listing of the compiler options.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="18b81-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="18b81-117">Related Sections</span></span>  
 [<span data-ttu-id="18b81-118">專案設計工具、建置頁</span><span class="sxs-lookup"><span data-stu-id="18b81-118">Build Page, Project Designer</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)  
 <span data-ttu-id="18b81-119">設定可控制如何編譯專案、建置及偵錯的屬性。</span><span class="sxs-lookup"><span data-stu-id="18b81-119">Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="18b81-120">包含有關在 Visual C# 專案中自訂建置步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="18b81-120">Includes information about custom build steps in Visual C# projects.</span></span>  
  
 [<span data-ttu-id="18b81-121">預設和自訂建置</span><span class="sxs-lookup"><span data-stu-id="18b81-121">Default and Custom Builds</span></span>](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 <span data-ttu-id="18b81-122">有關建置類型和組態的資訊。</span><span class="sxs-lookup"><span data-stu-id="18b81-122">Information on build types and configurations.</span></span>  
  
 [<span data-ttu-id="18b81-123">準備和管理建置</span><span class="sxs-lookup"><span data-stu-id="18b81-123">Preparing and Managing Builds</span></span>](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 <span data-ttu-id="18b81-124">在 Visual Studio 開發環境內建置的程序。</span><span class="sxs-lookup"><span data-stu-id="18b81-124">Procedures for building within the Visual Studio development environment.</span></span>

