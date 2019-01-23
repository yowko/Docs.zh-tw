---
title: HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結
ms.date: 03/30/2017
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
ms.openlocfilehash: f39325829cf4b548482a6a570a5aa1fd65e61a1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516677"
---
# <a name="how-to-create-a-custom-reliable-session-binding-with-https"></a>HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結

本主題示範使用 Secure Sockets Layer (SSL) 傳輸安全性來搭配可靠工作階段。 若要透過 HTTPS 使用可靠工作階段，您必須建立使用可靠工作階段與 HTTPS 傳輸的自訂繫結。 透過命令式程式碼或是宣告式組態檔中，您就會啟用可靠工作階段。 此程序會使用用戶端和服務組態檔來啟用可靠工作階段並[  **\<httpsTransport >** ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md)項目。

此程序的重要部分在於**\<端點 >** 組態項目包含`bindingConfiguration`參考名為自訂繫結組態的屬性`reliableSessionOverHttps`。 [ **\<繫結 >** ](../../../../docs/framework/misc/binding.md)組態項目會參考此名稱來指定包含要使用可靠工作階段和 HTTPS 傳輸 **\<reliableSession >** 並 **\<httpsTransport >** 項目。

如需此範例中的來源複本，請參閱[自訂繫結可靠工作階段透過 HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md)。

### <a name="configure-the-service-with-a-custombinding-to-use-a-reliable-session-with-https"></a>設定包含 CustomBinding 來使用搭配 HTTPS 的可靠工作階段的服務

1. 定義服務類型的服務合約。

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]

1. 在服務類別中實作服務合約。 請注意，位址或繫結資訊不指定的服務實作內。 您不需要撰寫程式碼來擷取組態檔中的位址或繫結資訊。

   [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]

1. 建立*Web.config*檔案來設定的端點`CalculatorService`名為的自訂繫結`reliableSessionOverHttps`使用可靠工作階段和 HTTPS 傳輸。

   [!code-xml[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]

1. 建立*Service.svc*檔案，其中包含的列：

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. 地方*Service.svc* Internet Information Services (IIS) 虛擬目錄中的檔案。

### <a name="configure-the-client-with-a-custombinding-to-use-a-reliable-session-with-https"></a>設定包含 CustomBinding 來使用搭配 HTTPS 的可靠工作階段的用戶端

1. 使用[ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從命令列，從服務中繼資料產生程式碼。

   ```console
   Svcutil.exe <Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. 產生的用戶端包含`ICalculator`定義必須滿足的用戶端實作的服務合約的介面。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]

1. 產生的用戶端應用程式也包含 `ClientCalculator` 的實作。 請注意，位址和繫結資訊不指定的服務實作內。 您不需要撰寫程式碼來擷取組態檔中的位址和繫結資訊。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]

1. 設定自訂繫結，名為`reliableSessionOverHttps`使用 HTTPS 傳輸和可靠工作階段。

   [!code-xml[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]

1. 在應用程式中建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。

   [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]

1. 請編譯並執行用戶端。  

## <a name="net-framework-security"></a>.NET Framework 安全性

因為此範例中使用的憑證是使用建立的測試憑證*Makecert.exe*，當您嘗試存取 HTTPS 位址，例如時，會顯示安全性警示`https://localhost/servicemodelsamples/service.svc`，從您的瀏覽器。

## <a name="see-also"></a>另請參閱

- [可靠工作階段](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
