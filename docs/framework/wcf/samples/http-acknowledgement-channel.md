---
title: HTTP 要求認可通道
ms.date: 03/30/2017
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
ms.openlocfilehash: d83f3aa590471aa3d83b8f7bd1464ec1e6e106fc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559539"
---
# <a name="http-acknowledgement-channel"></a><span data-ttu-id="8daec-102">HTTP 要求認可通道</span><span class="sxs-lookup"><span data-stu-id="8daec-102">HTTP Acknowledgement Channel</span></span>
<span data-ttu-id="8daec-103">HTTP 確認通道 (HTTP Acknowledgement Channel) 是層次通道的一個範例，此通道可以變更單向訊息模式，讓服務確認或拒絕傳入訊息，而不會在收到後就自動傳送確認。</span><span class="sxs-lookup"><span data-stu-id="8daec-103">The HTTP Acknowledgement Channel is an example of a layered channel that changes the one-way messaging pattern, allowing a service to acknowledge or refuse incoming messages rather than automatically sending an acknowledgement on receipt.</span></span> <span data-ttu-id="8daec-104">HTTP 確認通道也會讓服務延遲確認，直到它可以保證商務層級的訊息將經過處理。</span><span class="sxs-lookup"><span data-stu-id="8daec-104">The HTTP Acknowledgement Channel also allows the service to delay acknowledgement until it can make a business-level guarantee that the message will be processed.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="8daec-105">示範</span><span class="sxs-lookup"><span data-stu-id="8daec-105">Demonstrates</span></span>  
 <span data-ttu-id="8daec-106"><xref:System.ServiceModel.Channels.ReceiveContext>，層次通道範例 (HTTP 確認通道)。</span><span class="sxs-lookup"><span data-stu-id="8daec-106"><xref:System.ServiceModel.Channels.ReceiveContext>, Layered channel example (HTTP Acknowledgement channel).</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="8daec-107">討論</span><span class="sxs-lookup"><span data-stu-id="8daec-107">Discussion</span></span>  
 <span data-ttu-id="8daec-108">HTTP 確認通道會實作 <xref:System.ServiceModel.Channels.ReceiveContext> 以便將 HTTP 要求-回覆訊息模式重設為具有延遲確認的單向模式。</span><span class="sxs-lookup"><span data-stu-id="8daec-108">The HTTP Acknowledgement Channel implements <xref:System.ServiceModel.Channels.ReceiveContext> to reshape the HTTP request-reply messaging pattern to a one-way pattern with delayed acknowledgement.</span></span> <span data-ttu-id="8daec-109">服務可以使用這個新模式確保在訊息處理完成之前，透過以 HTTP OK 狀態碼 200 的形式傳送確認處理的訊息沒有封鎖用戶端，也可以透過 HTTP 內部伺服器錯誤狀態碼 500 的形式傳送失敗訊息給用戶端。</span><span class="sxs-lookup"><span data-stu-id="8daec-109">Using this new pattern, a service can ensure message processing by sending an acknowledgement in the form of an HTTP OK status code of 200 without blocking the client until message processing completes or can send a failure message to the client in the form of an HTTP Internal Server error status code of 500.</span></span> <span data-ttu-id="8daec-110">例如，將訊息寫入佇列之後，服務可以傳送一個確認，然後以非同步方式繼續處理訊息。</span><span class="sxs-lookup"><span data-stu-id="8daec-110">For example, a service could send an acknowledgement after writing a message to a queue, and then continue processing the message asynchronously.</span></span> <span data-ttu-id="8daec-111">在此案例中，如果在用戶端收到來自服務的確認之前重新傳送每個訊息，可以確保其訊息至少處理過一次。</span><span class="sxs-lookup"><span data-stu-id="8daec-111">In this scenario, a client could be assured its messages were processed at least once by the service, if it re-sent each message until it received an acknowledgement from the service.</span></span> <span data-ttu-id="8daec-112">請注意，如果再沒有任何訊息處理保證的情況下，服務需要透過 HTTP 進行快速的非同步訊息處理，則 <xref:System.ServiceModel.Channels.OneWayBindingElement> 是更適當的選擇。</span><span class="sxs-lookup"><span data-stu-id="8daec-112">Note that, if a service requires fast asynchronous message processing over HTTP without any message processing guarantees, then the <xref:System.ServiceModel.Channels.OneWayBindingElement> is a more appropriate choice.</span></span>  
  
 <span data-ttu-id="8daec-113">在確定訊息是否可以在服務進行處理時，<xref:System.ServiceModel.Channels.ReceiveContext> 用來將訊息保存在妥善的位置。</span><span class="sxs-lookup"><span data-stu-id="8daec-113"><xref:System.ServiceModel.Channels.ReceiveContext> is used to hold the message in place while it is determined whether the message can be processed at the service.</span></span> <span data-ttu-id="8daec-114">服務是否可以成功處理訊息是透過在傳送 HTTP OK 狀態碼的 <xref:System.ServiceModel.Channels.ReceiveContext> 物件上呼叫 Complete 而定，而服務是否可以處理訊息，則是透過在傳送 HTTP 內部伺服器錯誤狀態碼的 <xref:System.ServiceModel.Channels.ReceiveContext> 物件上呼叫 `Abandon`’s <xref:System.ServiceModel.Channels.ReceiveContext> 方法而定。</span><span class="sxs-lookup"><span data-stu-id="8daec-114">The ability of a service to successfully process the message is indicated by calling Complete on the <xref:System.ServiceModel.Channels.ReceiveContext> object that sends an HTTP OK status code and whether the service can process the message is indicated by calling <xref:System.ServiceModel.Channels.ReceiveContext>’s `Abandon` method on the <xref:System.ServiceModel.Channels.ReceiveContext> object, which sends an HTTP Internal Server error status code.</span></span>  
  
 <span data-ttu-id="8daec-115">在此範例中，用戶端是透過傳送員工識別碼來要求處理資訊。</span><span class="sxs-lookup"><span data-stu-id="8daec-115">In this example, the client requests processing information by sending an employee ID.</span></span> <span data-ttu-id="8daec-116">如果在伺服器端收到的員工識別碼大於 50，服務會將 HTTP 狀態碼 500 (內部伺服器錯誤) 傳送回用戶端，否則，它會假設處理可以成功完成，然後將 HTTP 狀態碼 200 (成功) 傳送到用戶端。</span><span class="sxs-lookup"><span data-stu-id="8daec-116">On the service end, if the employee ID received is greater than 50, the service sends an HTTP Status code of 500 (Internal Server Error) back to the client, otherwise it is assumed that the processing can be successfully done and sends an HTTP Status code of 200 (Successful) to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8daec-117">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="8daec-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8daec-118">以系統管理員權限開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8daec-118">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with Administrator privileges.</span></span>  
  
