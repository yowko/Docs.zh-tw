---
title: 安全對話與安全工作階段
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 6cbf877c80b7d10705868120c4ec4a7b40895114
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288498"
---
# <a name="secure-conversations-and-secure-sessions"></a>安全對話與安全工作階段

Windows Communication Foundation (WCF) 的一個功能，就是能夠在兩個端點之間建立安全會話，以互相驗證並同意加密與數位簽章程式。 例如，服務端點可能需要用戶端端點來傳送用於驗證的 X.509 憑證為基礎的安全性權杖。 一驗證用戶端後，服務端點即將安全性內容權杖 (SCT) 傳回用戶端，該用戶端用於保護工作階段內所有後續訊息的安全性。 由於 SCT 有對稱金鑰，因此建立此安全工作階段使得在兩個端點之間交換訊息組更有效率。 非對稱金鑰是 X.509 憑證的基礎，當它產生數位簽章或加密資料集時，需要遠比對稱金鑰多的運算功能。  
  
 在 SecurityPolicy standard) 區段6.2.7 中定義的啟動 [程式](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html) 原則 (包含用來保護通道的訊息安全性判斷提示，並在 RST/SCT 和 RSTR/sct 交換之前驗證用戶端。 某些 WCF 標準系結具有 `Security.Message.EstablishSecurityContext` 屬性，可控制是否使用安全對話。 使用自訂系結時，會透過 [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 在設定檔中或在程式碼中呼叫的方式，將安全性繫結項目的程式碼，藉以表示啟動程式 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> 。  
  
 如需會話的詳細資訊，請參閱 [使用會話](../using-sessions.md)。  
  
## <a name="see-also"></a>另請參閱

- [工作階段、執行個體與並行](sessions-instancing-and-concurrency.md)
- [作法：建立需要工作階段的服務](how-to-create-a-service-that-requires-sessions.md)
