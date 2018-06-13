---
title: 相互關聯計算機
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 77e13b3ca913d2432cfe5d4a95e83764effbb109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514137"
---
# <a name="correlated-calculator"></a><span data-ttu-id="0b6bc-102">相互關聯計算機</span><span class="sxs-lookup"><span data-stu-id="0b6bc-102">Correlated Calculator</span></span>
<span data-ttu-id="0b6bc-103">這個範例會示範如何在設計工具中使用訊息活動 (<xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply>) 並搭配以內容為主的相互關聯 (根據訊息中的參數)。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-103">This sample demonstrates how to use the messaging activities (<xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply>) in the designer with content-based correlation based on a parameter in the message.</span></span> <span data-ttu-id="0b6bc-104">在這個案例中，計算機的運算會在平行 Convoy 中。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-104">In this scenario, the operations of the calculator are in a parallel convoy.</span></span> <span data-ttu-id="0b6bc-105">當第一個訊息傳送給工作流程時，便會建立執行個體和相互關聯 (根據 `CalculatorId`)，而具有相同 `CalculatorId` 的後續訊息則會發送給該執行個體，直到呼叫 Reset 作業為止。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-105">Both an instance and a correlation (based on `CalculatorId`) are created when the first message is sent to the workflow, and subsequent messages with the same `CalculatorId` are dispatched to that instance until the Reset operation is called.</span></span> <span data-ttu-id="0b6bc-106">用戶端會實作為 WPF 應用程式，該應用程式會使用程式碼式用戶端 Proxy 來與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-106">The client is implemented as a WPF application that uses a code-based client proxy to communicate with the service.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="0b6bc-107">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="0b6bc-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="0b6bc-108">以更高的權限啟動 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]，並開啟 For.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-108">Start [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] in elevated permissions, open the For.sln solution file.</span></span>  
  
    1.  <span data-ttu-id="0b6bc-109">導覽至包含 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-109">Navigate to the folder that contains [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    2.  <span data-ttu-id="0b6bc-110">以滑鼠右鍵按一下 Devenv.exe，並選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-110">Right-click Devenv.exe and select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="0b6bc-111">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CorrelatedCalculator.sln 方案檔。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-111">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CorrelatedCalculator.sln solution file.</span></span>  
  
3.  <span data-ttu-id="0b6bc-112">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-112">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="0b6bc-113">若要執行服務專案，請按 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-113">To run the service project, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="0b6bc-114">一旦服務準備好接聽訊息，請在 [方案總管] 中，以滑鼠右鍵按一下用戶端專案，並執行此專案。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-114">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0b6bc-115">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0b6bc-116">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0b6bc-117">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0b6bc-118">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0b6bc-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`