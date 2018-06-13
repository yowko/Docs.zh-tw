---
title: 確保服務與用戶端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2e0440aadcad7c4297cdc6e6489ca004480420ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497408"
---
# <a name="securing-services-and-clients"></a>確保服務與用戶端的安全
程式設計 Windows Communication Foundation (WCF) 安全性著重於本節中的資訊。 一般來說，此安全性包括選取適當之系統提供的繫結、設定安全性項目的屬性，以及設定服務行為的屬性，而這些服務行為則會管理擷取認證以用於服務或用戶端的方法。 這些技術涵蓋大部分情況下，大部分使用者的安全性需求，如中所示[常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。 如果您的案例需要更多的功能，第一次看到[自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); 如果方案不會出現，請參閱[擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)。 如果您正在建立 （或與互通） 使用系統，提供豐富的宣告，請參閱[授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [WCF 安全性程式設計](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 用於確保訊息安全的程式設計模型概觀。  
  
 [傳輸安全性概觀](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 如何透過傳輸層確保訊息安全的概觀。  
  
 [訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 摘要說明使用 Windows Communication Foundation (WCF) 訊息層級安全性的理由。  
  
 [安全工作階段](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 保護 WCF 工作階段時所需的考量事項討論。  
  
 [使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 使用 X.509 憑證時，所需之部分常見工作的說明。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>相關章節  
 [安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [常見的安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [繫結和安全性](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>另請參閱  
 [基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Windows Server App Fabric 的安全性模型](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
