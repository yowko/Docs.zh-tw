---
title: 安全工作階段的安全性考量
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
author: BrucePerlerMS
ms.openlocfilehash: 470ffc007ed73b28beba24bd0eb9c670dea9337d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199966"
---
# <a name="security-considerations-for-secure-sessions"></a>安全工作階段的安全性考量
您必須考量下列會在實作安全工作階段時影響安全性的項目。 如需有關安全性考量的詳細資訊，請參閱[安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)並[安全性的最佳做法](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)。  
  
## <a name="secure-sessions-and-metadata"></a>安全工作階段與中繼資料  
 當建立安全工作階段並<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A>屬性設定為`false`，Windows Communication Foundation (WCF) 會傳送`mssp:MustNotSendCancel`一部分的 Web 服務描述語言 (WSDL) 文件中的中繼資料的判斷提示服務端點。 `mssp:MustNotSendCancel` 判斷提示會告知用戶端該服務無法對取消安全工作階段的要求做出回應。 當<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A>屬性設定為`true`，則 WCF 不會發出`mssp:MustNotSendCancel`WSDL 文件中的判斷提示。 當用戶端不再需要安全工作階段時，用戶端應該要傳送取消要求給服務。 使用產生的用戶端時[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，用戶端程式碼做出適當回應的存在與否`mssp:MustNotSendCancel`判斷提示。  
  
## <a name="secure-conversations-and-custom-tokens"></a>安全對話與自訂權扙  
 由於 WS-SecureConversation 規格中所定義的方式，因此混合使用自訂權扙及衍生金鑰可能會導致一些問題。 規格指出`wsse:SecurityTokenReference`是參考衍生的語彙基元的選擇性元素:"`/wsc:DerivedKeyToken/wsse:SecurityTokenReference`此選擇性項目用來指定安全性內容權杖、 安全性權杖或共用的金鑰/秘密金鑰用於衍生。 如果沒有指定，系統會假定收件者端可以從訊息內文確認共用金鑰。 如果無法判斷內容，然後將這類錯誤`wsc:UnknownDerivationSource`應該引發。 」  
  
 這意味著如果您希望衍生自訂權扙，必須將以 `SecurityTokenReference` 項目包裝它的子句型別。 也可以選擇關閉衍生，但是預設值為會衍生金鑰。 如果您無法包裝金鑰，序列化衍生金鑰權杖仍會繼續進行，但是嘗試還原序列化時，便會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [如何：在 WSFederationHttpBinding 上停用安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [安全性的最佳做法](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
