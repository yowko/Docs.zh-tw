---
title: 編譯 Interop 專案
description: 回顧如何編譯 COM Interop 專案，如果它們參考一個或多個包含已匯入 COM 類型的元件，就會編譯為 managed 專案。
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
ms.openlocfilehash: a8dfbeb88d0057eb3c9047b4435f021750ed86d2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620855"
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="4159b-103">編譯 Interop 專案</span><span class="sxs-lookup"><span data-stu-id="4159b-103">Compiling an Interop Project</span></span>

<span data-ttu-id="4159b-104">會編譯參考一或多個包含已匯入 COM 類型之組件的 COM Interop 專案，就像任何其他 Managed 專案一樣。</span><span class="sxs-lookup"><span data-stu-id="4159b-104">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="4159b-105">您可以參考 Visual Studio 這類開發環境中的 Interop 組件，也可以在使用命令列編譯器時參考它們。</span><span class="sxs-lookup"><span data-stu-id="4159b-105">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="4159b-106">在任一情況下，若要正常編譯，則 Interop 組件必須與其他專案檔位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="4159b-106">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>

 <span data-ttu-id="4159b-107">有兩種方法可以參考 Interop 組件：</span><span class="sxs-lookup"><span data-stu-id="4159b-107">There are two ways to reference interop assemblies:</span></span>

- <span data-ttu-id="4159b-108">內嵌的 interop 類型：從 .NET Framework 4 和 Visual Studio 2010 開始，您可以指示編譯器將 interop 元件的類型資訊內嵌到可執行檔。</span><span class="sxs-lookup"><span data-stu-id="4159b-108">Embedded interop types: Beginning with the .NET Framework 4 and Visual Studio 2010, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="4159b-109">這是建議使用的技巧。</span><span class="sxs-lookup"><span data-stu-id="4159b-109">This is the recommended technique.</span></span>

- <span data-ttu-id="4159b-110">部署 Interop 組件：您可以建立 Interop 組件的標準參考。</span><span class="sxs-lookup"><span data-stu-id="4159b-110">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="4159b-111">在此情況下，Interop 組件必須與您的應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="4159b-111">In this case, the interop assembly must be deployed with your application.</span></span>

 <span data-ttu-id="4159b-112">[在 Managed 程式碼中使用 COM 類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))會更詳細討論這兩種技術之間的差異。</span><span class="sxs-lookup"><span data-stu-id="4159b-112">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>

 <span data-ttu-id="4159b-113">Visual Studio 的內嵌 interop 類型會在[逐步解說：從 Visual Studio 中的 Managed 元件內嵌類型](../../standard/assembly/embed-types-visual-studio.md)中示範。</span><span class="sxs-lookup"><span data-stu-id="4159b-113">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Types from Managed Assemblies in Visual Studio](../../standard/assembly/embed-types-visual-studio.md).</span></span>

 <span data-ttu-id="4159b-114">若要使用命令列編譯器來參考 interop 元件，並在可執行檔中內嵌類型資訊，請使用[-link （c # 編譯器選項）](../../csharp/language-reference/compiler-options/link-compiler-option.md)或[-link （Visual Basic）](../../visual-basic/reference/command-line-compiler/link.md)編譯器參數，並指定 interop 元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="4159b-114">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or the [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="4159b-115">Visual C++ 應用程式無法內嵌類型資訊，但可以與執行的應用程式或增益集交互操作。</span><span class="sxs-lookup"><span data-stu-id="4159b-115">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>

 <span data-ttu-id="4159b-116">若要在部署包含主要 Interop 組件的應用程式時進行編譯，請使用 **/reference** 編譯器參數，並指定 Interop 組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="4159b-116">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="4159b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4159b-117">See also</span></span>

- [<span data-ttu-id="4159b-118">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4159b-118">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="4159b-119">語言獨立性以及與語言無關的元件</span><span class="sxs-lookup"><span data-stu-id="4159b-119">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- <span data-ttu-id="4159b-120">[在受控程式碼中使用 COM 型別](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4159b-120">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="4159b-121">逐步解說：在 Visual Studio 中內嵌來自 Managed 組件的型別</span><span class="sxs-lookup"><span data-stu-id="4159b-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="4159b-122">匯入類型程式庫做為組件</span><span class="sxs-lookup"><span data-stu-id="4159b-122">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
