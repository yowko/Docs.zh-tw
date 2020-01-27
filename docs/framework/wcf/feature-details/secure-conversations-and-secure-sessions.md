---
title: 安全對話與安全工作階段
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 887b2e6e6553a910de046950514869907519cf35
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746459"
---
# <a name="secure-conversations-and-secure-sessions"></a>安全對話與安全工作階段
Windows Communication Foundation （WCF）的一項功能是能夠在兩個端點之間建立安全會話，以彼此驗證並同意加密與數位簽章程式。 例如，服務端點可能需要用戶端端點來傳送用於驗證的 X.509 憑證為基礎的安全性權杖。 一驗證用戶端後，服務端點即將安全性內容權杖 (SCT) 傳回用戶端，該用戶端用於保護工作階段內所有後續訊息的安全性。 由於 SCT 有對稱金鑰，因此建立此安全工作階段使得在兩個端點之間交換訊息組更有效率。 非對稱金鑰是 X.509 憑證的基礎，當它產生數位簽章或加密資料集時，需要遠比對稱金鑰多的運算功能。  
  
 啟動程式原則（定義于[SecurityPolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html)標準的區段6.2.7）包含用來保護通道和在 RST/SCT 和 RSTR/sct 交換之前驗證用戶端的訊息安全性判斷提示。 某些 WCF 標準系結具有 `Security.Message.EstablishSecurityContext` 屬性，可控制是否使用安全對話。 使用自訂系結時，啟動程式是藉由在設定檔中[\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) ，或是在程式碼中呼叫 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> 來表示。  
  
 如需有關會話的詳細資訊，請參閱[使用會話](../../../../docs/framework/wcf/using-sessions.md)。  
  
## <a name="see-also"></a>請參閱

- [工作階段、執行個體與並行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [如何：建立需要工作階段的服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
