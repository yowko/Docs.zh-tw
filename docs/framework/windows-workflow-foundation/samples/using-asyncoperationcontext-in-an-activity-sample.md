---
title: "使用活動中的 AsyncOperationContext 範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5aa36c3173e4e20d063f93b3583d063057b9bac7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="45b9d-102">使用活動中的 AsyncOperationContext 範例</span><span class="sxs-lookup"><span data-stu-id="45b9d-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="45b9d-103">這個範例示範如何開發自訂的 <xref:System.Activities.CodeActivity>，該活動會使用 <xref:System.Activities.AsyncCodeActivityContext> 在工作流程之外以非同步方式執行工作。</span><span class="sxs-lookup"><span data-stu-id="45b9d-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="45b9d-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="45b9d-104">Sample Details</span></span>  
 <span data-ttu-id="45b9d-105">範例活動會使用 <xref:System.IO.FileStream.BeginWrite%2A> 類別上的 <xref:System.IO.FileStream.EndWrite%2A> 和 <xref:System.IO.FileStream> 方法，以非同步方式將資料寫入檔案中。</span><span class="sxs-lookup"><span data-stu-id="45b9d-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="45b9d-106">此處介紹的模式可加以調整，以應用於其他非同步方法。</span><span class="sxs-lookup"><span data-stu-id="45b9d-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="45b9d-107">非同步作業執行時，工作流程中的其他活動也可以執行，不過工作流程無法保存。</span><span class="sxs-lookup"><span data-stu-id="45b9d-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="45b9d-108">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="45b9d-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="45b9d-109">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [Async.sln] 範例方案。</span><span class="sxs-lookup"><span data-stu-id="45b9d-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="45b9d-110">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="45b9d-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="45b9d-111">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="45b9d-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="45b9d-112">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="45b9d-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="45b9d-113">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="45b9d-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="45b9d-114">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="45b9d-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`