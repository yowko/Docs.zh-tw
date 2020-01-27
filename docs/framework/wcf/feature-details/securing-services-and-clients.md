---
title: 確保服務與用戶端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 719ab26198bd7b83310025e03e541fa11b109612
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746423"
---
# <a name="securing-services-and-clients"></a>確保服務與用戶端的安全
本節中的資訊著重于 Windows Communication Foundation （WCF）中的安全性程式設計。 一般來說，此安全性包括選取適當之系統提供的繫結、設定安全性項目的屬性，以及設定服務行為的屬性，而這些服務行為則會管理擷取認證以用於服務或用戶端的方法。 這些技術涵蓋大部分使用者在大多數情況下的安全性需求，如常見的[安全性案例](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)所示。 如果您的案例需要更多功能，請先參閱[具有自訂系結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md);如果解決方案不明顯，請參閱[擴充安全性](../../../../docs/framework/wcf/extending/extending-security.md)。 如果您要建立（或交互操作）使用豐富宣告的系統，請參閱[授權](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)中的主題。  
  
## <a name="in-this-section"></a>本章節內容  
 [WCF 安全性程式設計](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 用於確保訊息安全的程式設計模型概觀。  
  
 [傳輸安全性概觀](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 如何透過傳輸層確保訊息安全的概觀。  
  
 [訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 摘要說明在 Windows Communication Foundation （WCF）中使用訊息層級安全性的原因。  
  
 [安全工作階段](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 保護 WCF 會話時所需考慮的討論。  
  
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
  
## <a name="see-also"></a>請參閱

- [基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Windows Server App Fabric 的安全性模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
