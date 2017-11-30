---
title: "數位簽章加密"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 147f62a895983557267d0a18fdd1ea261ae6c855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="encryption-of-digital-signatures"></a>數位簽章加密
根據預設，訊息會經過簽署及加密，並且簽章會經過數位加密。 您可以透過使用 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 或 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 的執行個體建立自訂繫結，並將其中一個類別的 `MessageProtectionOrder` 屬性設定為 <xref:System.ServiceModel.Security.MessageProtectionOrder> 列舉值的方式來控制。 預設為 <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>。 這個過程的耗用時間會比純粹簽署和加密的耗用時間多出 10% 至 40%。 然而，停用簽章加密可能會使攻擊者得以猜測訊息內容。 這是有可能的，因為簽章項目包含訊息中每個簽署部分的純文字雜湊程式碼。 例如，雖然訊息本文預設會經過加密，但未加密的簽章會包含訊息本文的雜湊程式碼。 如果訊息內容較短，攻擊者可能會推算出內容。 加密簽章則可降低或排除這種可能性。  
  
 因此，只有在內容不具重要性以及效能提升是關鍵要素時才可停用簽章加密，例如，當傳送不具安全性含義的大型二進位檔案時。  
  
### <a name="to-disable-digital-signing"></a>若要停用數位簽章  
  
1.  建立 <xref:System.ServiceModel.Channels.CustomBinding>。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][How to： 建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。  
  
2.  在繫結集合中加入 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 或 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>。  
  
3.  將 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>，或將 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立自訂繫結，請參閱[Creating User-Defined 繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立自訂繫結的特定驗證模式，請參閱[How to： 指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 [如何： 建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [建立使用者定義繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [如何： 指定的驗證模式建立 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
