---
title: "安全對話與安全工作階段"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48cb104a-532d-40ae-aa57-769dae103fda
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 6647ef8124279e9fc0b3049beb5c87f887125dfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="secure-conversations-and-secure-sessions"></a>安全對話與安全工作階段
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的其中一個特點是在兩個端點之間建立安全工作階段的能力，端點會互相驗證並同意加密與數位簽章程序。 例如，服務端點可能需要用戶端端點來傳送用於驗證的 X.509 憑證為基礎的安全性權杖。 一驗證用戶端後，服務端點即將安全性內容權杖 (SCT) 傳回用戶端，該用戶端用於保護工作階段內所有後續訊息的安全性。 由於 SCT 有對稱金鑰，因此建立此安全工作階段使得在兩個端點之間交換訊息組更有效率。 非對稱金鑰是 X.509 憑證的基礎，當它產生數位簽章或加密資料集時，需要遠比對稱金鑰多的運算功能。  
  
 啟動程序的原則 (定義於區段 6.2.7 [Ws-securitypolicy](http://go.microsoft.com/fwlink/?LinkId=99817)標準) 包含用來保護通道以及驗證用戶端，則 RST/SCT 和 RSTR/SCT 交換的訊息安全性判斷提示。 某些 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 標準繫結的 `Security.Message.EstablishSecurityContext` 屬性可控制是否使用安全對話。 使用自訂繫結時啟動安裝程式會以巢狀安全性繫結項目，透過[ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)組態檔中，或藉由呼叫<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>程式碼中。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]工作階段，請參閱[Sessions<](../../../../docs/framework/wcf/using-sessions.md)。  
  
## <a name="see-also"></a>另請參閱  
 [工作階段中，執行個體與並行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [如何： 建立需要工作階段的服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
