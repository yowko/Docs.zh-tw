---
title: "編譯 Interop 專案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8115df3159b715fbd01a15621c391cbe35612dfe
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2018
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="39283-102">編譯 Interop 專案</span><span class="sxs-lookup"><span data-stu-id="39283-102">Compiling an Interop Project</span></span>
<span data-ttu-id="39283-103">會編譯參考一或多個包含已匯入 COM 類型之組件的 COM Interop 專案，就像任何其他 Managed 專案一樣。</span><span class="sxs-lookup"><span data-stu-id="39283-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="39283-104">您可以參考 Visual Studio 這類開發環境中的 Interop 組件，也可以在使用命令列編譯器時參考它們。</span><span class="sxs-lookup"><span data-stu-id="39283-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="39283-105">在任一情況下，若要正常編譯，則 Interop 組件必須與其他專案檔位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="39283-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>  
  
 <span data-ttu-id="39283-106">有兩種方法可以參考 Interop 組件：</span><span class="sxs-lookup"><span data-stu-id="39283-106">There are two ways to reference interop assemblies:</span></span>  
  
-   <span data-ttu-id="39283-107">內嵌的 Interop 類型：從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 和 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 開始，您可以指示編譯器將 Interop 組件的類型資訊內嵌到可執行檔。</span><span class="sxs-lookup"><span data-stu-id="39283-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="39283-108">這是建議使用的技巧。</span><span class="sxs-lookup"><span data-stu-id="39283-108">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="39283-109">部署 Interop 組件：您可以建立 Interop 組件的標準參考。</span><span class="sxs-lookup"><span data-stu-id="39283-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="39283-110">在此情況下，Interop 組件必須與您的應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="39283-110">In this case, the interop assembly must be deployed with your application.</span></span>  
  
 <span data-ttu-id="39283-111">[在 Managed 程式碼中使用 COM 類型](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))會更詳細討論這兩種技術之間的差異。</span><span class="sxs-lookup"><span data-stu-id="39283-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).</span></span>  
  
 <span data-ttu-id="39283-112">[逐步解說：從 Microsoft Office 組件內嵌類型資訊](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)和 [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21) (逐步解說：從 Managed 組件內嵌類型) 示範如何使用 Visual Studio 內嵌 Interop 類型。</span><span class="sxs-lookup"><span data-stu-id="39283-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Type Information from Microsoft Office Assemblies](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) and [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="39283-113">若要參考具有命令列編譯器的 Interop 組件，以及在可執行檔中內嵌類型資訊，請使用 [/link (C# 編譯器選項)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) 或 [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) 編譯器參數，並指定 Interop 組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="39283-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39283-114">Visual C++ 應用程式無法內嵌類型資訊，但可以與執行的應用程式或增益集交互操作。</span><span class="sxs-lookup"><span data-stu-id="39283-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>  
  
 <span data-ttu-id="39283-115">若要在部署包含主要 Interop 組件的應用程式時進行編譯，請使用 **/reference** 編譯器參數，並指定 Interop 組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="39283-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39283-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="39283-116">See Also</span></span>  
 [<span data-ttu-id="39283-117">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="39283-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="39283-118">語言獨立性以及與語言無關的元件</span><span class="sxs-lookup"><span data-stu-id="39283-118">Language Independence and Language-Independent Components</span></span>](../../../docs/standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="39283-119">[在 Managed 程式碼中使用 COM 類型](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="39283-119">[Using COM Types in Managed Code](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))</span></span>  
 [<span data-ttu-id="39283-120">逐步解說：從 Microsoft Office 組件內嵌類型資訊</span><span class="sxs-lookup"><span data-stu-id="39283-120">Walkthrough: Embedding Type Information from Microsoft Office Assemblies</span></span>](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [<span data-ttu-id="39283-121">逐步解說：從 Managed 組件內嵌類型</span><span class="sxs-lookup"><span data-stu-id="39283-121">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="39283-122">匯入類型程式庫做為組件</span><span class="sxs-lookup"><span data-stu-id="39283-122">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
