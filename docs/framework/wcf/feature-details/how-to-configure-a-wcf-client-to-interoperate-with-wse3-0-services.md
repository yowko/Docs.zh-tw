---
title: HOW TO：將 WCF 用戶端設為與 WSE3.0 服務交互操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 62642651516274a27c44abfc19e94dc529690ea9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304541"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a>HOW TO：將 WCF 用戶端設為與 WSE3.0 服務交互操作
當 WCF 用戶端會設定為使用 August 2004 版本的 Ws-addressing 規格，Windows Communication Foundation (WCF) 用戶端會將與 Web Services Enhancements 3.0 for Microsoft.NET (WSE) 服務的連線層級相容性。  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a>將 WCF 用戶端設定為與 WSE 3.0 Web 服務交互操作  
  
1. 執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立 WSE 3.0 Web 服務的 WCF 用戶端。  
  
     針對 WSE Web 服務，建立 WCF 用戶端類別。  
  
     如需建立 WCF 用戶端的詳細資訊，請參閱[How to:建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。  
  
2. 建立類別，表示可與 WSE 3.0 Web 服務通訊的繫結。  
  
     下列類別是屬於[與 WSE 交互操作](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)範例。  
  
    1.  建立從 <xref:System.ServiceModel.Channels.Binding> 類別衍生的類別。  
  
         下列程式碼範例會建立一個名為 `WseHttpBinding` 的類別，此類別衍生自 <xref:System.ServiceModel.Channels.Binding> 類別。  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  將屬性加入至類別，以指定 WSE 通行判斷提示 (Turnkey Assertion)、是否需要衍生金鑰、是否使用安全工作階段、是否需要簽章確認，以及訊息保護設定。  
  
         下列程式碼範例會定義`SecurityAssertion`， `RequireDerivedKeys`， `EstablishSecurityContext`，和`MessageProtectionOrder`屬性。 它們分別指定 WSE 通行判斷提示、 是否需要衍生的金鑰、 是否使用安全工作階段、 是否需要簽章確認和訊息保護設定。  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  覆寫 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法來設定繫結屬性。  
  
         下列程式碼範例會藉由取得 `SecurityAssertion` 和 `MessageProtectionOrder` 屬性的值，指定傳輸、訊息編碼和訊息保護設定。  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. 在用戶端應用程式程式碼中，加入程式碼以設定繫結屬性。  
  
     下列程式碼範例指定 WCF 用戶端必須使用訊息保護和驗證所定義的 WSE 3.0`AnonymousForCertificate`通行安全性判斷提示。 此外，也需要安全工作階段和衍生金鑰。  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義自訂的繫結，此繫結會公開 WSE 3.0 通行安全性判斷提示屬性的對應屬性。 自訂繫結，名為`WseHttpBinding`，然後用來指定 WCF 用戶端的繫結屬性。  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.Binding>
- [與 WSE 交互操作](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
