---
title: HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: 26466a97ae44e6852c189d0b72bdba1b93d86141
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141730"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結

本主題示範使用 Secure Sockets Layer (SSL) 傳輸安全性來搭配可靠工作階段。 若要透過 HTTPS 使用可靠工作階段，您必須建立使用可靠工作階段與 HTTPS 傳輸的自訂繫結。 您可以使用程式碼或以宣告方式在設定檔中啟用可靠會話。 此程式會使用用戶端和服務設定檔來啟用可靠會話和[ **\<HTTPsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)元素。

此程式的重要部分是 **\<端點 >** configuration 元素包含一個 `bindingConfiguration` 屬性，其參考名為 `reliableSessionOverHttps`的自訂系結設定。 \<系結[ **>** ](../../configure-apps/file-schema/wcf/bindings.md) configuration 專案會參考此名稱，藉由包含 **\<reliableSession >** 和 **\<HTTPsTransport >** 元素，來指定要使用可靠會話和 HTTPS 傳輸。

如需此範例的來源複本，請參閱透過[HTTPS 自訂系結可靠會話](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md)。

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>以 CustomBinding 設定服務，以搭配使用可靠會話與 HTTPS

1. 定義服務類型的服務合約。

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. 在服務類別中實作服務合約。 請注意，不會在服務的執行中指定位址或系結資訊。 您不需要撰寫程式碼，就能從設定檔抓取位址或系結資訊。

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. 建立*web.config*檔案，使用名為 `reliableSessionOverHttps` 的自訂系結來設定 `CalculatorService` 的端點，該系結會使用可靠會話和 HTTPS 傳輸。

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. 建立包含這一行的*服務 .svc*檔案：

   `<%@ServiceHost language=c# Service="CalculatorService" %>`

1. 將*服務 .svc*檔案放在您的 INTERNET INFORMATION SERVICES （IIS）虛擬目錄中。

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>設定具有 CustomBinding 的用戶端，以搭配使用可靠會話與 HTTPS

1. 從命令列使用[System.servicemodel 中繼資料公用程式工具（*Svcutil*）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ，以從服務中繼資料產生程式碼。

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. 產生的用戶端會包含 `ICalculator` 介面，以定義用戶端執行必須滿足的服務合約。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. 產生的用戶端應用程式也包含 `ClientCalculator` 的實作。 請注意，不會在服務的執行中指定位址和系結資訊。 您不需要撰寫程式碼，就能從設定檔抓取位址和系結資訊。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. 設定名為 `reliableSessionOverHttps` 的自訂系結，以使用 HTTPS 傳輸和可靠會話。

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. 在應用程式中建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. 請編譯並執行用戶端。  

## <a name="net-framework-security"></a>.NET Framework 安全性

因為此範例中使用的憑證是使用*Makecert*建立的測試憑證，所以當您嘗試從瀏覽器存取 HTTPS 位址（例如 `https://localhost/servicemodelsamples/service.svc`）時，就會出現安全性警示。

## <a name="see-also"></a>請參閱

- [可靠工作階段](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
