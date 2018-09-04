---
title: SendParameters 及 ReceiveParameters 活動的基本使用
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: c13999ad1571a6413e30e801b6c642000f8e4654
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504004"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a><span data-ttu-id="04653-102">SendParameters 及 ReceiveParameters 活動的基本使用</span><span class="sxs-lookup"><span data-stu-id="04653-102">Basic Usage of SendParameters and ReceiveParameters Activities</span></span>
<span data-ttu-id="04653-103">這個範例示範 <xref:System.ServiceModel.Activities.SendParametersContent> 和 <xref:System.ServiceModel.Activities.ReceiveParametersContent> 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="04653-103">This sample shows the use of <xref:System.ServiceModel.Activities.SendParametersContent> and <xref:System.ServiceModel.Activities.ReceiveParametersContent> activities.</span></span> <span data-ttu-id="04653-104">服務會公開依向作業，該作業會使用字串引數並將輸入 echo 至用戶端。</span><span class="sxs-lookup"><span data-stu-id="04653-104">The service exposes one operation that takes a string argument and echoes the input back to the client.</span></span> <span data-ttu-id="04653-105">這個範例將示範如何設定這些訊息處理活動的參數。</span><span class="sxs-lookup"><span data-stu-id="04653-105">The sample shows how to set up the parameters for these messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="04653-106">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="04653-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="04653-107">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="04653-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="04653-108">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="04653-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04653-109">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="04653-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a><span data-ttu-id="04653-110">使用這個範例</span><span class="sxs-lookup"><span data-stu-id="04653-110">Using this sample</span></span>  
  
1.  <span data-ttu-id="04653-111">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中載入專案方案，然後建立專案。</span><span class="sxs-lookup"><span data-stu-id="04653-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="04653-112">請先執行 [方案基底目錄]\EchoWorkflowService\bin\debug 中產生的 EchoWorkflowService 應用程式。</span><span class="sxs-lookup"><span data-stu-id="04653-112">First run the EchoWorkflowService application generated in [solution base directory]\EchoWorkflowService\bin\debug.</span></span>  
  
3.  <span data-ttu-id="04653-113">接著執行 [方案基底目錄]\EchoWorkflowClient\bin\debug 中產生的 EchoWorkflowClient 應用程式。</span><span class="sxs-lookup"><span data-stu-id="04653-113">Second, run the EchoWorkflowClient application generated in [solution base directory]\EchoWorkflowClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="04653-114">用戶端會在服務上呼叫 Echo 作業並列印結果。</span><span class="sxs-lookup"><span data-stu-id="04653-114">The client calls Echo operation on the service and prints the results.</span></span> <span data-ttu-id="04653-115">完成時，按下 ENTER 結束用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="04653-115">When complete, press ENTER to exit the client and then the service.</span></span>