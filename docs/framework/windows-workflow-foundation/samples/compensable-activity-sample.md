---
title: 可補償的活動範例
ms.date: 03/30/2017
ms.assetid: 58f4898c-b2b8-44a4-9a73-3bef4da6d5ba
ms.openlocfilehash: 3bf1d120cd700830a98f53495f7e9989ffec73db
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46583323"
---
# <a name="compensable-activity-sample"></a><span data-ttu-id="9f66e-102">可補償的活動範例</span><span class="sxs-lookup"><span data-stu-id="9f66e-102">Compensable Activity Sample</span></span>
<span data-ttu-id="9f66e-103">這個範例示範如何使用 `CompensableActivity` 活動，定義一般執行期間針對給定動作所執行的工作，以及稍後如有需要，為了補償該動作所必須執行的工作。</span><span class="sxs-lookup"><span data-stu-id="9f66e-103">This sample demonstrates how to use the `CompensableActivity` activity to define the work to be done for a given action during normal execution and the work that is necessary to be done to compensate that action, if necessary at a later time.</span></span>  <span data-ttu-id="9f66e-104">此範例的第一個部分說明如何可補償工作單位可以定義在 Windows Workflow Foundation (WF) 使用`CompensableActivity`活動，並在成功執行的執行方式。</span><span class="sxs-lookup"><span data-stu-id="9f66e-104">The first part of the sample shows how units of compensable work can be defined in Windows Workflow Foundation (WF) using a `CompensableActivity` activity and how they are executed in a successful run.</span></span>  <span data-ttu-id="9f66e-105">範例的第二個部分示範當發生未預期的事件，工作流程執行個體取消時，相同的可補償工作單位如何自動處理補償。</span><span class="sxs-lookup"><span data-stu-id="9f66e-105">The second part of the sample shows how the same units of compensable work automatically take care of compensation when an unexpected event is hit and the workflow instance is canceled.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9f66e-106">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="9f66e-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9f66e-107">使用 Visual Studio 2010 開啟 CompensableActivity.sln。</span><span class="sxs-lookup"><span data-stu-id="9f66e-107">Using Visual Studio 2010, open the CompensableActivity.sln.</span></span>  
  
2.  <span data-ttu-id="9f66e-108">按 CTRL+SHIFT+B 建置此方案。</span><span class="sxs-lookup"><span data-stu-id="9f66e-108">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="9f66e-109">按 F5 鍵執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="9f66e-109">Run the application by pressing F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f66e-110">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="9f66e-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9f66e-111">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="9f66e-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9f66e-112">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="9f66e-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9f66e-113">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="9f66e-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\BasicCompensableActivity`