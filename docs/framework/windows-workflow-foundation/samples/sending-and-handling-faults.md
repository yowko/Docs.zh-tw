---
title: 傳送及處理錯誤
ms.date: 03/30/2017
ms.assetid: 98e8e04d-2ac9-4a33-ae08-462f757a7a14
ms.openlocfilehash: 896f209e7daeeab2bb33c1fde15298aae96c8776
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406654"
---
# <a name="sending-and-handling-faults"></a><span data-ttu-id="6196a-102">傳送及處理錯誤</span><span class="sxs-lookup"><span data-stu-id="6196a-102">Sending and Handling Faults</span></span>
<span data-ttu-id="6196a-103">這個範例示範如何使用 <xref:System.ServiceModel.Activities.SendReply> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 訊息活動，傳送及接收預期和非預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6196a-103">This sample demonstrates how to use the <xref:System.ServiceModel.Activities.SendReply> and <xref:System.ServiceModel.Activities.ReceiveReply> messaging activities to send and receive expected and unexpected faults.</span></span> <span data-ttu-id="6196a-104">在這個案例中，第一個用戶端要求產生已包含在 <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> 集合中的預期錯誤。</span><span class="sxs-lookup"><span data-stu-id="6196a-104">In this scenario, the first client request results in an expected fault that has been included in its <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> collection.</span></span> <span data-ttu-id="6196a-105">後面幾個用戶端要求會在最終要求成功之前產生非預期的錯誤。</span><span class="sxs-lookup"><span data-stu-id="6196a-105">The next few client requests result in receiving unexpected faults, before the final request succeeds.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="6196a-106">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="6196a-106">To use this sample</span></span>  
  
1.  <span data-ttu-id="6196a-107">開啟[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]以提高的權限，以滑鼠右鍵按一下[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]圖示，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="6196a-107">Open [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="6196a-108">開啟 Faults.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="6196a-108">Open the Faults.sln solution file.</span></span>  
  
3.  <span data-ttu-id="6196a-109">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="6196a-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="6196a-110">執行服務專案。</span><span class="sxs-lookup"><span data-stu-id="6196a-110">Run the service project.</span></span>  
  
    1.  <span data-ttu-id="6196a-111">在 **方案總管**，以滑鼠右鍵按一下`FaultService`專案，然後選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="6196a-111">In **Solution Explorer**, right-click the `FaultService` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="6196a-112">按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="6196a-112">Press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="6196a-113">開啟另一份[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]以提高的權限，以滑鼠右鍵按一下[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]圖示，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="6196a-113">Open another copy of [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with elevated permissions, by right-clicking the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] icon and selecting **Run as administrator**.</span></span>  
  
6.  <span data-ttu-id="6196a-114">開啟 Faults.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="6196a-114">Open the Faults.sln solution file.</span></span>  
  
7.  <span data-ttu-id="6196a-115">執行用戶端專案。</span><span class="sxs-lookup"><span data-stu-id="6196a-115">Run the client project.</span></span>  
  
    1.  <span data-ttu-id="6196a-116">在 **方案總管**，以滑鼠右鍵按一下`FaultClient`專案，然後選取**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="6196a-116">In **Solution Explorer**, right-click the `FaultClient` project and select **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="6196a-117">按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="6196a-117">Press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6196a-118">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="6196a-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6196a-119">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="6196a-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6196a-120">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="6196a-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6196a-121">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="6196a-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Faults`