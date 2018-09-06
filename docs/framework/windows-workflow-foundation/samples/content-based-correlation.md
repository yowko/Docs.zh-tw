---
title: 以內容為基礎的相互關聯
ms.date: 03/30/2017
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
ms.openlocfilehash: c0367f480701468dcd5024ea3439bdcd38acc78f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785813"
---
# <a name="content-based-correlation"></a><span data-ttu-id="55108-102">以內容為基礎的相互關聯</span><span class="sxs-lookup"><span data-stu-id="55108-102">Content-Based Correlation</span></span>
<span data-ttu-id="55108-103">這個範例示範訊息活動 (<xref:System.ServiceModel.Activities.Send>、<xref:System.ServiceModel.Activities.Receive>、<xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply>) 與多個內容架構相互關聯搭配使用的方式。</span><span class="sxs-lookup"><span data-stu-id="55108-103">This sample demonstrates how the messaging activities (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>) can be used with multiple content-based correlations.and content-based correlation.</span></span> <span data-ttu-id="55108-104">在這個案例中，根據採購單識別碼先初始化一個相互關聯，接著根據客戶識別碼建立另一個相互關聯。</span><span class="sxs-lookup"><span data-stu-id="55108-104">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span> <span data-ttu-id="55108-105">這示範 <xref:System.ServiceModel.Activities.Receive> 活動如何追蹤現有的相互關聯，以及根據相同的傳入訊息來初始化新的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="55108-105">This shows how a <xref:System.ServiceModel.Activities.Receive> activity can both follow an existing correlation and initialize a new correlation based on the same incoming message.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="55108-106">示範</span><span class="sxs-lookup"><span data-stu-id="55108-106">Demonstrates</span></span>  
 <span data-ttu-id="55108-107">訊息活動和內容架構相互關聯</span><span class="sxs-lookup"><span data-stu-id="55108-107">Messaging activities and content-based correlation</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="55108-108">討論</span><span class="sxs-lookup"><span data-stu-id="55108-108">Discussion</span></span>  
 <span data-ttu-id="55108-109">這個範例示範如何使用多個內容架構相互關聯。</span><span class="sxs-lookup"><span data-stu-id="55108-109">This sample shows how to use multiple content-based correlations.</span></span>  <span data-ttu-id="55108-110">在這個案例中，根據採購單識別碼先初始化一個相互關聯，接著根據客戶識別碼建立另一個相互關聯。</span><span class="sxs-lookup"><span data-stu-id="55108-110">In this scenario, a correlation is first initialized based on a purchase order ID, and then another correlation is created later based on the customer ID.</span></span>  <span data-ttu-id="55108-111">相互關聯是以 <xref:System.ServiceModel.Activities.Receive> 活動串聯，這個活動會追蹤現有的相互關聯 (PurchaseOrderId)，以及根據相同的傳入訊息來初始化新的相互關聯 (CustomerId)。</span><span class="sxs-lookup"><span data-stu-id="55108-111">The correlations are cascaded using a <xref:System.ServiceModel.Activities.Receive> activity that both follows an existing correlation (PurchaseOrderId) and initializes a new correlation (CustomerId) based on the same incoming message.</span></span>  <span data-ttu-id="55108-112"><xref:System.ServiceModel.Activities.Receive> 活動使用 <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>、<xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> 和 <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> 屬性來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="55108-112">To accomplish this, the <xref:System.ServiceModel.Activities.Receive> activity uses the <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> and <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="55108-113">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="55108-113">To use this sample</span></span>  
  
1.  <span data-ttu-id="55108-114">開啟[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]以提高的權限，以滑鼠右鍵按一下[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]圖示，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="55108-114">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="55108-115">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 CascadingCorrelation.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="55108-115">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CascadingCorrelation.sln solution file.</span></span>  
  
3.  <span data-ttu-id="55108-116">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="55108-116">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="55108-117">若要執行伺服器，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="55108-117">To run the server, press F5.</span></span>  
  
5.  <span data-ttu-id="55108-118">一旦服務準備好接聽訊息，請在 [方案總管] 中，以滑鼠右鍵按一下用戶端專案，並執行此專案。</span><span class="sxs-lookup"><span data-stu-id="55108-118">Once the service is ready and listening for messages, in Solution Explorer, right-click the Client project and run it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55108-119">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="55108-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="55108-120">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="55108-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55108-121">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="55108-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55108-122">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="55108-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`