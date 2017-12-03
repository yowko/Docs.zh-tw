---
title: WSStreamedHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94df68732622c45605479cc62f600258b54a95c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="wsstreamedhttpbinding"></a>WSStreamedHttpBinding
本範例會示範如何建立可在使用 HTTP 傳輸時支援資料流案例的繫結。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 建立與設定新標準繫結的步驟如下所示。  
  
1.  建立新標準繫結  
  
     [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的標準繫結 (例如 basicHttpBinding 以及 netTcpBinding 等) 會設定特定需求的基礎傳輸與通道堆疊。 在這個範例中，`WSStreamedHttpBinding` 會將通道堆疊設定成支援資料流。 根據預設，WS-Security 和可信賴傳訊不會新增至通道堆疊中，因為資料流並不支援這兩項功能。 新繫結是透過衍生自 `WSStreamedHttpBinding` 的 <xref:System.ServiceModel.Channels.Binding> 類別所實作的。 `WSStreamedHttpBinding` 包含下列繫結項目：<xref:System.ServiceModel.Channels.HttpTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpsTransportBindingElement>、<xref:System.ServiceModel.Channels.TransactionFlowBindingElement> 和 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>。 類別會提供 `CreateBindingElements()` 方法以設定結果繫結堆疊，如下列範例程式碼所示。  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2.  新增組態支援  
  
     為了透過組態公開傳輸，此範例會實作兩個額外的類別：`WSStreamedHttpBindingConfigurationElement` 和 `WSStreamedHttpBindingSection`。 類別 `WSStreamedHttpBindingSection` 是 <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602>`WSStreamedHttpBinding`，它會將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 公開至組態系統。 大量實作會委派至衍生自 `WSStreamedHttpBindingConfigurationElement` 的 <xref:System.ServiceModel.Configuration.StandardBindingElement>。 類別 `WSStreamedHttpBindingConfigurationElement` 有對應至 `WSStreamedHttpBinding` 之屬性的屬性，以及將每個組態項目對應至繫結的功能。  
  
     向組態系統註冊此處理常式的方式是，將下列區段新增至服務的組態檔中。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     這樣就能夠從 serviceModel 組態區段參考該處理常式。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  確認您有執行中所列的步驟[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3.  請確定您已執行[網際網路資訊服務 (IIS) 伺服器憑證安裝指示](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。  
  
4.  若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
5.  若要跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
6.  當用戶端視窗顯示時，請輸入 "Sample.txt"。 您應該會在目錄中找到「複製 - Sample.txt」。  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a>WSStreamedHttpBinding 範例服務  
 使用 `WSStreamedHttpBinding` 的範例服務位於服務子目錄中。 `OperationContract` 的實作會先使用 `MemoryStream` 從傳入資料流擷取所有資料，接著再傳回 `MemoryStream`。 此範例服務是由網際網路資訊服務 (IIS) 裝載。  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a>WSStreamedHttpBinding 範例用戶端  
 透過 `WSStreamedHttpBinding` 與服務互動時所使用的用戶端位於用戶端子目錄中。 因為本範例中所使用的憑證是使用 Makecert.exe 所建立的測試憑證，所以當您嘗試從瀏覽器存取 HTTPS 位址時 (例如 https://localhost/servicemodelsamples/service.svc)，會顯示安全性警示。 若要允許 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端適當地使用測試憑證，就必須在用戶端新增某些其他程式碼以便隱藏安全性警示。 使用實際執行憑證時，不需要這個程式碼及伴隨的類別。  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a>另請參閱
