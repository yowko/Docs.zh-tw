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
ms.openlocfilehash: dc3bbe0ee72ca5583b1e52a61c914ad866a22a05
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596806"
---
# <a name="integrating-with-com-applications"></a>整合 COM 應用程式
Windows Communication Foundation （WCF）服務可以使用 WCF 服務標記，直接整合到您現有的程式碼中。 服務 Moniker 可以從多種 COM 架構開發環境中使用，例如 Office VBA、Visual Basic 6.0 或 Visual C++ 6.0。  
  
## <a name="in-this-section"></a>本節內容  
 [與 COM 應用程式整合總覽](integrating-with-com-applications-overview.md)  
 提供整合處理序主要部分的概觀。  
  
 [如何：註冊和設定服務 Moniker](how-to-register-and-configure-a-service-moniker.md)  
 若要在 COM 應用程式中使用 WCF 服務名字標記，請向 COM 註冊必要的屬性化型別，並以必要的系結設定來設定 COM 應用程式和名字。  
  
 [HOW TO：使用 Windows Communication Foundation 服務 Moniker 且不註冊](use-the-wcf-service-moniker-without-registration.md)  
 說明如何取得格式為 Web Services Definition Language (WSDL) 文件的合約定義，或如何從 WS-MetadataExchange 端點取得該定義。  
  
 [如何：使用服務 Moniker 搭配 WSDL 合約](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 描述如何使用 WCF WSDL 標記呼叫 WCF 範例。  
  
 [如何：使用服務 Moniker 搭配中繼資料交換合約](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 描述如何使用指定 Mex 端點的 WCF 標記呼叫 WCF 範例。  
  
 [HOW TO：指定通道安全性認證](how-to-specify-channel-security-credentials.md)  
 WCF 服務的「標記」支援 `IChannelCredentials` 介面，可允許一系列的替代方法來指定通道認證。  
  
## <a name="reference"></a>參考  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a>請參閱

- [與 COM + 應用程式整合](integrating-with-com-plus-applications.md)
