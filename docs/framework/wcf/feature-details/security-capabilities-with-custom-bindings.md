---
title: 自訂繫結的安全性功能
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 1b12907481ccb3f3c5f4b8aaba6ede8ebfa6228a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288303"
---
# <a name="security-capabilities-with-custom-bindings"></a>自訂繫結的安全性功能

您可以使用一種系統提供的繫結來執行常見的安全性工作。 不過，如果需要更多控制，您可以依照這些主題中的說明，使用 <xref:System.ServiceModel.Channels.SecurityBindingElement> 來建立自訂繫結。 如需自訂系結的詳細資訊，請參閱 [自訂](../extending/custom-bindings.md)系結。  
  
## <a name="in-this-section"></a>本節內容  

 [SecurityBindingElement 驗證模式](securitybindingelement-authentication-modes.md)  
 說明自訂繫結的可能驗證模式。  
  
 [作法：使用 SecurityBindingElement 建立自訂繫結](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 說明建立包含安全性項目之自訂繫結的基本步驟。  
  
 [作法：為指定的驗證模式建立 SecurityBindingElement](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 說明如何建立指定之驗證模式的安全性項目。  
  
 [作法：在 WSFederationHttpBinding 上停用安全工作階段](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 說明如何在建立聯合服務時停用安全工作階段。  
  
 [作法：啟用訊息重新執行偵測](how-to-enable-message-replay-detection.md)  
 說明如何判斷何時會發生重新執行攻擊。  
  
 [作法：建立支援的認證](how-to-create-a-supporting-credential.md)  
 說明如何為需要認證的服務提供支援認證。  
  
 [作法：設定簽章確認](how-to-set-up-a-signature-confirmation.md)  
 說明在數位簽署訊息時的簽章確認步驟。  
  
 [作法：設定最大時鐘誤差](how-to-set-a-max-clock-skew.md)  
 描述如何設定服務與用戶端之間的最大允許時間差異。  
  
 [作法：停用數位簽章加密](how-to-disable-encryption-of-digital-signatures.md)  
 說明如何從停用數位簽章加密來創造效能優勢。  
  
## <a name="reference"></a>參考  

 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a>相關章節  

 [了解保護層級](../understanding-protection-level.md)  
  
 [確保服務與用戶端的安全](securing-services-and-clients.md)  
  
## <a name="see-also"></a>另請參閱

- [繫結和安全性](bindings-and-security.md)
- [安全性概觀](security-overview.md)
- [系統提供的繫結](../system-provided-bindings.md)
