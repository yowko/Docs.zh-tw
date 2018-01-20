---
title: "HOW TO：使用 WCF 用戶端來存取 WSE 3.0 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49ff6378bcd35ab2d4e2adf3783a1c4e73025d3a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>HOW TO：使用 WCF 用戶端來存取 WSE 3.0 服務
當 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端設定為使用 WS-Addressing August 2004 版本規格時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的連線層級與 Microsoft .NET 服務的 Web Services Enhancements (WSE) 3.0 相容。 不過，WSE 3.0 服務不支援中繼資料交換 (MEX) 通訊協定，因此當您使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端類別的安全性設定不會套用至產生[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端。 因此，在產生 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端之後，您必須指定 WSE 3.0 服務所需的安全性設定。  
  
 您可以使用自訂繫結來套用這些安全性設定，將 WSE 3.0 服務的需求，以及 WSE 3.0 服務和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端之間的互通需求納入考量。 這些互通性需求包含上述的 WS-Addressing August 2004 規格使用和 WSE 3.0 預設訊息保護 <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的預設訊息保護為 <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>。 本主題詳細說明如何建立與 WSE 3.0 服務相互操作的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也會提供包含這個繫結的範例。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]此範例中，請參閱[與 ASMX Web 服務互通](../../../../docs/framework/wcf/samples/interoperating-with-asmx-web-services.md)。  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>若要使用 WCF 用戶端來存取 WSE 3.0 Web 服務  
  
1.  執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]WSE 3.0 Web 服務用戶端。  
  
     隨即建立 WSE 3.0 Web 服務的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。 因為 WSE 3.0 不支援 MEX 通訊協定，所以您無法使用此工具擷取 Web 服務的安全性需求。 應用程式開發人員必須為用戶端加入安全性設定。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端，請參閱[How to： 建立用戶端](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。  
  
2.  建立類別，表示可與 WSE 3.0 Web 服務通訊的繫結。  
  
     下列類別是一部分[與 WSE 互通](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)範例：  
  
    1.  建立從 <xref:System.ServiceModel.Channels.Binding> 類別衍生的類別。  
  
         下列程式碼範例會建立一個名為 `WseHttpBinding` 的類別，此類別衍生自 <xref:System.ServiceModel.Channels.Binding> 類別。  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2.  將屬性加入至類別，這些屬性會指定 WSE 服務所使用的 WSE 通行判斷提示 (Turnkey Assertion)、是否需要衍生金鑰、是否使用安全工作階段、是否需要簽章確認，以及訊息保護設定。 在 WSE 3.0 中，通行判斷提示會指定用戶端或 Web 服務的安全性需求，這與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的繫結驗證模式類似。  
  
         下列程式碼範例會定義 `SecurityAssertion`、`RequireDerivedKeys`、`EstablishSecurityContext` 和 `MessageProtectionOrder` 屬性，這些屬性會分別指定 WSE 通行判斷提示、是否需要衍生金鑰、是否使用安全工作階段、是否需要簽章確認，以及訊息保護設定。  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3.  覆寫 <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> 方法來設定繫結屬性。  
  
         下列程式碼範例會藉由取得 `SecurityAssertion` 和 `MessageProtectionOrder` 屬性的值，指定傳輸、訊息編碼和訊息保護設定。  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3.  在用戶端應用程式程式碼中，加入程式碼以設定繫結屬性。  
  
     下列程式碼範例會指定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端必須依照 WSE 3.0 `AnonymousForCertificate` 通行安全性判斷提示所定義，使用訊息保護和驗證。 此外，也需要安全工作階段和衍生金鑰。  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會定義自訂的繫結，此繫結會公開 WSE 3.0 通行安全性判斷提示屬性的對應屬性。 此自訂繫結 (名為 `WseHttpBinding`) 接著會用來指定可與 WSSecurityAnonymous WSE 3.0 快速入門範例通訊的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端的繫結屬性。  
  
  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Channels.Binding>  
 [與 WSE 互通](http://msdn.microsoft.com/library/f6816861-96a0-45f9-8736-8e4e82cd3a41)
