---
title: 通道處理站
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 6479c4bb057ad73b0aeb84c882cbed8dec306ce6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911692"
---
# <a name="channel-factory"></a>通道處理站
本範例示範用戶端應用程式如何使用 <xref:System.ServiceModel.ChannelFactory> 類別而非使用產生的用戶端來建立通道。 這個範例是以執行計算機服務的[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此範例使用 <xref:System.ServiceModel.ChannelFactory%601> 類別來建立服務端點的通道。 一般而言, 若要建立服務端點的通道, 您可以使用[System.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端類型, 並建立所產生類型的實例。 您也可以使用 <xref:System.ServiceModel.ChannelFactory%601> 類別來建立通道，如此範例所示。 下列範例程式碼所建立的服務, 與[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)中的服務相同。  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  如果您是在跨電腦的情況中執行此範例，必須使用正在執行服務的電腦完整名稱來取代先前程式碼中的 "localhost"。 此範例不會使用組態來設定端點位址，因此必須透過程式碼來完成。  
  
 一旦建立了通道，即可透過叫用已產生用戶端的相同方式來叫用服務作業。  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 若要關閉通道，必須先將通道轉換為 <xref:System.ServiceModel.IClientChannel> 介面。 這是因為產生的通道會使用 `ICalculator` 介面在用戶端應用程式中宣告，且使用的方法與 `Add` 和 `Subtract` 類似，但和 `Close` 不同。 `Close` 方法源自 <xref:System.ServiceModel.ICommunicationObject> 介面。  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按 ENTER 鍵，關閉用戶端應用程式。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。 請注意，此範例不會啟用中繼資料發行。 您必須先為此範例啟用中繼資料發行，以重新產生用戶端類型。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
### <a name="to-run-the-sample-cross-machine"></a>若要執行跨電腦範例  
  
1. 請使用正在執行服務的電腦完整名稱來取代下列程式碼中的 "localhost"。  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
