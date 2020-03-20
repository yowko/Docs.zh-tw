---
title: 非同步通訊
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142872"
---
# <a name="asynchronous-communication"></a><span data-ttu-id="113a3-102">非同步通訊</span><span class="sxs-lookup"><span data-stu-id="113a3-102">Asynchronous Communication</span></span>
<span data-ttu-id="113a3-103">此示例演示如何在預設情況下非同步地完成兩個不同的 Windows 工作流基礎 （WF） 服務之間的通信。</span><span class="sxs-lookup"><span data-stu-id="113a3-103">This sample demonstrates how the communication between two different Windows Workflow Foundation (WF) services is done asynchronously by default.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="113a3-104">示範</span><span class="sxs-lookup"><span data-stu-id="113a3-104">Demonstrates</span></span>  
 <span data-ttu-id="113a3-105">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] 服務之間的非同步通訊。</span><span class="sxs-lookup"><span data-stu-id="113a3-105">Asynchronous communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] services.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="113a3-106">討論區</span><span class="sxs-lookup"><span data-stu-id="113a3-106">Discussion</span></span>  
 <span data-ttu-id="113a3-107">這個範例示範如何在 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 應用程式之間使用 .NET Framework 提供的訊息處理活動，以非同步方式進行通訊。</span><span class="sxs-lookup"><span data-stu-id="113a3-107">This sample shows how the communication between [!INCLUDE[wf1](../../../../includes/wf1-md.md)] applications is done asynchronously by using the messaging activities provided by .NET Framework.</span></span>  
  
 <span data-ttu-id="113a3-108">這個範例包含下列三個專案。</span><span class="sxs-lookup"><span data-stu-id="113a3-108">This sample consists of the following three projects.</span></span>  
  
 <span data-ttu-id="113a3-109">CreditCheckService</span><span class="sxs-lookup"><span data-stu-id="113a3-109">CreditCheckService</span></span>  
 <span data-ttu-id="113a3-110">這項服務會接受特定人員的信用得分，或是要擷取的項目值，然後決定是否給予該人員信用額度。</span><span class="sxs-lookup"><span data-stu-id="113a3-110">This service receives the credit score of a particular person or the value of the item to acquire, and then decides whether the credit is given to the person.</span></span>  
  
 <span data-ttu-id="113a3-111">RentalApprovalService</span><span class="sxs-lookup"><span data-stu-id="113a3-111">RentalApprovalService</span></span>  
 <span data-ttu-id="113a3-112">這項服務會接收需要一些信用額度的人提出的申請。</span><span class="sxs-lookup"><span data-stu-id="113a3-112">This service receives an application from a person who is in need of some credit.</span></span> <span data-ttu-id="113a3-113">這項服務會以非同步方式與 `CreditCheckService` 進行通訊，決定信用額度申請是否有效。</span><span class="sxs-lookup"><span data-stu-id="113a3-113">This service communicates asynchronously with the `CreditCheckService` to decide whether the credit application is valid.</span></span>  
  
 <span data-ttu-id="113a3-114">Client</span><span class="sxs-lookup"><span data-stu-id="113a3-114">Client</span></span>  
 <span data-ttu-id="113a3-115">Client 會以同步方式與 `RentalApprovalService` 進行通訊，了解信用額度是否核准。</span><span class="sxs-lookup"><span data-stu-id="113a3-115">The client communicates synchronously with the `RentalApprovalService` to know whether the credit is approved.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="113a3-116">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="113a3-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="113a3-117">按右鍵**非同步通信**解決方案並選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="113a3-117">Right-click the **AsynchronousCommunication** solution and select **Properties**.</span></span>  
  
2. <span data-ttu-id="113a3-118">在 **"通用屬性**"中，選擇**啟動專案**，然後選擇**多個啟動專案**。</span><span class="sxs-lookup"><span data-stu-id="113a3-118">In **Common Properties**, select **Startup Project**, and select **Multiple Startup Projects**.</span></span>  
  
3. <span data-ttu-id="113a3-119">將**租賃批准服務**移到清單中的第一個位置，後跟**CreditCheck 服務**，後跟**客戶**。</span><span class="sxs-lookup"><span data-stu-id="113a3-119">Move **RentalApprovalService** to the first position in the list, followed by **CreditCheckService**, followed by **Client**.</span></span> <span data-ttu-id="113a3-120">為所有三個專案設置 **"開始"** 操作。</span><span class="sxs-lookup"><span data-stu-id="113a3-120">Set the **Start** action on all three projects.</span></span>  
  
4. <span data-ttu-id="113a3-121">按一下 **"確定**"，然後按 F5 以運行示例。</span><span class="sxs-lookup"><span data-stu-id="113a3-121">Click **OK**, and press F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="113a3-122">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="113a3-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="113a3-123">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="113a3-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="113a3-124">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="113a3-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="113a3-125">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="113a3-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
