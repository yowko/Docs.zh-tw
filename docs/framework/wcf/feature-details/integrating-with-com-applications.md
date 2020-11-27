---
title: 整合 COM 應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: bc58e22b64284d66367302d55b5c9554c9ec0d72
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268231"
---
# <a name="integrating-with-com-applications"></a>整合 COM 應用程式

Windows Communication Foundation 您可以使用 WCF 服務的標記，將 WCF) 服務的 (直接整合到您現有的程式碼中。 服務 Moniker 可以從多種 COM 架構開發環境中使用，例如 Office VBA、Visual Basic 6.0 或 Visual C++ 6.0。  
  
## <a name="in-this-section"></a>本節內容  

 [整合 COM 應用程式概觀](integrating-with-com-applications-overview.md)  
 提供整合處理序主要部分的概觀。  
  
 [作法：註冊和設定服務 Moniker](how-to-register-and-configure-a-service-moniker.md)  
 若要在 COM 應用程式中使用 WCF 服務的標記，請向 COM 註冊必要的屬性化型別，並使用必要的系結設定來設定 COM 應用程式和標記。  
  
 [作法：使用 Windows Communication Foundation 服務 Moniker 且不註冊](use-the-wcf-service-moniker-without-registration.md)  
 說明如何取得格式為 Web Services Definition Language (WSDL) 文件的合約定義，或如何從 WS-MetadataExchange 端點取得該定義。  
  
 [作法：使用服務 Moniker 搭配 WSDL 合約](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 描述如何使用 WCF WSDL 標記呼叫 WCF 範例。  
  
 [作法：使用服務 Moniker 搭配中繼資料交換合約](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 說明如何使用指定 Mex 端點的 WCF 標記來呼叫 WCF 範例。  
  
 [作法：指定通道安全性認證](how-to-specify-channel-security-credentials.md)  
 WCF 服務的「標記」（WCF service）支援 `IChannelCredentials` 允許一系列替代方法來指定通道認證的介面。  
  
## <a name="reference"></a>參考  

 <xref:System.ServiceModel>  
  
## <a name="see-also"></a>另請參閱

- [與 COM + 應用程式整合](integrating-with-com-plus-applications.md)
