---
title: "相互關聯計算機"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d0d3c03b946a1f3805ea6e229e4019540b58286
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="correlated-calculator"></a><span data-ttu-id="b0162-102">相互關聯計算機</span><span class="sxs-lookup"><span data-stu-id="b0162-102">Correlated Calculator</span></span>
<span data-ttu-id="b0162-103">這個範例會示範如何在設計工具中使用訊息活動 (<xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply>) 並搭配以內容為主的相互關聯 (根據訊息中的參數)。</span><span class="sxs-lookup"><span data-stu-id="b0162-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="b0162-104">在這個案例中，計算機的運算會在平行 Convoy 中。</span><span class="sxs-lookup"><span data-stu-id="b0162-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="b0162-105">當第一個訊息傳送給工作流程時，便會建立執行個體和相互關聯 (根據 `CalculatorId`)，而具有相同 `CalculatorId` 的後續訊息則會發送給該執行個體，直到呼叫 Reset 作業為止。</span><span class="sxs-lookup"><span data-stu-id="b0162-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="b0162-106">用戶端會實作為 WPF 應用程式，該應用程式會使用程式碼式用戶端 Proxy 來與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="b0162-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b0162-107">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="b0162-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="b0162-108">以更高的權限啟動 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]，並開啟 For.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="b0162-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="b0162-109">導覽至包含 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="b0162-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="b0162-110">以滑鼠右鍵按一下 Devenv.exe，並選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="b0162-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="b0162-111">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CorrelatedCalculator.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="b0162-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="b0162-112">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="b0162-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="b0162-113">若要執行服務專案，請按 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="b0162-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="b0162-114">一旦服務準備好接聽訊息，請在 [方案總管] 中，以滑鼠右鍵按一下用戶端專案，並執行此專案。</span><span class="sxs-lookup"><span data-stu-id="b0162-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b0162-115">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b0162-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b0162-116">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="b0162-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b0162-117">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="b0162-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0162-118">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="b0162-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`  
  
## <a name="see-also"></a><span data-ttu-id="b0162-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0162-119">See Also</span></span>
