---
title: HOW TO：設定基本的 Windows Communication Foundation 用戶端
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 18acec48b2af78877f99335da38ccb0ae8942824
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332311"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>HOW TO：設定基本的 Windows Communication Foundation 用戶端

這是建立基本的 Windows Communication Foundation (WCF) 應用程式所需的六個工作的第五個。 如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。

本主題討論使用所產生用戶端組態檔**加入服務參考**Visual Studio 的功能或有[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 設定用戶端包含指定用戶端用來存取服務的端點。 端點位址、 繫結和合約，而且每一種必須設定用戶端的過程中指定。

## <a name="configure-a-windows-communication-foundation-client"></a>設定 Windows Communication Foundation 用戶端

從 GettingStartedClient 專案開啟產生的組態檔 (App.config)。 下列範例是產生之組態檔的外觀。 底下[ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)區段中，尋找[\<端點 >](../configure-apps/file-schema/wcf/endpoint-element.md)項目。

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
          <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

這個範例會設定用戶端用以存取位於下列位址的服務端點： `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`。

端點元素會指定將 `ServiceReference1.ICalculator` 服務合約用於 WCF 用戶端和服務之間的通訊。 WCF 通道是透過系統提供的 <xref:System.ServiceModel.WSHttpBinding> 進行設定。 此合約由使用產生**加入服務參考**Visual Studio 中。 它基本上是 GettingStartedLib 專案中所定義之合約的複本。 
  <xref:System.ServiceModel.WSHttpBinding> 繫結會指定 HTTP 為傳輸、互通安全性，與其他組態詳細資料。

如需如何使用產生的用戶端使用此設定的詳細資訊，請參閱[How to:使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [如何：使用 WCF 用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

## <a name="see-also"></a>另請參閱

- [使用繫結設定服務與用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [自我裝載](../../../docs/framework/wcf/samples/self-host.md)