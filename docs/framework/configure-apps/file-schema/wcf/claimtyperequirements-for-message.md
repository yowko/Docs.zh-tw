---
title: '&lt;message&gt; 的 &lt;claimTypeRequirements&gt;'
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: 5c2bc05887701e78335629a37ce82815ac9abda5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628860"
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a>&lt;message&gt; 的 &lt;claimTypeRequirements&gt;
指定必要宣告型別的集合。  
  
 服務會使用這個集合，指定發行的權杖中的必要與選用的宣告，而用戶端會使用此權杖存取服務。 如果啟用 WSDL 發行，但 WCF 不要求發行的權杖中含有指定的宣告型別，則服務會在中繼資料公開需要的宣告型別。 如果服務希望強制需要的宣告型別要出現，應使用授權原則。  
  
 在聯合用戶端上，此集合包含必要與選用宣告的清單，用戶端要求發行的權杖時，此清單會傳送給安全性權杖服務。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
