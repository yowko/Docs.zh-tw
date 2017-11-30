---
title: "設計模式：以清單為基礎的發行訂閱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f3f5b9f8b07083c46ad98ce6e8ab6b5d3242e05
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="f1879-102">設計模式：以清單為基礎的發行訂閱</span><span class="sxs-lookup"><span data-stu-id="f1879-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="f1879-103">這個範例說明實作成為 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 程式的清單架構發行訂閱模式。</span><span class="sxs-lookup"><span data-stu-id="f1879-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1879-104">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="f1879-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f1879-105">描述的清單架構發行訂閱設計模式在 Microsoft Patterns & Practices 發行[整合模式](http://go.microsoft.com/fwlink/?LinkId=95894)。</span><span class="sxs-lookup"><span data-stu-id="f1879-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](http://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="f1879-106">發行訂閱模式會傳遞資訊給已訂閱某個資訊主題的收件者集合。</span><span class="sxs-lookup"><span data-stu-id="f1879-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="f1879-107">以清單為基礎的發行訂閱會維護訂閱者的清單。</span><span class="sxs-lookup"><span data-stu-id="f1879-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="f1879-108">當有要分享的資訊時，清單上的每個訂閱者都會接獲一份複本。</span><span class="sxs-lookup"><span data-stu-id="f1879-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="f1879-109">這個範例示範動態的清單架構發行訂閱模式，用戶端可以視需要在這裡訂閱或取消訂閱。</span><span class="sxs-lookup"><span data-stu-id="f1879-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="f1879-110">以清單為基礎的發行訂閱範例是由用戶端、服務和資料來源程式所組成。</span><span class="sxs-lookup"><span data-stu-id="f1879-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="f1879-111">可以有一個以上的用戶端和一個以上的資料來源程式在其中執行。</span><span class="sxs-lookup"><span data-stu-id="f1879-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="f1879-112">用戶端會訂閱服務、接收通知和取消訂閱。</span><span class="sxs-lookup"><span data-stu-id="f1879-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="f1879-113">資料來源程式會將資訊傳送至服務，以供目前所有訂閱者分享。</span><span class="sxs-lookup"><span data-stu-id="f1879-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="f1879-114">在這個範例中，用戶端和資料來源是主控台程式 (.exe 檔案)，而服務是裝載於網際網路資訊服務 (IIS) 的程式庫 (.dll) 。</span><span class="sxs-lookup"><span data-stu-id="f1879-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="f1879-115">您可以在桌面上看見用戶端和資料來源活動。</span><span class="sxs-lookup"><span data-stu-id="f1879-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="f1879-116">服務會使用雙工通訊。</span><span class="sxs-lookup"><span data-stu-id="f1879-116">The service uses duplex communication.</span></span> <span data-ttu-id="f1879-117">`ISampleContract` 服務合約會和 `ISampleClientCallback` 回呼合約配成一組。</span><span class="sxs-lookup"><span data-stu-id="f1879-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="f1879-118">服務會實作用戶端用來加入或離開訂閱者清單的訂閱與取消訂閱服務作業。</span><span class="sxs-lookup"><span data-stu-id="f1879-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="f1879-119">服務還會實作 `PublishPriceChange` 服務作業，資料來源程式將呼叫此作業以提供新資訊給服務。</span><span class="sxs-lookup"><span data-stu-id="f1879-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="f1879-120">用戶端程式會實作 `PriceChange` 服務作業，服務將呼叫此作業以通知所有訂閱者關於價格的變更。</span><span class="sxs-lookup"><span data-stu-id="f1879-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
```  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,   
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 <span data-ttu-id="f1879-121">服務會使用 .NET Framework 事件做為告知所有訂閱者新資訊的機制。</span><span class="sxs-lookup"><span data-stu-id="f1879-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="f1879-122">當用戶端呼叫訂閱以加入服務時，它會提供事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f1879-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="f1879-123">當用戶端離開時，則會從事件取消訂閱其事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="f1879-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="f1879-124">當資料來源呼叫服務以報告價格變更時，服務會引發事件。</span><span class="sxs-lookup"><span data-stu-id="f1879-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="f1879-125">這會呼叫服務的每個執行個體 (每個已訂閱的用戶端各一個)，而促使其事件處理常式開始執行。</span><span class="sxs-lookup"><span data-stu-id="f1879-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="f1879-126">每個事件處理常式都會透過各自的回呼函式，傳遞資訊至其用戶端。</span><span class="sxs-lookup"><span data-stu-id="f1879-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
```  
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is deregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 <span data-ttu-id="f1879-127">當您執行範例時，請啟動數個用戶端。</span><span class="sxs-lookup"><span data-stu-id="f1879-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="f1879-128">用戶端會訂閱服務，</span><span class="sxs-lookup"><span data-stu-id="f1879-128">The clients subscribe to the service.</span></span> <span data-ttu-id="f1879-129">然後執行資料來源程式，後者再將資訊傳送給服務。</span><span class="sxs-lookup"><span data-stu-id="f1879-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="f1879-130">服務則傳遞資訊給所有訂閱者。</span><span class="sxs-lookup"><span data-stu-id="f1879-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="f1879-131">您可以看見每個用戶端主控台上的活動，確認已收到資訊。</span><span class="sxs-lookup"><span data-stu-id="f1879-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="f1879-132">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="f1879-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="f1879-133">若要設定和建置範例</span><span class="sxs-lookup"><span data-stu-id="f1879-133">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="f1879-134">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="f1879-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f1879-135">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="f1879-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="f1879-136">若要在同一部機器上執行範例</span><span class="sxs-lookup"><span data-stu-id="f1879-136">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="f1879-137">輸入下列位址，測試您是否可以使用瀏覽器存取服務：http://localhost/servicemodelsamples/service.svc。</span><span class="sxs-lookup"><span data-stu-id="f1879-137">Test that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="f1879-138">確認頁面應該會顯示在回應中。</span><span class="sxs-lookup"><span data-stu-id="f1879-138">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="f1879-139">從 \client\bin 執行 Client.exe\\，將語言特定資料夾下。</span><span class="sxs-lookup"><span data-stu-id="f1879-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="f1879-140">用戶端活動會顯示在用戶端主控台視窗上。</span><span class="sxs-lookup"><span data-stu-id="f1879-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="f1879-141">啟動數個用戶端。</span><span class="sxs-lookup"><span data-stu-id="f1879-141">Launch several clients.</span></span>  
  
3.  <span data-ttu-id="f1879-142">執行 \datasource\bin Datasource.exe\\，將語言特定資料夾下。</span><span class="sxs-lookup"><span data-stu-id="f1879-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="f1879-143">資料來源活動會顯示在主控台視窗上。</span><span class="sxs-lookup"><span data-stu-id="f1879-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="f1879-144">一旦資料來源將資訊傳送至服務，服務就必須將它傳遞給每個用戶端。</span><span class="sxs-lookup"><span data-stu-id="f1879-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4.  <span data-ttu-id="f1879-145">如果用戶端、 資料來源和程式服務無法通訊，請參閱[疑難排解提示](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b)。</span><span class="sxs-lookup"><span data-stu-id="f1879-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="f1879-146">若要跨機器執行範例</span><span class="sxs-lookup"><span data-stu-id="f1879-146">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="f1879-147">設定服務機器：</span><span class="sxs-lookup"><span data-stu-id="f1879-147">Set up the service machine:</span></span>  
  
    1.  <span data-ttu-id="f1879-148">在服務機器上，建立一個名稱為 ServiceModelSamples 的虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="f1879-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="f1879-149">批次檔案從 Setupvroot.bat[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)可用來建立磁碟和虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="f1879-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="f1879-150">將服務程式檔案從 %SystemDrive%\Inetpub\wwwroot\servicemodelsamples 複製到服務機器上的 ServiceModelSamples 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="f1879-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="f1879-151">請務必將檔案放在 \bin 目錄中。</span><span class="sxs-lookup"><span data-stu-id="f1879-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="f1879-152">測試您是否能夠使用瀏覽器，從用戶端機器存取服務。</span><span class="sxs-lookup"><span data-stu-id="f1879-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2.  <span data-ttu-id="f1879-153">設定用戶端機器：</span><span class="sxs-lookup"><span data-stu-id="f1879-153">Set up the client machines:</span></span>  
  
    1.  <span data-ttu-id="f1879-154">將語言特定資料夾下 \client\bin\ 資料夾中的用戶端程式檔案複製到用戶端機器。</span><span class="sxs-lookup"><span data-stu-id="f1879-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2.  <span data-ttu-id="f1879-155">在每個用戶端組態檔中，將端點定義的位址值變更成符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="f1879-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="f1879-156">以位址中的完整網域名稱取代 "localhost" 的任何參考。</span><span class="sxs-lookup"><span data-stu-id="f1879-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3.  <span data-ttu-id="f1879-157">設定資料來源機器：</span><span class="sxs-lookup"><span data-stu-id="f1879-157">Set up the data source machine:</span></span>  
  
    1.  <span data-ttu-id="f1879-158">將語言特定資料夾下 \datasource\bin\ 資料夾中的資料來源程式檔複製到資料來源機器中。</span><span class="sxs-lookup"><span data-stu-id="f1879-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2.  <span data-ttu-id="f1879-159">在資料來源組態檔中，將端點定義的位址值變更成符合服務的新位址。</span><span class="sxs-lookup"><span data-stu-id="f1879-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="f1879-160">以位址中的完整網域名稱取代 "localhost" 的任何參考。</span><span class="sxs-lookup"><span data-stu-id="f1879-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4.  <span data-ttu-id="f1879-161">在用戶端機器上，從命令提示字元啟動 Client.exe。</span><span class="sxs-lookup"><span data-stu-id="f1879-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="f1879-162">在資料來源機器上，從命令提示字元啟動 Datasource.exe。</span><span class="sxs-lookup"><span data-stu-id="f1879-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1879-163">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f1879-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1879-164">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f1879-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f1879-165">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="f1879-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1879-166">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="f1879-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a><span data-ttu-id="f1879-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1879-167">See Also</span></span>
