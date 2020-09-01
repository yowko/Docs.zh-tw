---
description: C# 編譯器選項
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
ms.openlocfilehash: bcb246055ecb553bbefad2a0d5c95bf6a083ee6f
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125523"
---
# <a name="c-compiler-options"></a><span data-ttu-id="75881-103">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="75881-103">C# Compiler Options</span></span>

<span data-ttu-id="75881-104">編譯器會產生可執行檔 (.exe)、動態連結程式庫 (.dll) 或程式碼模組 (.netmodule)。</span><span class="sxs-lookup"><span data-stu-id="75881-104">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="75881-105">每個編譯器選項都能以兩種形式使用︰**-option** 和 **/option**。</span><span class="sxs-lookup"><span data-stu-id="75881-105">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="75881-106">本文件只呈現 **-option** 形式。</span><span class="sxs-lookup"><span data-stu-id="75881-106">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="75881-107">在 Visual Studio 中，您可以在 *web.config* 檔中設定編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="75881-107">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="75881-108">如需詳細資訊，請參閱[ \<compiler> 元素](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)。</span><span class="sxs-lookup"><span data-stu-id="75881-108">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="75881-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="75881-109">In this section</span></span>

- <span data-ttu-id="75881-110">[使用 csc.exe的命令列建立 ](command-line-building-with-csc-exe.md) 從命令列建立 Visual c # 應用程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="75881-110">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="75881-111">[如何設定 Visual Studio 命令列的環境變數](how-to-set-environment-variables-for-the-visual-studio-command-line.md) 提供執行 *vsvars32.bat* 以啟用命令列組建的步驟。</span><span class="sxs-lookup"><span data-stu-id="75881-111">[How to set environment variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *vsvars32.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="75881-112">[依分類列出的 c # 編譯器選項](listed-by-category.md) 編譯器選項的類別清單。</span><span class="sxs-lookup"><span data-stu-id="75881-112">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="75881-113">依[字母順序列出的 c # 編譯器選項](listed-alphabetically.md)依字母順序列出的編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="75881-113">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="75881-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="75881-114">Related sections</span></span>

- <span data-ttu-id="75881-115">[專案設計工具、組建頁面](/visualstudio/ide/reference/build-page-project-designer-csharp) 設定可控制如何編譯、建立和調試專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="75881-115">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="75881-116">包含有關在 Visual C# 專案中自訂建置步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="75881-116">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="75881-117">[預設和自訂群組建](/visualstudio/ide/compiling-and-building-in-visual-studio) 組建類型和設定的資訊。</span><span class="sxs-lookup"><span data-stu-id="75881-117">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="75881-118">[準備和管理組建](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) 在 Visual Studio 開發環境內建立的程式。</span><span class="sxs-lookup"><span data-stu-id="75881-118">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
