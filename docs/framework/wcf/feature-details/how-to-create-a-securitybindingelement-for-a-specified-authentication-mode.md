---
title: HOW TO：為指定的驗證模式建立 SecurityBindingElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
author: BrucePerlerMS
ms.openlocfilehash: 6204a2832bbdc0c6631903687fcd8a1c45b35d03
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088408"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="68d1b-102">HOW TO：為指定的驗證模式建立 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="68d1b-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
<span data-ttu-id="68d1b-103">Windows Communication Foundation (WCF) 提供數種模式的用戶端和服務來相互驗證。</span><span class="sxs-lookup"><span data-stu-id="68d1b-103">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="68d1b-104">您可以在 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別上使用靜態方法或透過組態，為這些驗證模式建立安全性繫結項目，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="68d1b-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="68d1b-105">如需 18 個驗證模式的詳細資訊，請參閱[SecurityBindingElement 驗證模式](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="68d1b-105">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68d1b-106">範例</span><span class="sxs-lookup"><span data-stu-id="68d1b-106">Example</span></span>  
 <span data-ttu-id="68d1b-107">下列程式碼範例示範為各種驗證模式建立繫結的方法。</span><span class="sxs-lookup"><span data-stu-id="68d1b-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68d1b-108">在建立 <xref:System.ServiceModel.Channels.SecurityBindingElement> 物件的執行個體之後，一些屬性是固定不變的，例如 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> 和 <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="68d1b-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="68d1b-109">在這類屬性上呼叫 `set` 並不會變更屬性。</span><span class="sxs-lookup"><span data-stu-id="68d1b-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="68d1b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68d1b-110">See Also</span></span>  
 [<span data-ttu-id="68d1b-111">SecurityBindingElement 驗證模式</span><span class="sxs-lookup"><span data-stu-id="68d1b-111">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [<span data-ttu-id="68d1b-112">如何：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="68d1b-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
