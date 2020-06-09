---
title: 確保服務與用戶端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: db0a0dcfbe04a7b7dbfabfed59f9b8637d0a2797
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586204"
---
# <a name="securing-services-and-clients"></a>確保服務與用戶端的安全
本節中的資訊著重于 Windows Communication Foundation （WCF）中的安全性程式設計。 一般來說，此安全性包括選取適當之系統提供的繫結、設定安全性項目的屬性，以及設定服務行為的屬性，而這些服務行為則會管理擷取認證以用於服務或用戶端的方法。 這些技術涵蓋大部分使用者在大多數情況下的安全性需求，如常見的[安全性案例](common-security-scenarios.md)所示。 如果您的案例需要更多功能，請先參閱[具有自訂系結的安全性功能](security-capabilities-with-custom-bindings.md);如果解決方案不明顯，請參閱[擴充安全性](../extending/extending-security.md)。 如果您要建立（或交互操作）使用豐富宣告的系統，請參閱[授權](authorization-in-wcf.md)中的主題。  
  
## <a name="in-this-section"></a>本節內容  
 [WCF 安全性程式設計](programming-wcf-security.md)  
 用於確保訊息安全的程式設計模型概觀。  
  
 [傳輸安全性概觀](transport-security-overview.md)  
 如何透過傳輸層確保訊息安全的概觀。  
  
 [訊息安全性](message-security-in-wcf.md)  
 摘要說明在 Windows Communication Foundation （WCF）中使用訊息層級安全性的原因。  
  
 [安全工作階段](secure-sessions.md)  
 保護 WCF 會話時所需考慮的討論。  
  
 [Working with Certificates](working-with-certificates.md)  
 使用 X.509 憑證時，所需之部分常見工作的說明。  
  
## <a name="reference"></a>參考  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>相關章節  
 [安全性概念](security-concepts.md)  
  
 [擴充安全性](../extending/extending-security.md)  
  
 [常見的安全性案例](common-security-scenarios.md)  
  
 [繫結和安全性](bindings-and-security.md)  
  
 [自訂繫結的安全性功能](security-capabilities-with-custom-bindings.md)  
  
 [擴充安全性](../extending/extending-security.md)  
  
 [授權](authorization-in-wcf.md)  
  
## <a name="see-also"></a>請參閱

- [基本 WCF 程式設計](../basic-wcf-programming.md)
- [Windows Server AppFabric 的資訊安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
