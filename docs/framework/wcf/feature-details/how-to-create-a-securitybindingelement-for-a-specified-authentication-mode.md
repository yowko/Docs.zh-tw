---
title: HOW TO：為指定的驗證模式建立 SecurityBindingElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: 62006397db3155d26a2c7bd327251b870a3b8460
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619924"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>HOW TO：為指定的驗證模式建立 SecurityBindingElement
Windows Communication Foundation (WCF) 提供數種模式的用戶端和服務來相互驗證。 您可以在 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別上使用靜態方法或透過組態，為這些驗證模式建立安全性繫結項目，如下列範例所示。  
  
 如需 18 個驗證模式的詳細資訊，請參閱[SecurityBindingElement 驗證模式](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範為各種驗證模式建立繫結的方法。  
  
> [!NOTE]
>  在建立 <xref:System.ServiceModel.Channels.SecurityBindingElement> 物件的執行個體之後，一些屬性是固定不變的，例如 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> 和 <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>。 在這類屬性上呼叫 `set` 並不會變更屬性。  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>另請參閱
- [SecurityBindingElement 驗證模式](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
- [如何：建立自訂繫結使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
