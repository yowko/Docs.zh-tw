---
title: 多個合約
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: 040ab9b80e9567139ca4588e3ddf83b8f43f2d76
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864809"
---
# <a name="multiple-contracts"></a>多個合約
多個合約範例會示範如何在服務上實作一個以上的合約，以及如何設定要與每個已實作合約進行通訊的端點。 此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。 此服務已修改成要定義兩個合約：`ICalculator` 以及 `ICalculatorSession` 合約。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此服務類別會同時實作 `ICalculator` 和 `ICalculatorSession` 合約。 因為其中一個合約需要工作階段，所以服務會使用 <xref:System.ServiceModel.InstanceContextMode.PerSession> 執行個體模式來維護整個工作階段存留期間的狀態。  
  
 此服務組態已修改成定義兩個要公開各個合約的端點。 `ICalculator` 端點會以 `basicHttpBinding` 公開於基底位址。 `ICalculatorSession` 端點會以 `wsHttpBinding` 屬性設定為 `bindingConfiguration` 的 `BindingWithSession` 公開於基底位址/工作階段，如下列範例組態所示。  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"   
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 產生的用戶端程式碼現在同時包含原始 `ICalculator` 合約與新 `ICalculatorSession` 合約的用戶端類別。 用戶端組態與程式碼已修改成可在適當的服務端點上與每個合約進行通訊。  
  
 用戶端為主控台視窗應用程式 (.exe)。 而服務是由網際網路資訊服務 (IIS) 裝載。  
  
 用戶端主控台視窗會顯示傳送至每個端點的作業，首先顯示基本端點，之後顯示安全端點。  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
  
## <a name="see-also"></a>另請參閱
