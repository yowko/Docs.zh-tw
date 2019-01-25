---
title: 安全對話與安全工作階段
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
ms.openlocfilehash: 6b57f1b9511ef3751fd1f9e5c41d0a0c648972f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527896"
---
# <a name="secure-conversations-and-secure-sessions"></a>安全對話與安全工作階段
Windows Communication Foundation (WCF) 的功能是能夠建立安全工作階段之間彼此驗證並同意加密與數位簽章的程序的兩個端點。 例如，服務端點可能需要用戶端端點來傳送用於驗證的 X.509 憑證為基礎的安全性權杖。 一驗證用戶端後，服務端點即將安全性內容權杖 (SCT) 傳回用戶端，該用戶端用於保護工作階段內所有後續訊息的安全性。 由於 SCT 有對稱金鑰，因此建立此安全工作階段使得在兩個端點之間交換訊息組更有效率。 非對稱金鑰是 X.509 憑證的基礎，當它產生數位簽章或加密資料集時，需要遠比對稱金鑰多的運算功能。  
  
 啟動程序的原則 (定義中的第 6.2.7 節[1.3、WS-SecurityPolicy](https://go.microsoft.com/fwlink/?LinkId=99817)標準) 包含用來保護通道並驗證用戶端的 RST/SCT 和 RSTR/SCT 交換前的訊息安全性判斷提示。 特定 WCF 的標準繫結`Security.Message.EstablishSecurityContext`使用哪些控制項是否安全對話的屬性。 使用自訂繫結時啟動程序會以巢狀的安全性繫結項目會透過[ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)組態檔中，或藉由呼叫<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>在程式碼中。  
  
 如需有關工作階段的詳細資訊，請參閱[使用工作階段的](../../../../docs/framework/wcf/using-sessions.md)。  
  
## <a name="see-also"></a>另請參閱
- [工作階段、執行個體與並行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [如何：建立需要工作階段的服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
