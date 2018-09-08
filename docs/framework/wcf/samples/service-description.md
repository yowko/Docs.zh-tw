---
title: 服務描述
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: 1acd82fddd378a379023c7aa46ead2ce36c5b243
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178360"
---
# <a name="service-description"></a>服務描述
服務描述範例會示範服務如何在執行階段擷取其服務描述資訊。 此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)，與其他服務作業定義會傳回描述服務的相關資訊。 傳回的資訊會列出服務的基底位址與端點。 服務會使用 <xref:System.ServiceModel.OperationContext>、<xref:System.ServiceModel.ServiceHost> 和 <xref:System.ServiceModel.Description.ServiceDescription> 類別提供這項資訊。  
  
 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例有個修改版本的計算機合約，名稱為 `IServiceDescriptionCalculator`。 該合約會定義名為 `GetServiceDescriptionInfo` 的其他服務作業，此作業會將描述服務的基底位址或位址以及服務端點或端點的多行字串傳回至用戶端。  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 `GetServiceDescriptionInfo` 的實作程式碼會使用 <xref:System.ServiceModel.Description.ServiceDescription> 來列出服務端點。 因為服務端點可以有相對位址，所以它會先列出服務的基底位址。 為了取得完整的這份資訊，該程式碼會使用 <xref:System.ServiceModel.OperationContext.Current%2A> 取得作業內容。 <xref:System.ServiceModel.ServiceHost> 和其 <xref:System.ServiceModel.Description.ServiceDescription> 物件，都是擷取自此作業內容。 為了列出服務的基底端點，該程式碼會逐一查看服務主機的 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> 集合。 為了列出服務的服務端點，該程式碼會逐一查看服務描述的端點集合。  
  
```  
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 當執行範例時，您會看到計算機作業，然後服務資訊會由 `GetServiceDescriptionInfo` 作業傳回。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
  
## <a name="see-also"></a>另請參閱
