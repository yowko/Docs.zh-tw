---
title: 安全對話與安全工作階段
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 3245c062db003cc387eff7af92fabe1554311c73
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590224"
---
# <a name="secure-conversations-and-secure-sessions"></a>安全對話與安全工作階段
Windows Communication Foundation （WCF）的一項功能是能夠在兩個端點之間建立安全會話，以彼此驗證並同意加密與數位簽章程式。 例如，服務端點可能需要用戶端端點來傳送用於驗證的 X.509 憑證為基礎的安全性權杖。 一驗證用戶端後，服務端點即將安全性內容權杖 (SCT) 傳回用戶端，該用戶端用於保護工作階段內所有後續訊息的安全性。 由於 SCT 有對稱金鑰，因此建立此安全工作階段使得在兩個端點之間交換訊息組更有效率。 非對稱金鑰是 X.509 憑證的基礎，當它產生數位簽章或加密資料集時，需要遠比對稱金鑰多的運算功能。  
  
 啟動程式原則（定義于[SecurityPolicy](https://docs.oasis-open.org/ws-sx/ws-securitypolicy/200702/ws-securitypolicy-1.2-spec-os.html)標準的區段6.2.7）包含用來保護通道和在 RST/SCT 和 RSTR/sct 交換之前驗證用戶端的訊息安全性判斷提示。 某些 WCF 標準系結具有 `Security.Message.EstablishSecurityContext` 屬性，可控制是否使用安全對話。 使用自訂系結時，啟動程式會藉由將安全性繫結項目（不論是 [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) 在設定檔中）或在程式碼中呼叫來表示 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> 。  
  
 如需有關會話的詳細資訊，請參閱[使用會話](../using-sessions.md)。  
  
## <a name="see-also"></a>請參閱

- [工作階段、執行個體與並行](sessions-instancing-and-concurrency.md)
- [HOW TO：建立需要工作階段的服務](how-to-create-a-service-that-requires-sessions.md)
