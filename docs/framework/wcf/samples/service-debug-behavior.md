---
title: "服務偵錯行為"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04520eda9fe7ce2cd461e094fe2cec76d52ccc7d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="service-debug-behavior"></a>服務偵錯行為
這個範例會示範如何設定服務偵錯行為設定。 範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，它會實作`ICalculator`服務合約。 這個範例會在組態檔中明確地定義服務偵錯行為。 這個行為也可以透過程式碼，以命令方式定義。  
  
 在這個範例中，用戶端是主控台應用程式 (.exe)，而服務則是由網際網路資訊服務 (IIS) 所裝載。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 伺服器的 Web.config 檔會定義服務偵錯行為，以啟用說明網頁與例外狀況處理，如下列範例所示。  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 [\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)是允許變更服務的偵錯行為屬性的組態項目。 使用者可以修改這項行為以達到下列目的：  
  
-   這可允許服務傳回應用程式碼擲回的任何例外狀況，即使例外狀況未使用 <xref:System.ServiceModel.FaultContractAttribute> 宣告。 將 `includeExceptionDetailInFaults` 設定為 `true`，便可達成這個目的。 當在伺服器擲回非預期例外狀況的案例中偵錯時，這個設定非常有用。  
  
    > [!IMPORTANT]
    >  在實際執行環境中開啟這項設定是不安全的。 未預期的伺服器例外狀況可能會包含某些不想要讓用戶端檢視的資訊，所以將 `includeExceptionDetailsInFaults` 設定為 `true` 可能會導致資訊洩漏。  
  
-   [ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)也允許使用者啟用或停用說明網頁。 每個服務都可以選擇公開一份說明網頁，其中包含的服務相關資訊可以包括取得服務之 WSDL 的端點。 將 `httpHelpPageEnabled` 設定為 `true`，便可啟用這項功能。 如此就可讓說明網頁傳回至要求服務基底位址的 GET 要求。 您可以藉由設定另一個 `httpHelpPageUrl` 屬性來變更這個位址。 如果改用 HTTPS 而非 HTTP，則可以保護其安全。 設定 `httpsHelpPageEnabled` 和 `httpsHelpPageUrl`，便可達成這個目的。  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 前三項作業 (加法、減法以及乘法) 一定會成功。 最後一個作業 (「除法」) 會因為除數為零例外狀況而失敗。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a>另請參閱
