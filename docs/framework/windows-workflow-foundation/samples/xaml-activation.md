---
title: "XAML 啟用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ac691e3d24e3526b43a6818fbe6bbb33a3375a7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="xaml-activation"></a><span data-ttu-id="ccf3a-102">XAML 啟用</span><span class="sxs-lookup"><span data-stu-id="ccf3a-102">XAML Activation</span></span>
<span data-ttu-id="ccf3a-103">這個範例示範如何在 IIS 中裝載宣告式工作流程。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-103">This sample demonstrates how to host a declarative workflow in IIS.</span></span> <span data-ttu-id="ccf3a-104">此範例是有一個作業的基本工作流程，名為 `EchoService`。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-104">The sample is a basic workflow called `EchoService` that has one operation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ccf3a-105">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ccf3a-106">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ccf3a-107">如果此目錄不存在，請移至 (下載頁面) 以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ccf3a-108">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ccf3a-109">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="ccf3a-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ccf3a-110">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 XAMLActivation.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-110">Open the XAMLActivation.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ccf3a-111">按下建置此方案**F5**。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-111">Build the solution by pressing **F5**.</span></span>  
  
3.  <span data-ttu-id="ccf3a-112">執行 WcfTestClient.exe。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-112">Run WcfTestClient.exe.</span></span> <span data-ttu-id="ccf3a-113">從命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ccf3a-113">From a command prompt, type in the following:</span></span>  
  
    1.  <span data-ttu-id="ccf3a-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span><span class="sxs-lookup"><span data-stu-id="ccf3a-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span></span>  
  
    2.  <span data-ttu-id="ccf3a-115">執行 WcfTestClient.exe。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-115">Run WcfTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="ccf3a-116">在 WcfTestClient.exe 設定服務位址，方式是按 CTRL+SHIFT+A，將服務位址設為 http://localhost:56133/Service.xamlx。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-116">Set the address of the service on WcfTestClient.exe by pressing CTRL+SHIFT+A and setting the service address to http://localhost:56133/Service.xamlx.</span></span>  
  
5.  <span data-ttu-id="ccf3a-117">執行 Echo 作業以測試服務。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-117">Perform the echo operation to test the service.</span></span>  
  
6.  <span data-ttu-id="ccf3a-118">在命令提示字元中，以系統管理員權限使用 DeployToIIS.Bat，以在 IIS 中部署服務。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-118">Deploy the Service in IIS using DeployToIIS.Bat in a command prompt with administrator privileges.</span></span>  
  
7.  <span data-ttu-id="ccf3a-119">將用戶端上的服務位址更新為 http://localhost/XAMLActivation/Service.xamlx，並且使用 WcfTestClient.exe 再次測試服務。</span><span class="sxs-lookup"><span data-stu-id="ccf3a-119">Update the service address in the client to http://localhost/XAMLActivation/Service.xamlx and test the service again using WcfTestClient.exe.</span></span>
