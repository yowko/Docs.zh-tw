---
title: HOW TO：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: ddd7e8c95701532010b54e5136a33d37d139f6a4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739235"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>HOW TO：將 WCF 服務設為與 ASP.NET Web 服務用戶端交互操作

要將 Windows 通訊基礎 (WCF) 服務終結點配置為與<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>ASP.NET Web 服務用戶端進行互通,請使用 該類型作為服務終結點的綁定類型。  
  
 您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。 ASP.NET Web 服務客戶端不支援 MTOM<xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType>訊息編碼, 因此該屬性應保留<xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>為其預設值,即 。 ASP.NET Web 服務客戶端不支援<xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType>WS-Security,<xref:System.ServiceModel.BasicHttpSecurityMode.Transport>因此 應設定為 。  
  
 要使 WCF 服務的中繼資料可用於 ASP.NET Web 服務代理生成工具(即 Web[服務描述語言工具 (Wsdl.exe)、Web](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v%3dvs.100))[服務發現工具 (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))和 Visual Studio 中的**新增 Web 引用**功能),應公開 HTTP/GET 元資料終結點。  
  
## <a name="add-an-endpoint-in-code"></a>在代碼中加入終結點  
  
1. 建立新的 <xref:System.ServiceModel.BasicHttpBinding> 執行個體。  
  
2. 設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結的傳輸安全性。 有關詳細資訊,請參閱[運輸安全](../../../../docs/framework/wcf/feature-details/transport-security.md)。  
  
3. 使用您剛建立的繫結執行個體新增新的應用程式端點到您的服務主機中。 有關如何在代碼中添加服務終結點的詳細資訊,請參閱[如何:在代碼中建立服務終結點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)。  
  
4. 啟用您的服務的 HTTP/GET 中繼資料端點。 有關詳細資訊,請參閱[:使用代碼發佈服務的中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)。  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a>在設定檔中加入終結點  
  
1. 建立新的 <xref:System.ServiceModel.BasicHttpBinding> 繫結組態。 有關詳細資訊,請參閱[如何:在設定中指定服務綁定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。  
  
2. 設定繫結至 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> 的安全性模式，以選擇性啟用此服務端點繫結組態的傳輸安全性。 有關詳細資訊,請參閱[運輸安全](../../../../docs/framework/wcf/feature-details/transport-security.md)。  
  
3. 使用您剛建立的繫結組態設定您的服務的新應用程式端點。 有關如何在設定檔中新增服務終結點的詳細資訊,請參閱[如何:在設定 中建立服務終結點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)。  
  
4. 啟用您的服務的 HTTP/GET 中繼資料端點。 關於詳細資訊,請參閱[如何:使用設定檔發佈服務的中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。  
  
## <a name="example"></a>範例  
 下面的範例代碼展示如何在代碼和設定檔中添加與ASP.NET Web 服務用戶端相容的 WCF 終結點。  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a>另請參閱

- [如何：在程式碼中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [HOW TO：使用程式碼發行服務的中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [如何：在設定中指定服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [HOW TO：在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [HOW TO：使用組態檔發行服務的中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [運輸安全](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [使用中繼資料](../../../../docs/framework/wcf/feature-details/using-metadata.md)
