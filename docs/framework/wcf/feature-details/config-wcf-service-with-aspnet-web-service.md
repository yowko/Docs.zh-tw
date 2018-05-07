---
title: HOW TO：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 12c5645b53e8e931edabc1a13fc1749e40538044
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>HOW TO：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作
若要設定 Windows Communication Foundation (WCF) 服務端點加入具有互通[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 服務用戶端，請使用<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>型別作為服務端點的繫結型別。  
  
 您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 服務用戶端不支援 MTOM 訊息編碼，因此應將 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 屬性保留為預設值，也就是 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>。 ASP.Net Web 服務用戶端不支援 Web 服務安全性，因此應該將 <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 設定為 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>。  
  
 若要將 WCF 服務的中繼資料提供給[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 服務 proxy 產生工具 (也就是[Web 服務描述語言工具 (Wsdl.exe)](http://go.microsoft.com/fwlink/?LinkId=73833)， [Web 服務探索工具 (Disco.exe)](http://go.microsoft.com/fwlink/?LinkId=73834)，和 Visual Studio 中的加入 Web 參考功能)，您應該公開 （expose) 的 HTTP/GET 中繼資料端點。  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>若要在程式碼中新增與 ASP.NET Web 服務用戶端相容的 WCF 端點  
  
1.  建立新的 <xref:System.ServiceModel.BasicHttpBinding> 執行個體。  
  
2.  設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結的傳輸安全性。 如需詳細資訊，請參閱[傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security.md)。  
  
3.  使用您剛建立的繫結執行個體新增新的應用程式端點到您的服務主機中。 如需有關如何在程式碼中加入服務端點的詳細資訊，請參閱[How to： 在程式碼中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)。  
  
4.  啟用您的服務的 HTTP/GET 中繼資料端點。 如需詳細資訊，請參閱[How to： 服務使用程式碼發行中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)。  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>若要在組態檔中新增與 ASP.NET Web 服務用戶端相容的 WCF 端點  
  
1.  建立新的 <xref:System.ServiceModel.BasicHttpBinding> 繫結組態。 如需詳細資訊，請參閱[How to： 在組態中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。  
  
2.  設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結組態的傳輸安全性。 如需詳細資訊，請參閱[傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security.md)。  
  
3.  使用您剛建立的繫結組態設定您的服務的新應用程式端點。 如需有關如何在組態檔中加入服務端點的詳細資訊，請參閱[How to： 在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)。  
  
4.  啟用您的服務的 HTTP/GET 中繼資料端點。 如需詳細資訊，請參閱[How to： 使用組態檔的服務發行中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何新增與相容的 WCF 端點[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 服務用戶端程式碼中的，或是在組態檔中。  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>另請參閱  
 [如何：在程式碼中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 [如何：使用程式碼發行服務的中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 [如何：在設定中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [如何：在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [如何：使用組態檔發行服務的中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [傳輸安全性](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [使用中繼資料](../../../../docs/framework/wcf/feature-details/using-metadata.md)
