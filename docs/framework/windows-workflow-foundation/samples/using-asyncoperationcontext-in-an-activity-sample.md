---
title: 使用活動中的 AsyncOperationContext 範例
ms.date: 03/30/2017
ms.assetid: 0888a0bd-d227-4c00-ad6a-b654a01740e8
ms.openlocfilehash: 4358a364a3f7ec69b7c1c548fcf82fe494f37505
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196903"
---
# <a name="using-asyncoperationcontext-in-an-activity-sample"></a><span data-ttu-id="0cce2-102">使用活動中的 AsyncOperationContext 範例</span><span class="sxs-lookup"><span data-stu-id="0cce2-102">Using AsyncOperationContext in an Activity Sample</span></span>
<span data-ttu-id="0cce2-103">這個範例示範如何開發自訂的 <xref:System.Activities.CodeActivity>，該活動會使用 <xref:System.Activities.AsyncCodeActivityContext> 在工作流程之外以非同步方式執行工作。</span><span class="sxs-lookup"><span data-stu-id="0cce2-103">This sample demonstrates how to develop a custom <xref:System.Activities.CodeActivity> that uses <xref:System.Activities.AsyncCodeActivityContext> to perform work asynchronously outside of the workflow.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="0cce2-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="0cce2-104">Sample Details</span></span>  
 <span data-ttu-id="0cce2-105">範例活動會使用 <xref:System.IO.FileStream.BeginWrite%2A> 類別上的 <xref:System.IO.FileStream.EndWrite%2A> 和 <xref:System.IO.FileStream> 方法，以非同步方式將資料寫入檔案中。</span><span class="sxs-lookup"><span data-stu-id="0cce2-105">The sample activity uses the <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.EndWrite%2A> methods on the <xref:System.IO.FileStream> class to asynchronously write data to a file.</span></span> <span data-ttu-id="0cce2-106">此處介紹的模式可加以調整，以應用於其他非同步方法。</span><span class="sxs-lookup"><span data-stu-id="0cce2-106">The pattern introduced here can be adapted for use with other asynchronous methods.</span></span> <span data-ttu-id="0cce2-107">非同步作業執行時，工作流程中的其他活動也可以執行，不過工作流程無法保存。</span><span class="sxs-lookup"><span data-stu-id="0cce2-107">While the asynchronous operation is executing, other activities in the workflow can execute, but the workflow cannot be persisted.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0cce2-108">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="0cce2-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0cce2-109">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [Async.sln] 範例方案。</span><span class="sxs-lookup"><span data-stu-id="0cce2-109">Open the Async.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="0cce2-110">建置並執行方案。</span><span class="sxs-lookup"><span data-stu-id="0cce2-110">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0cce2-111">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0cce2-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0cce2-112">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0cce2-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0cce2-113">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0cce2-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0cce2-114">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0cce2-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\Async`