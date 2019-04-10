---
title: HOW TO：在 IIS 中裝載 WCF 服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: f106ce1bca67f8b88df0835496eea0b3297ac946
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59309676"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>HOW TO：在 IIS 中裝載 WCF 服務
本主題概要說明建立 Windows Communication Foundation (WCF) 服務裝載在網際網路資訊服務 (IIS) 所需的基本步驟。 本主題假設您熟悉 IIS，而且了解如何使用 IIS 管理工具建立與管理 IIS 應用程式。 如需 IIS 的詳細資訊，請參閱[Internet Information Services](https://go.microsoft.com/fwlink/?LinkId=132449)。 WCF 服務會在 IIS 環境中的執行採用完整的 IIS 功能，例如處理序回收、 閒置關機、 處理序健康狀態監控，以及訊息啟動。 這個裝載選項要求必須正確設定 IIS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。 IIS 裝載只能和 HTTP 傳輸一起使用。  
  
 如需有關如何 WCF 及[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]互動，請參閱 < [WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。 如需有關如何設定安全性的詳細資訊，請參閱 <<c0> [ 安全性](../../../../docs/framework/wcf/feature-details/security.md)。  
  
 如需此範例中的來源複本，請參閱[IIS 裝載使用內嵌程式碼](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)。  
  
### <a name="to-create-a-service-hosted-by-iis"></a>若要建立 IIS 裝載的服務  
  
1. 確認您的電腦上已安裝 IIS 且正在執行中。 如需安裝和設定 IIS 的詳細資訊，請參閱[安裝和設定 IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=132128)  
  
2. 為您的應用程式檔案建立稱為 "IISHostedCalcService" 新的資料夾，確保 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 能夠存取資料夾內容，然後使用 IIS 管理工具來建立實際位於此應用程式目錄中的新 IIS 應用程式。 建立應用程式目錄的別名時，請使用 "IISHostedCalc"。  
  
3. 在應用程式目錄中建立名為 "service.svc" 的新檔案。 編輯此檔案中加入下列@ServiceHost項目。  
  
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
  
10. 在應用程式目錄中建立名為 "Web.config" 的檔案，並將下列組態程式碼加入至該檔案中。 在執行階段，WCF 基礎結構會使用資訊以建構用戶端應用程式可以與通訊的端點。  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]      
  
     此範例會在組態檔中明確地指定端點。 如果您沒有將任何端點加入至服務中，執行階段會為您加入預設端點。 如需有關預設端點、 繫結和行為，請參閱[Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
11. 若要確定服務裝載正確，請開啟 Internet Explorer 並瀏覽至服務的 URL 的執行個體： `http://localhost/IISHostedCalc/Service.svc`  
  
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
- [Windows Server AppFabric 裝載功能](https://go.microsoft.com/fwlink/?LinkId=201276)
