---
title: 非同步通訊
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: 28b325a6bd870282577a2989b616628d52262deb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711854"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="aa8f4-102">非同步通訊</span><span class="sxs-lookup"><span data-stu-id="aa8f4-102">Asynchronous Communication</span></span>
<span data-ttu-id="aa8f4-103">這個範例會示範兩個不同 Windows Workflow Foundation （WF）服務之間的通訊預設如何以非同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="aa8f4-104">示範</span><span class="sxs-lookup"><span data-stu-id="aa8f4-104">Demonstrates</span></span>  
 <span data-ttu-id="aa8f4-105">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] 服務之間的非同步通訊。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="aa8f4-106">討論</span><span class="sxs-lookup"><span data-stu-id="aa8f4-106">Discussion</span></span>  
 <span data-ttu-id="aa8f4-107">這個範例示範如何在 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 應用程式之間使用 .NET Framework 提供的訊息處理活動，以非同步方式進行通訊。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="aa8f4-108">這個範例包含下列三個專案。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="aa8f4-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="aa8f4-109">CreditCheckService</span></span>  
 <span data-ttu-id="aa8f4-110">這項服務會接受特定人員的信用得分，或是要擷取的項目值，然後決定是否給予該人員信用額度。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="aa8f4-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="aa8f4-111">RentalApprovalService</span></span>  
 <span data-ttu-id="aa8f4-112">這項服務會接收需要一些信用額度的人提出的申請。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="aa8f4-113">這項服務會以非同步方式與 `CreditCheckService` 進行通訊，決定信用額度申請是否有效。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="aa8f4-114">Client</span><span class="sxs-lookup"><span data-stu-id="aa8f4-114">Client</span></span>  
 <span data-ttu-id="aa8f4-115">Client 會以同步方式與 `RentalApprovalService` 進行通訊，了解信用額度是否核准。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aa8f4-116">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="aa8f4-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="aa8f4-117">以滑鼠右鍵按一下 [ **AsynchronousCommunication** ] 方案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="aa8f4-118">在 [**通用屬性**] 中，選取 [**啟始專案**]，然後選取 [**多個啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="aa8f4-119">將**RentalApprovalService**移至清單中的第一個位置，後面接著**CreditCheckService**，接著**用戶端**。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="aa8f4-120">在所有三個專案上設定 [**啟動**] 動作。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="aa8f4-121">按一下 **[確定]** ，然後按 F5 執行範例。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="aa8f4-122">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aa8f4-123">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-123">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="aa8f4-124">如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aa8f4-125">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="aa8f4-125">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
