---
title: "整合 COM 應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a0e625beaf20f6445099d8fb15cb175d3d71a860
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications"></a>整合 COM 應用程式
可以使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務 Moniker，將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務直接整合至現有的程式碼。 服務 Moniker 可以從多種 COM 架構開發環境中使用，例如 Office VBA、Visual Basic 6.0 或 Visual C++ 6.0。  
  
## <a name="in-this-section"></a>本章節內容  
 [整合 COM 應用程式概觀](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 提供整合處理序主要部分的概觀。  
  
 [如何： 註冊並設定服務 Moniker](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 若要在 COM 應用程式內使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker，請以 COM 登錄必要的屬性類型，並以必要的繫結組態設定 COM 應用程式和 Moniker。  
  
 [如何： 使用 Windows Communication Foundation 服務 Moniker，但不註冊](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 說明如何取得格式為 Web Services Definition Language (WSDL) 文件的合約定義，或如何從 WS-MetadataExchange 端點取得該定義。  
  
 [如何： 使用服務 Moniker 搭配 WSDL 合約](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 描述如何使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL Moniker 呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例。  
  
 [如何： 使用服務 Moniker 搭配中繼資料交換合約](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 描述如何使用指定 Mex 端點的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker 呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例。  
  
 [如何： 指定通道安全性認證](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker 支援 `IChannelCredentials` 介面，這個介面提供一系列的替代方法以指定通道認證。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a>另請參閱  
 [整合 COM + 應用程式](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
