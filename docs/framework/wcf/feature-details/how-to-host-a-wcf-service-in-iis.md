---
title: HOW TO：在 IIS 中裝載 WCF 服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 580b380a6c6349c6a4efa26e3eefe38bd660fa1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184928"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>HOW TO：在 IIS 中裝載 WCF 服務
本主題概述了創建 Internet 資訊服務 （IIS） 中託管的 Windows 通信基礎 （WCF） 服務所需的基本步驟。 本主題假設您熟悉 IIS，而且了解如何使用 IIS 管理工具建立與管理 IIS 應用程式。 有關 IIS 的更多資訊，請參閱[互聯網資訊服務](https://www.iis.net/)。 在 IIS 環境中運行的 WCF 服務充分利用了 IIS 功能，例如進程回收、空閒關閉、過程運行狀況監視和基於消息的啟動。 這個裝載選項要求必須正確設定 IIS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。 IIS 裝載只能和 HTTP 傳輸一起使用。  
  
 有關 WCF 和ASP.NET如何交互的詳細資訊，請參閱[WCF 服務和ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。 有關配置安全性的詳細資訊，請參閱[安全](../../../../docs/framework/wcf/feature-details/security.md)。  
  
 有關此示例的源副本，請參閱[使用內聯代碼進行 IIS 託管](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)。  
  
### <a name="to-create-a-service-hosted-by-iis"></a>若要建立 IIS 裝載的服務  
  
1. 確認您的電腦上已安裝 IIS 且正在執行中。 有關安裝和配置 IIS 的詳細資訊，請參閱[安裝和配置 IIS 7.0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)  
  
2. 為您的應用程式檔創建一個名為"IIS託管CalcService"的新資料夾，確保ASP.NET有權訪問該資料夾的內容，並使用 IIS 管理工具創建位於此應用程式目錄中的新 IIS 應用程式。 建立應用程式目錄的別名時，請使用 "IISHostedCalc"。  
  
3. 在應用程式目錄中建立名為 "service.svc" 的新檔案。 通過添加以下@ServiceHost元素編輯此檔。  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. 在應用程式目錄中建立 App_Code 子目錄。  
  
5. 在 App_Code 子目錄中建立名為 Service.cs 的程式碼檔案。  
  
6. 使用陳述式將以下加入至 Service.cs 檔案的最上方。  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. 使用陳述式之後，加入下列命名空間宣告。  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. 在命名空間宣告內定義服務合約，如下列程式碼所示。  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. 在符合合約定義之後實作服務合約，如下列程式碼所示。  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. 在應用程式目錄中建立名為 "Web.config" 的檔案，並將下列組態程式碼加入至該檔案中。 在運行時，WCF 基礎結構使用資訊構造用戶端應用程式可以與其通信的終結點。  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     此範例會在組態檔中明確地指定端點。 如果您沒有將任何端點加入至服務中，執行階段會為您加入預設端點。 有關預設終結點、綁定和行為的詳細資訊，請參閱 WCF 服務的[簡化配置](../../../../docs/framework/wcf/simplified-configuration.md)和[簡化配置](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
11. 若要確認服務裝載正確，請開啟 Internet Explorer 的執行個體，然後瀏覽到服務的 URL：`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>範例  
 以下是裝載於 IIS 之計算機服務的完整程式碼清單。  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>另請參閱

- [在網際網路資訊服務中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [裝載服務](../../../../docs/framework/wcf/hosting-services.md)
- [WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [安全性](../../../../docs/framework/wcf/feature-details/security.md)
- [Windows Server AppFabric 裝載功能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
