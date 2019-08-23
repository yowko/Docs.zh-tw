---
title: 單一 ListenUri 的多個端點
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: ea0cd0d8636f5301dab3fe60b181dfd36fc30d54
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930327"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a>單一 ListenUri 的多個端點
這個範例會示範在單一 `ListenUri` 裝載多個端點的服務。 這個範例是以執行計算機服務的[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 如[多個端點](../../../../docs/framework/wcf/samples/multiple-endpoints.md)範例中所示, 服務可以裝載多個端點, 每個端點都有不同的位址, 而且可能也會有不同的系結。 這個範例會示範如何在相同位址裝載多個端點。 此外，這個範例還會示範服務端點所具有兩種位址的差異：`EndpointAddress` 和 `ListenUri`。  
  
 `EndpointAddress` 是服務的邏輯位址。 這是 SOAP 訊息傳送至的目標位址。 `ListenUri` 是服務的實際位址， 含有連接埠和位址資訊，而服務端點實際上會接聽目前電腦上的訊息。 在大多數情況下，這些位址不需要有所不同，因為未明確指定 `ListenUri` 時，預設會是端點之 `EndpointAddress` 的 URI。 在少數情況下，例如設定路由器時區分這些位址就很有用，該路由器可能會接受傳送至一些不同服務的訊息。  
  
## <a name="service"></a>服務  
 這個範例中的服務有兩個合約，`ICalculator` 和 `IEcho`。 除了可自訂的 `IMetadataExchange` 端點外，還有三個應用程式端點，如下列程式碼所示。  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 這三個端點都會裝載在相同的 `ListenUri`，並使用相同的 `binding`。相同 `ListenUri` 上的端點必須具有相同的繫結，這樣才可以共用接聽電腦上該實際位址之訊息的單一通道堆疊。 每個端點的 `address` 為 URN。雖然一般來說，位址表示實際位置，事實上位址可以是任何種類的 URI，因為位址的用途就是比對和篩選，如本範例所示。  
  
 由於這三個端點都共用`ListenUri`相同的, 因此當訊息抵達該處時, Windows Communication Foundation (WCF) 必須決定訊息的目的地端點。 每個端點都具有由兩個部分組成的訊息篩選條件：位址篩選條件和合約篩選條件。 位址篩選條件會比對 SOAP 訊息的 `To` 和服務端點的位址。 例如，只有指定 `To "Urn:OtherEcho"` 的訊息是這個服務第三個端點的候選。 合約篩選條件會比對與特定合約作業相關聯的動作。 例如，具有 `IEcho` 動作的訊息。 `Echo` 會比對這個服務第二和第三個端點的合約篩選條件，因為這兩個端點都會裝載 `IEcho` 合約。  
  
 因此，結合位址篩選條件和合約篩選條件之後，就可以將抵達這個服務之 `ListenUri` 的每個訊息路由至正確的端點。 第三個端點與其他兩個端點不同，它會接受從其他端點傳送至不同位址的訊息。 第一個和第二個端點可以依合約 (傳入訊息的動作) 區分。  
  
## <a name="client"></a>用戶端  
 由於伺服器上的端點有兩個不同的位址，用戶端端點也會有兩個位址。 在伺服器和用戶端上，邏輯位址稱為 `EndpointAddress`。 不過，在伺服器上，實際位址稱為 `ListenUri`，在用戶端上，實際位址則稱為 `Via`。  
  
 根據預設，伺服器上的這兩個位址是相同的。 若要在用戶端上指定與端點位址不同的 `Via`，請使用 `ClientViaBehavior`：  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 位址照例是來自 Svcutil.exe 所產生的用戶端組態檔。 `Via` (對應至服務的 `ListenUri`) 不會顯示在服務的中繼資料中，因此這個資訊必須傳送到超出範圍的用戶端 (就和服務的中繼資料位址一樣)。  
  
 這個範例中的用戶端會將訊息傳送至伺服器的三個應用程式端點，示範它可以與這三個端點通訊 (也可以區別這三個端點)，即使這三個端點具有相同的 `Via` 也是一樣。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
    > [!NOTE]
    >  如果是跨電腦，您必須以服務電腦的名稱取代 Client.cs 檔案中的 localhost。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
