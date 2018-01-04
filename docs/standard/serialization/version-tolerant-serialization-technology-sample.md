---
title: "版本相容序列化技術範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a183664-bfbf-4ff0-96f6-c836284ea916
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9517abe23dba1b1b4b198fb8375e1ae35d8a2ca4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="version-tolerant-serialization-technology-sample"></a><span data-ttu-id="7c764-102">版本相容序列化技術範例</span><span class="sxs-lookup"><span data-stu-id="7c764-102">Version Tolerant Serialization Technology Sample</span></span>
[<span data-ttu-id="7c764-103">下載範例</span><span class="sxs-lookup"><span data-stu-id="7c764-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/VTS.zip.exe)  
  
 <span data-ttu-id="7c764-104">這個範例將示範.NET 序列化的版本相容功能。</span><span class="sxs-lookup"><span data-stu-id="7c764-104">This sample demonstrates the version tolerance features of .NET Serialization.</span></span> <span data-ttu-id="7c764-105">此範例會建置使用不同版本之 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 將資料序列化及還原序列化的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c764-105">The sample builds applications that use different versions of a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> to serialize and deserialize data.</span></span> <span data-ttu-id="7c764-106">雖然有不同型別的版本存在，這些應用程式還是能密切地互相通訊。</span><span class="sxs-lookup"><span data-stu-id="7c764-106">Despite the presence of different type versions, the applications communicate seamlessly.</span></span> <span data-ttu-id="7c764-107">如需詳細資訊，請參閱[版本相容序列化](../../../docs/standard/serialization/version-tolerant-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="7c764-107">For more information, see [Version Tolerant Serialization](../../../docs/standard/serialization/version-tolerant-serialization.md).</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="7c764-108">若要使用命令提示字元建置範例</span><span class="sxs-lookup"><span data-stu-id="7c764-108">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="7c764-109">開啟 [命令提示字元] 視窗，並巡覽至此範例的任一程式設計語言的子目錄 (V1 Application 或 V2 Application 底下)。</span><span class="sxs-lookup"><span data-stu-id="7c764-109">Open a Command Prompt window and navigate to one of the language-specific subdirectories (under V1 Application or V2 Application) for the sample.</span></span>  
  
2.  <span data-ttu-id="7c764-110">在命令列中輸入 **msbuild.exe \<本> application.sln** (其中 \<本> 為 v1 或 v2)。</span><span class="sxs-lookup"><span data-stu-id="7c764-110">Type **msbuild.exe \<ver> application.sln** at the command line (where \<ver> is either v1 or v2).</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="7c764-111">若要使用 Visual Studio 建置範例</span><span class="sxs-lookup"><span data-stu-id="7c764-111">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="7c764-112">開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，並巡覽至此範例任一程式設計語言的子目錄。</span><span class="sxs-lookup"><span data-stu-id="7c764-112">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="7c764-113">巡覽至您在前一個步驟選取之目錄的 [V1 Application] 子目錄。</span><span class="sxs-lookup"><span data-stu-id="7c764-113">Navigate to the V1 Application subdirectory of the directory you selected in the previous step.</span></span>  
  
3.  <span data-ttu-id="7c764-114">按兩下 V1 Application.sln 的圖示，在 Visual Studio 中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="7c764-114">Double-click the icon for V1 Application.sln to open the file in Visual Studio.</span></span>  
  
4.  <span data-ttu-id="7c764-115">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="7c764-115">On the **Build** menu, click **Build Solution**.</span></span>  
  
5.  <span data-ttu-id="7c764-116">巡覽至 [V2 Application] 子目錄，然後重複前兩個步驟，以建置 V2 Application。</span><span class="sxs-lookup"><span data-stu-id="7c764-116">Navigate to the V2 Application subdirectory and repeat the two previous steps to build the V2 Application.</span></span>  
  
 <span data-ttu-id="7c764-117">應用程式將建置於其個別專案目錄的預設 \bin 或 \bin\Debug 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="7c764-117">The applications will be built in the default \bin or \bin\Debug subdirectories of their respective project directories.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="7c764-118">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="7c764-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="7c764-119">在 [命令提示字元] 視窗中，巡覽至您建置範例應用程式時所選的語言特定子目錄。</span><span class="sxs-lookup"><span data-stu-id="7c764-119">In the Command Prompt window, navigate to the language-specific subdirectory that you selected when you built the sample applications.</span></span>  
  
2.  <span data-ttu-id="7c764-120">在命令列輸入 **runme.cmd**，同時執行兩個應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c764-120">Type **runme.cmd** at the command line to run both applications at once.</span></span>  
  
 <span data-ttu-id="7c764-121">或者，巡覽至新可執行檔所在的目錄，然後循序執行這些可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7c764-121">Alternatively, navigate to the directories that contain the new executables and run them sequentially.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c764-122">這個範例會建置一個主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="7c764-122">The sample builds console applications.</span></span> <span data-ttu-id="7c764-123">您必須在 [命令提示字元] 視窗中啟動及執行這些應用程式，才能檢視這些應用程式的輸出。</span><span class="sxs-lookup"><span data-stu-id="7c764-123">You must launch and run them in a Command Prompt window to view their output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c764-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c764-124">See Also</span></span>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.IO.FileStream>
