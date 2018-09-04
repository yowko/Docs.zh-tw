---
title: LINQ 訊息查詢相互關聯
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 7881140f2926bc27073a0be425a63566f313b50c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559075"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="a57cb-102">LINQ 訊息查詢相互關聯</span><span class="sxs-lookup"><span data-stu-id="a57cb-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="a57cb-103">這個範例示範如何使用自訂 <xref:System.ServiceModel.Dispatcher.MessageQuery> 實作 (而不是系統提供的 <xref:System.ServiceModel.XPathMessageQuery>) 來執行以內容為主的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="a57cb-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a57cb-104">示範</span><span class="sxs-lookup"><span data-stu-id="a57cb-104">Demonstrates</span></span>  
 <span data-ttu-id="a57cb-105">自訂 <xref:System.ServiceModel.Dispatcher.MessageQuery>、以內容為主的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="a57cb-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a57cb-106">討論</span><span class="sxs-lookup"><span data-stu-id="a57cb-106">Discussion</span></span>  
 <span data-ttu-id="a57cb-107">這個範例示範如何為了相互關聯，從 <xref:System.ServiceModel.Dispatcher.MessageQuery> 基底類別延伸。</span><span class="sxs-lookup"><span data-stu-id="a57cb-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="a57cb-108">`LinqMessageQuery` 自訂實作可讓使用者提供 XName，以使用 XLinq 在訊息中尋找。</span><span class="sxs-lookup"><span data-stu-id="a57cb-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="a57cb-109">查詢所擷取的資料是用來形成相互關聯索引鍵，以便將訊息分派至適當的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="a57cb-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a57cb-110">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="a57cb-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a57cb-111">這個範例使用 HTTP 端點公開工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="a57cb-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="a57cb-112">若要執行這個範例，適當的 URL Acl 必須加入 (請參閱[設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊)，是由系統管理員身分執行 Visual Studio 或執行下列命令，提高權限的提示來加入適當 Acl。</span><span class="sxs-lookup"><span data-stu-id="a57cb-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="a57cb-113">請確定您的網域和使用者名稱已用來取代。</span><span class="sxs-lookup"><span data-stu-id="a57cb-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="a57cb-114">一旦加入 URL ACL，請使用下列步驟。</span><span class="sxs-lookup"><span data-stu-id="a57cb-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="a57cb-115">建置方案。</span><span class="sxs-lookup"><span data-stu-id="a57cb-115">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="a57cb-116">設定多個啟始專案，以滑鼠右鍵按一下方案，然後選取**設定啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="a57cb-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="a57cb-117">新增**服務**並**用戶端**（依此順序） 做為多個啟始專案。</span><span class="sxs-lookup"><span data-stu-id="a57cb-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3.  <span data-ttu-id="a57cb-118">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a57cb-118">Run the application.</span></span> <span data-ttu-id="a57cb-119">用戶端主控台會顯示傳送訂單及接收採購單識別碼、後續確認訂單的工作流程。</span><span class="sxs-lookup"><span data-stu-id="a57cb-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="a57cb-120">服務視窗會顯示正在處理的要求。</span><span class="sxs-lookup"><span data-stu-id="a57cb-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a57cb-121">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a57cb-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a57cb-122">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a57cb-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a57cb-123">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="a57cb-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a57cb-124">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a57cb-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
