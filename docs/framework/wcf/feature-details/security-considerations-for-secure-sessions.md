---
title: "安全工作階段的安全性考量 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# 安全工作階段的安全性考量
您必須考量下列會在實作安全工作階段時影響安全性的項目。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]安全性考量的詳細資訊，請參閱[安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)和 [安全性的最佳做法](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)。  
  
## 安全工作階段與中繼資料  
 當已建立安全工作階段且將 <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> 屬性設定為 `false` 時，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會傳送 `mssp:MustNotSendCancel` 判斷提示 \(Assertion\) 做為服務端點之 Web Services Description Language \(WSDL\) 文件內中繼資料的一部分。`mssp:MustNotSendCancel` 判斷提示會告知用戶端該服務無法對取消安全工作階段的要求做出回應。當 <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> 屬性設定為 `true` 時，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 就不會在 WSDL 文件中發出 `mssp:MustNotSendCancel` 判斷提示。當用戶端不再需要安全工作階段時，用戶端應該要傳送取消要求給服務。如果用戶端是使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 所產生，該用戶端程式碼就會依據 `mssp:MustNotSendCancel` 判斷提示的存在與否做出適當回應。  
  
## 安全對話與自訂權扙  
 由於 WS\-SecureConversation 規格中所定義的方式，因此混合使用自訂權扙及衍生金鑰可能會導致一些問題。根據規則，`wsse:SecurityTokenReference` 是參考衍生權扙 `/wsc:DerivedKeyToken/wsse:SecurityTokenReference` 的選用項目 這個選用項目用來指定安全性內容權扙、安全性權杖，或是用於衍生的共用金鑰\/秘密金鑰。如果沒有指定，系統會假定收件者端可以從訊息內文確認共用金鑰。如果無法確定內容，應該會出現如 `wsc:UnknownDerivationSource` 的錯誤。  
  
 這意味著如果您希望衍生自訂權扙，必須將以 `SecurityTokenReference` 項目包裝它的子句型別。也可以選擇關閉衍生，但是預設值為會衍生金鑰。如果您無法包裝金鑰，序列化衍生金鑰權杖仍會繼續進行，但是嘗試還原序列化時，便會擲回例外狀況。  
  
## 請參閱  
 [HOW TO：在 WSFederationHttpBinding 上停用安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)   
 [安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)   
 [安全性的最佳做法](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)