---
title: HOW TO：將 COM + 整合應用程式部署
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: 0dcaa7d12c7e35170dee155612f824ed22ab8b2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672795"
---
# <a name="how-to-deploy-a-com-integration-application"></a>HOW TO：將 COM + 整合應用程式部署
撰寫好 COM+ 整合應用程式後，您可能會想要將它部署在其他機器上。 此主題描述如何將 COM+ 整合應用程式從一部機器移到另一部機器。  
  
### <a name="moving-a-com-hosted-integration-app"></a>移動 COM+ 主控的整合應用程式  
  
1.  請確定兩台電腦上已安裝 WCF。  
  
2.  從機器 A 匯出應用程式。  
  
3.  將應用程式匯入機器 B。  
  
4.  設定應用程式根目錄。 根據慣例，根目錄是 %PROGRAMFILES%/ComPlus Applications/{AppGUID}。  
  
5.  從機器 A 的應用程式根目錄，將 Application.config 和 Application.manifest 檔案複製到機器 B 的應用程式根目錄。  
  
6.  在機器 B 的 Application.config 檔案中編輯服務端點位址，以識別適當的機器。 例如，將 `http://machineA/MyService` 變更為 `http://machineB/MyService`。  
  
### <a name="moving-a-web-hosted-integration-application"></a>移動 Web 主控的整合應用程式  
  
1.  請確定兩台電腦上已安裝 WCF。  
  
2.  從機器 A 匯出應用程式。  
  
3.  將應用程式匯入機器 B。  
  
4.  在機器 B 上建立 IIS VRoot。  
  
5.  從機器 A 的 VRoot，將 .svc 檔 (componentName.svc) 和 Web.config 檔複製到機器 B 上新建立的 VRoot。  
  
## <a name="see-also"></a>另請參閱
- [整合 COM+ 應用程式概觀](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [如何：設定 COM + 服務設定](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [如何：使用 COM + 服務模型組態工具](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