2.  <span data-ttu-id="8daec-119">開啟**HttpAckChannel**解決方案。</span><span class="sxs-lookup"><span data-stu-id="8daec-119">Open the **HttpAckChannel** solution.</span></span>  
  
3.  <span data-ttu-id="8daec-120">啟動的新執行個體**服務**專案中的專案上按一下滑鼠右鍵**方案總管**，然後選取**偵錯**，**開始新執行個體**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="8daec-120">Start a new instance of the **Service** project by right clicking the project in **Solution Explorer**, and selecting **Debug**, **Start new instance** from the context menu.</span></span>  
  
4.  <span data-ttu-id="8daec-121">啟動的新執行個體**用戶端**專案中的專案上按一下滑鼠右鍵**方案總管**，然後選取**偵錯**，和**開始新執行個體**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="8daec-121">Start a new instance of the **Client** project by right clicking the project in **Solution Explorer**, and selecting **Debug**, and **Start new instance** from the context menu.</span></span>  
  
5.  <span data-ttu-id="8daec-122">一旦服務啟動後，按下用戶端視窗中的 ENTER，讓用戶端傳送訊息給服務。</span><span class="sxs-lookup"><span data-stu-id="8daec-122">Once the service has started, press ENTER in the client window to let the client send a message to the service.</span></span>  
  
6.  <span data-ttu-id="8daec-123">第一個訊息會在服務上進行處理，然後該服務會將 HTTP OK 狀態碼傳送回用戶端。</span><span class="sxs-lookup"><span data-stu-id="8daec-123">The first message is processed on the service, and it sends an HTTP OK status code back to the client.</span></span>  
  
7.  <span data-ttu-id="8daec-124">第二個訊息不成功，因此服務會將 HTTP 內部伺服器錯誤狀態碼傳送回用戶端，然後在用戶端上引發 <xref:System.ServiceModel.CommunicationException>。</span><span class="sxs-lookup"><span data-stu-id="8daec-124">The second message is unsuccessful, and it sends an HTTP Internal Server error status code back to the client, which raises a <xref:System.ServiceModel.CommunicationException> on the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8daec-125">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="8daec-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8daec-126">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="8daec-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8daec-127">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="8daec-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8daec-128">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="8daec-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
