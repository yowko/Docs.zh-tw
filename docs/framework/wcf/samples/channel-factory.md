---
title: 通道處理站
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: a528cc759ad550b21845dfd351d4e7808cfb6b56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="channel-factory"></a>通道處理站
本範例示範用戶端應用程式如何使用 <xref:System.ServiceModel.ChannelFactory> 類別而非使用產生的用戶端來建立通道。 這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，用來實作計算機服務。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此範例使用 <xref:System.ServiceModel.ChannelFactory%601> 類別來建立服務端點的通道。 一般而言，若要建立服務端點的通道您要產生的用戶端類型[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)並建立產生之型別的執行個體。 您也可以使用 <xref:System.ServiceModel.ChannelFactory%601> 類別來建立通道，如此範例所示。 下列範例程式碼所建立的服務中的服務等同[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。  
  
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
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。 請注意，此範例不會啟用中繼資料發行。 您必須先為此範例啟用中繼資料發行，以重新產生用戶端類型。  
  
3.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
### <a name="to-run-the-sample-cross-machine"></a>若要執行跨電腦範例  
  
1.  請使用正在執行服務的電腦完整名稱來取代下列程式碼中的 "localhost"。  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a>另請參閱
