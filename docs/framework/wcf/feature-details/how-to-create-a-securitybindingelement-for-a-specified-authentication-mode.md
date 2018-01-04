---
title: "HOW TO：為指定的驗證模式建立 SecurityBindingElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 29cbe3c10ac68d508dc22781e46a6041f2d7eab7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>HOW TO：為指定的驗證模式建立 SecurityBindingElement
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供數個模式，可讓用戶端和服務用來相互驗證。 您可以在 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別上使用靜態方法或透過組態，為這些驗證模式建立安全性繫結項目，如下列範例所示。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]18 種驗證模式中，請參閱[SecurityBindingElement 驗證模式](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範為各種驗證模式建立繫結的方法。  
  
> [!NOTE]
>  在建立 <xref:System.ServiceModel.Channels.SecurityBindingElement> 物件的執行個體之後，一些屬性是固定不變的，例如 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> 和 <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>。 在這類屬性上呼叫 `set` 並不會變更屬性。  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>請參閱  
 [SecurityBindingElement 驗證模式](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [如何：使用 SecurityBindingElement 建立自訂繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
