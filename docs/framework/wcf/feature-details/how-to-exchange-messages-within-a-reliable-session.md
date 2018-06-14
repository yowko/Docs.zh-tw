---
title: HOW TO：在可靠的工作階段內交換訊息
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 80dea8545e9d813e68e67414151e2c96537db2e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491822"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>HOW TO：在可靠的工作階段內交換訊息

本主題概要說明透過其中一個系統提供的繫結啟用可靠工作階段 (此繫結支援此類工作階段，但非預設) 所需的步驟。 啟用可靠工作階段命令式程式碼或是宣告式組態檔。 若要啟用可靠工作階段，並規定訊息到達其傳送的順序相同，此程序會使用用戶端和服務組態檔。

此程序的重要部分為端點組態項目包含`bindingConfiguration`屬性必須參考名為繫結組態`Binding1`。 [ **\<繫結 >** ](../../../../docs/framework/misc/binding.md)組態項目會參考此名稱，藉此啟用可靠工作階段`enabled`屬性[ **\<reliableSession >** ](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)元素`true`。 您可以將 `ordered` 屬性設為 `true`，為可靠工作階段指定依序傳遞保證。

此範例的來源副本，請參閱[WS 可靠工作階段](../../../../docs/framework/wcf/samples/ws-reliable-session.md)。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>透過 WSHttpBinding 使用可靠工作階段設定服務

1. 定義服務類型的服務合約。

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. 在服務類別中實作服務合約。 請注意，位址或繫結資訊不指定服務的實作內部。 您不需要撰寫程式碼以擷取組態檔中的位址或繫結資訊的資訊。

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. 建立*Web.config*檔案來設定的端點`CalculatorService`使用<xref:System.ServiceModel.WSHttpBinding>與可靠工作階段啟用和排序的傳遞所需的訊息。

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. 建立*Service.svc*檔案包含行：

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  位置*Service.svc*網際網路資訊服務 (IIS) 虛擬目錄中的檔案。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>設定用戶端透過 WSHttpBinding 使用可靠工作階段

1. 使用[ServiceModel Metadata Utility Tool (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從命令列從服務中繼資料產生程式碼：

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. 產生的用戶端包含`ICalculator`定義用戶端實作所必須滿足的服務合約的介面。

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. 產生的用戶端應用程式也包含 `ClientCalculator` 的實作。 請注意，位址和繫結資訊不內部指定服務的實作。 您不需要撰寫程式碼以擷取組態檔中的位址或繫結資訊的資訊。

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe*也會產生的組態會使用用戶端<xref:System.ServiceModel.WSHttpBinding>類別。 組態檔命名*App.config*使用 Visual Studio 時。

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. 建立的執行個體`ClientCalculator`應用程式中呼叫服務作業。

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. 請編譯並執行用戶端。

## <a name="example"></a>範例

好幾個系統提供的繫結預設都支援可靠工作階段。 它們包括：

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

如需如何建立支援可靠工作階段的自訂繫結的範例，請參閱[How to： 使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)。

## <a name="see-also"></a>另請參閱

[可靠工作階段](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
