---
title: HOW TO：在可靠的工作階段內交換訊息
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 39dd6636f80b107ced1caac29869c6c66e67e21e
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052035"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>HOW TO：在可靠的工作階段內交換訊息

本主題概要說明透過其中一個系統提供的繫結啟用可靠工作階段 (此繫結支援此類工作階段，但非預設) 所需的步驟。 您可以使用程式碼或以宣告方式在您的設定檔中啟用可靠會話。 此程式會使用用戶端和服務設定檔來啟用可靠會話，並規定訊息送達的順序與傳送的相同。

此程式的主要部分是端點設定元素包含參考名為之系結設定的 `bindingConfiguration` 屬性 `Binding1` 。 [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Configuration 元素會參考此名稱，藉由將專案的屬性設定為來啟用可靠會話 `enabled` [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) `true` 。 您可以將 `ordered` 屬性設為 `true`，為可靠工作階段指定依序傳遞保證。

如需此範例的來源複本，請參閱[WS 可靠會話](../samples/ws-reliable-session.md)。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>以 WSHttpBinding 設定服務以使用可靠會話

1. 定義服務類型的服務合約。

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. 在服務類別中實作服務合約。 請注意，不會在服務的執行中指定位址或系結資訊。 您不需要撰寫程式碼，就能從設定檔抓取位址或系結資訊。

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. 建立*Web.config*檔案來設定的端點 `CalculatorService` ，其會使用 <xref:System.ServiceModel.WSHttpBinding> 已啟用可靠會話和所需訊息的排序傳遞。

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. 建立包含這一行的*服務 .svc*檔案：

   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. 將*服務 .svc*檔案放在您的 INTERNET INFORMATION SERVICES （IIS）虛擬目錄中。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>以 WSHttpBinding 設定用戶端以使用可靠會話

1. 從命令列使用[System.servicemodel 中繼資料公用程式工具（*Svcutil.exe*）](../servicemodel-metadata-utility-tool-svcutil-exe.md) ，以從服務中繼資料產生程式碼：

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. 產生的用戶端包含 `ICalculator` 定義用戶端執行必須滿足之服務合約的介面。

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. 產生的用戶端應用程式也包含 `ClientCalculator` 的實作。 請注意，在服務的執行內的任何位置都不會指定位址和系結資訊。 您不需要撰寫程式碼，就能從設定檔抓取位址或系結資訊。

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe*也會為使用類別的用戶端產生設定 <xref:System.ServiceModel.WSHttpBinding> 。 使用 Visual Studio 時，將設定檔命名為*App.config* 。

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. `ClientCalculator`在應用程式中建立的實例，並呼叫服務作業。

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. 請編譯並執行用戶端。

## <a name="example"></a>範例

好幾個系統提供的繫結預設都支援可靠工作階段。 這些包括：

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

如需如何建立支援可靠會話之自訂系結的範例，請參閱[如何：使用 HTTPS 建立自訂可靠會話](how-to-create-a-custom-reliable-session-binding-with-https.md)系結。

## <a name="see-also"></a>另請參閱

- [可靠工作階段](reliable-sessions.md)
