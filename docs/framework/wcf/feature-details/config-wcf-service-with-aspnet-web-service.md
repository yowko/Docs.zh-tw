---
title: 作法：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 9c241c06f153e4f85c70459ff3c50889057103f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295037"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>作法：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作

若要設定 Windows Communication Foundation (WCF) 服務端點與 ASP.NET Web 服務用戶端互通，請使用 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 類型做為服務端點的系結類型。  
  
 您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。 ASP.NET Web 服務用戶端不支援 MTOM 訊息編碼，因此 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 屬性應該保留為其預設值，也就是 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> 。 ASP.NET Web 服務用戶端不支援 WS-Security，因此 <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 應該設定為 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 。  
  
 若要將 WCF 服務的中繼資料提供給 ASP.NET Web 服務 proxy 產生工具 (也就是 [Web 服務描述語言工具 ( # A0)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))、 [Web 服務探索工具 ( # A1)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))和 Visual Studio) 中的「 **加入 Web 參考** 」功能，您應該公開 HTTP/GET 中繼資料端點。  
  
## <a name="add-an-endpoint-in-code"></a>在程式碼中新增端點  
  
1. 建立新的 <xref:System.ServiceModel.BasicHttpBinding> 執行個體。  
  
2. 設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結的傳輸安全性。 如需詳細資訊，請參閱 [傳輸安全性](transport-security.md)。  
  
3. 使用您剛建立的繫結執行個體新增新的應用程式端點到您的服務主機中。 如需如何在程式碼中新增服務端點的詳細資訊，請參閱 [如何：在程式碼中建立服務端點](how-to-create-a-service-endpoint-in-code.md)。  
  
4. 啟用您的服務的 HTTP/GET 中繼資料端點。 如需詳細資訊，請參閱 [如何：使用程式碼發行服務的中繼資料](how-to-publish-metadata-for-a-service-using-code.md)。  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a>在設定檔中新增端點  
  
1. 建立新的 <xref:System.ServiceModel.BasicHttpBinding> 繫結組態。 如需詳細資訊，請參閱 [如何：在設定中指定服務](../how-to-specify-a-service-binding-in-configuration.md)系結。  
  
2. 設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結組態的傳輸安全性。 如需詳細資訊，請參閱 [傳輸安全性](transport-security.md)。  
  
3. 使用您剛建立的繫結組態設定您的服務的新應用程式端點。 如需如何在設定檔中新增服務端點的詳細資訊，請參閱 [如何：在設定中建立服務端點](how-to-create-a-service-endpoint-in-configuration.md)。  
  
4. 啟用您的服務的 HTTP/GET 中繼資料端點。 如需詳細資訊，請參閱 [如何：使用設定檔發行服務的中繼資料](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。  
  
## <a name="example"></a>範例  

 下列範例程式碼示範如何在程式碼中新增與 ASP.NET Web 服務用戶端相容的 WCF 端點，也可以在設定檔中新增。  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>另請參閱

- [作法：在程式碼中建立服務端點](how-to-create-a-service-endpoint-in-code.md)
- [作法：使用程式碼發行服務的中繼資料](how-to-publish-metadata-for-a-service-using-code.md)
- [作法：在組態中指定服務繫結](../how-to-specify-a-service-binding-in-configuration.md)
- [作法：在組態中建立服務端點](how-to-create-a-service-endpoint-in-configuration.md)
- [作法：使用組態檔發行服務的中繼資料](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [傳輸安全性](transport-security.md)
- [使用中繼資料](using-metadata.md)
