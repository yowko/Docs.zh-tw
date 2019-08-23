---
title: HOW TO：設定 COM+ 服務設定
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 58845ab7b9da7377f4fdaa7da13e7c407226d63c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912198"
---
# <a name="how-to-configure-com-service-settings"></a>作法：設定 COM+ 服務設定
使用 COM+ 服務組態工具加入或移除應用程式介面時，Web 服務組態會在應用程式的組態檔中更新。 在 com + 裝載模式中, app.config 檔案會放在應用程式根目錄中 (%programfiles%\complus applications\ 應用程式\\{appid} 是預設值)。 在兩個 Web 裝載模式中，Web.config 檔案都會放在指定的 vroot 目錄中。  
  
> [!NOTE]
> 訊息簽章應用來保護用戶端和伺服器之間的訊息不受竄改。 此外，訊息或傳輸層加密也應該用來保護用戶端和伺服器之間的訊息，以免資訊洩漏。 如同 Windows Communication Foundation (WCF) 服務, 您應該使用節流來限制同時呼叫、連接、實例和暫止作業的數目。 這有助防止資源過度消耗。 節流行為是透過服務組態檔設定所指定的。  
  
## <a name="example"></a>範例  
 試想實作下列介面的元件：  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 如果元件公開為 Web 服務，則公開 (且用戶端必須符合) 的對應服務合約如下：  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
> IID 是做為合約的初始命名空間一部分。  
  
 使用這個服務的用戶端應用程式必須符合這個合約，並且使用與應用程式組態中所指定的繫結相容的繫結。  
  
 下列程式碼範例中會示範預設組態檔。 做為 Windows Communication Foundation (WCF) Web 服務, 這符合標準的服務模型設定架構, 而且可以使用與其他 WCF 服務設定檔相同的方式進行編輯。  
  
 一般修改包含：  
  
- 將端點位址從預設形式 ApplicationName/ComponentName/InterfaceName 變更為更容易使用的形式。  
  
- 將服務的命名空間從預設`http://tempuri.org/InterfaceID`表單修改為更相關的表單。  
  
- 變更端點以使用不同的傳輸繫結。  
  
     在 COM+ 裝載案例中，預設會使用具名管道，但也可以使用像 TCP 的電腦外傳輸。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [整合 COM 應用程式](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
