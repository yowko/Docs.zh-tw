---
title: '&lt;claimTypeRequirements&gt; 項目的 &lt;clear&gt;'
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: 1e77e3c978c1e385aec983d5e2d4bea64697c43e
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145285"
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a>&lt;claimTypeRequirements&gt; 項目的 &lt;clear&gt;
指定移除聯合認證中的所有宣告型別。 這個動作可確保集合啟動時是空的。  
  
 \<system.ServiceModel>  
\<繫結 >  
\<wsFederatedBinding>  
\<繫結 >  
\<安全性 >  
\<message>  
\<claimTypeRequirements >  
  
## <a name="syntax"></a>語法  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|指定必要宣告型別的集合。 每個項目的型別為 <xref:System.ServiceModel.Configuration.ClaimTypeElement>。<br /><br /> 在聯合案例中，服務會聲明對傳入認證的需求。 例如，傳入認證必須處理特定的一組宣告型別。 這個集合中的每一個項目都會指定要顯示在聯合認證中的必要和選擇性宣告型別。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
