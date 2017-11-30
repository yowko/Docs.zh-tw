---
title: "如何：將參考加入至類型程式庫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e5bbc99c3c40b0864a7c1c25cb79a3d7c26e3a86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="2b56a-102">如何：將參考加入至類型程式庫</span><span class="sxs-lookup"><span data-stu-id="2b56a-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="2b56a-103">Visual Studio 會產生內含新增類型程式庫參考時所產生之中繼資料的 interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2b56a-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="2b56a-104">如有提供主要的 Interop 組件，Visual Studio 便會先使用現有的組件，然後再產生新的 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2b56a-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="2b56a-105">新增 Visual Studio 中之類型程式庫的參考</span><span class="sxs-lookup"><span data-stu-id="2b56a-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="2b56a-106">若 Windows Setup.exe 未在您的電腦上安裝 COM DLL 或 EXE 檔案，請自行安裝。</span><span class="sxs-lookup"><span data-stu-id="2b56a-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="2b56a-107">依序選擇 [專案] 及 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="2b56a-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="2b56a-108">在 [參考管理員] 中，選擇 [COM]。</span><span class="sxs-lookup"><span data-stu-id="2b56a-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="2b56a-109">從清單中選取類型程式庫，或瀏覽至 .tlb 檔案。</span><span class="sxs-lookup"><span data-stu-id="2b56a-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="2b56a-110">選擇 [ **確定**]。</span><span class="sxs-lookup"><span data-stu-id="2b56a-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="2b56a-111">在方案總管中，開啟所新增之參考的捷徑功能表，然後選擇 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="2b56a-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="2b56a-112">在 [屬性] 視窗中，確定**內嵌 Interop 類型**屬性已設為 [True]。</span><span class="sxs-lookup"><span data-stu-id="2b56a-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="2b56a-113">這可讓 Visual Studio 將 COM 類型的類型資訊嵌入您的可執行檔中，免除將主要 Interop 組件部署到應用程式的動作。</span><span class="sxs-lookup"><span data-stu-id="2b56a-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b56a-114">功能表與對話方塊可能會隨您所使用的 Visual Studio 版本而不同。</span><span class="sxs-lookup"><span data-stu-id="2b56a-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="2b56a-115">新增類型程式庫參考供命令列編譯時使用</span><span class="sxs-lookup"><span data-stu-id="2b56a-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="2b56a-116">產生[如何：從型別程式庫產生 Interop 組件](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)中所述的 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="2b56a-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="2b56a-117">使用 [/link (C# 編譯器選項)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) 或 [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) 編譯器選項加上 Interop 組件名稱，將 COM 類型的類型資訊嵌入您的可執行檔中。</span><span class="sxs-lookup"><span data-stu-id="2b56a-117">Use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b56a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b56a-118">See Also</span></span>  
 [<span data-ttu-id="2b56a-119">匯入型別程式庫作為組件</span><span class="sxs-lookup"><span data-stu-id="2b56a-119">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [<span data-ttu-id="2b56a-120">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2b56a-120">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="2b56a-121">逐步解說：從 Microsoft Office 組件內嵌類型資訊</span><span class="sxs-lookup"><span data-stu-id="2b56a-121">Walkthrough: Embedding Type Information from Microsoft Office Assemblies</span></span>](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [<span data-ttu-id="2b56a-122">逐步解說：從 Managed 組件內嵌類型</span><span class="sxs-lookup"><span data-stu-id="2b56a-122">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="2b56a-123">/link (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="2b56a-123">/link (C# Compiler Options)</span></span>](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md)  
 [<span data-ttu-id="2b56a-124">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b56a-124">/link (Visual Basic)</span></span>](~/docs/visual-basic/reference/command-line-compiler/link.md)
