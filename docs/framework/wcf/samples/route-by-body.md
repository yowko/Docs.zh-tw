---
title: 依本文路由
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 4266068bb53e5ae90a05cc6537df2ab9b65b6b07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965505"
---
# <a name="route-by-body"></a>依本文路由
這個範例會示範如何實作使用任何 SOAP 動作接受訊息物件的服務。 這個範例是以執行計算機服務的[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。 此服務會實作接受 `Calculate` 要求參數並傳回 <xref:System.ServiceModel.Channels.Message> 回應的單一 <xref:System.ServiceModel.Channels.Message> 作業。  
  
 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務是裝載在 IIS 中。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 下列範例會示範根據本文內容的訊息分派。 內建的 Windows Communication Foundation (WCF) 服務模型訊息分派機制是以訊息動作為基礎。 然而，有很多現有的 Web 服務以 Action="" 定義其所有作業。 根據以 Action 資訊為基礎保留分派要求訊息的 WSDL 來建置服務，是不可能的。 這個範例會示範根據 WSDL 的服務合約 (WSDL 包含在範例隨附的 Service.wsdl 中)。 服務合約是計算機, 與[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)中使用的不同。 不過，`[OperationContract]` 會指定所有作業的 `Action=""`。  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 如果是合約，服務需要自訂分派行為 `DispatchByBodyBehavior`，以允許在作業之間分派訊息。 這個分派行為會以`DispatchByBodyElementOperationSelector`個別包裝函式專案的 QName 所索引之作業名稱的資料表, 初始化自訂作業選取器。 `DispatchByBodyElementOperationSelector` 會查看本文之第一個子系的開始標記，並使用先前提到的資料表來選取作業。  
  
 用戶端會使用使用[System.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從服務所匯出的 WSDL 自動產生的 proxy。  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 除了自動產生之 Proxy 中的 Action 參數以外，所有作業的動作都是空的，這事實對用戶端程式碼沒有影響。  
  
 用戶端程式碼會執行數次計算。 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建立方案, 請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。  
  
3. 若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
