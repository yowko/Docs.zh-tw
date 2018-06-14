---
title: 安全對話與安全工作階段
ms.date: 03/30/2017
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c87f53bcaa167dd7b3b039c70129efca43742c1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497603"
---
# <a name="secure-conversations-and-secure-sessions"></a>安全對話與安全工作階段
Windows Communication Foundation (WCF) 的功能是能夠建立彼此驗證並同意加密與數位簽章程序的兩個端點之間的安全工作階段。 例如，服務端點可能需要用戶端端點來傳送用於驗證的 X.509 憑證為基礎的安全性權杖。 一驗證用戶端後，服務端點即將安全性內容權杖 (SCT) 傳回用戶端，該用戶端用於保護工作階段內所有後續訊息的安全性。 由於 SCT 有對稱金鑰，因此建立此安全工作階段使得在兩個端點之間交換訊息組更有效率。 非對稱金鑰是 X.509 憑證的基礎，當它產生數位簽章或加密資料集時，需要遠比對稱金鑰多的運算功能。  
  
 啟動程序的原則 (定義於區段 6.2.7 [Ws-securitypolicy](http://go.microsoft.com/fwlink/?LinkId=99817)標準) 包含用來保護通道以及驗證用戶端，則 RST/SCT 和 RSTR/SCT 交換的訊息安全性判斷提示。 某些 WCF 標準繫結`Security.Message.EstablishSecurityContext`屬性使用的控制項是否安全對話。 使用自訂繫結時啟動安裝程式會以巢狀安全性繫結項目，透過[ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)組態檔中，或藉由呼叫<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>程式碼中。  
  
 如需工作階段的詳細資訊，請參閱[Sessions<](../../../../docs/framework/wcf/using-sessions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作階段、執行個體與並行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [如何：建立需要工作階段的服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
