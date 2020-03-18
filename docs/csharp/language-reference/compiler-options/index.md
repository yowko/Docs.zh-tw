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
ms.openlocfilehash: 787f9c5fff79eb67e2d74043782532c1fc4034b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73972754"
---
# <a name="c-compiler-options"></a><span data-ttu-id="64201-102">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="64201-102">C# Compiler Options</span></span>

<span data-ttu-id="64201-103">編譯器會產生可執行檔 (.exe)、動態連結程式庫 (.dll) 或程式碼模組 (.netmodule)。</span><span class="sxs-lookup"><span data-stu-id="64201-103">The compiler produces executable (.exe) files, dynamic-link libraries (.dll), or code modules (.netmodule).</span></span>

<span data-ttu-id="64201-104">每個編譯器選項都能以兩種形式使用︰**-option** 和 **/option**。</span><span class="sxs-lookup"><span data-stu-id="64201-104">Every compiler option is available in two forms: **-option** and **/option**.</span></span> <span data-ttu-id="64201-105">本文件只呈現 **-option** 形式。</span><span class="sxs-lookup"><span data-stu-id="64201-105">The documentation only shows the **-option** form.</span></span>

<span data-ttu-id="64201-106">在 Visual Studio 中，您可以在*Web.config 檔中*設置編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="64201-106">In Visual Studio, you set compiler options in the *web.config* file.</span></span> <span data-ttu-id="64201-107">有關詳細資訊，請參閱[\<編譯器>元素](../../../framework/configure-apps/file-schema/compiler/compiler-element.md)。</span><span class="sxs-lookup"><span data-stu-id="64201-107">For more information, see [\<compiler> Element](../../../framework/configure-apps/file-schema/compiler/compiler-element.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="64201-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="64201-108">In this section</span></span>

- <span data-ttu-id="64201-109">[命令列建設與 csc.exe](command-line-building-with-csc-exe.md)有關從命令列構建 Visual C# 應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="64201-109">[Command-line Building With csc.exe](command-line-building-with-csc-exe.md) Information about building a Visual C# application from the command line.</span></span>

- <span data-ttu-id="64201-110">[如何為視覺化工作室命令列設置環境變數](how-to-set-environment-variables-for-the-visual-studio-command-line.md)提供用於運行*vsvars32.bat*以啟用命令列生成的步驟。</span><span class="sxs-lookup"><span data-stu-id="64201-110">[How to set environment variables for the Visual Studio Command Line](how-to-set-environment-variables-for-the-visual-studio-command-line.md) Provides steps for running *vsvars32.bat* to enable command-line builds.</span></span>

- <span data-ttu-id="64201-111">[按類別列出的 C# 編譯器選項](listed-by-category.md)編譯器選項的分類清單。</span><span class="sxs-lookup"><span data-stu-id="64201-111">[C# Compiler Options Listed by Category](listed-by-category.md) A categorical listing of the compiler options.</span></span>

- <span data-ttu-id="64201-112">[C# 編譯器選項按字母順序列出](listed-alphabetically.md)編譯器選項的字母順序清單。</span><span class="sxs-lookup"><span data-stu-id="64201-112">[C# Compiler Options Listed Alphabetically](listed-alphabetically.md) An alphabetical listing of the compiler options.</span></span>

## <a name="related-sections"></a><span data-ttu-id="64201-113">相關章節</span><span class="sxs-lookup"><span data-stu-id="64201-113">Related sections</span></span>

- <span data-ttu-id="64201-114">[生成頁面，專案設計器](/visualstudio/ide/reference/build-page-project-designer-csharp)設置控制專案編譯、生成和調試方式的屬性。</span><span class="sxs-lookup"><span data-stu-id="64201-114">[Build Page, Project Designer](/visualstudio/ide/reference/build-page-project-designer-csharp) Setting properties that govern how your project is compiled, built, and debugged.</span></span> <span data-ttu-id="64201-115">包含有關在 Visual C# 專案中自訂建置步驟的資訊。</span><span class="sxs-lookup"><span data-stu-id="64201-115">Includes information about custom build steps in Visual C# projects.</span></span>

- <span data-ttu-id="64201-116">[預設和自訂生成](/visualstudio/ide/compiling-and-building-in-visual-studio)有關組建類型和配置的資訊。</span><span class="sxs-lookup"><span data-stu-id="64201-116">[Default and Custom Builds](/visualstudio/ide/compiling-and-building-in-visual-studio) Information on build types and configurations.</span></span>

- <span data-ttu-id="64201-117">[準備和管理生成](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)在視覺化工作室開發環境中構建的過程。</span><span class="sxs-lookup"><span data-stu-id="64201-117">[Preparing and Managing Builds](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) Procedures for building within the Visual Studio development environment.</span></span>
