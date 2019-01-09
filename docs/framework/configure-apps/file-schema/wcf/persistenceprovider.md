---
title: '&lt;persistenceProvider&gt;'
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: ba02977a7df44931ae195040949e9a8eb0c141b5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54152017"
---
# <a name="ltpersistenceprovidergt"></a>&lt;persistenceProvider&gt;
指定要使用的持續性提供者實作型別，以及持續性作業所使用的逾時。  
  
 \<system.ServiceModel>  
\<行為 >  
\<serviceBehaviors>  
\<行為 >  
\<persistenceProvider >  
  
## <a name="syntax"></a>語法  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|persistenceOperationTimeout|<xref:System.TimeSpan> 值，此值會指定用於持續性作業的逾時。 預設值是"00: 00:30"。|  
|類型|字串，指定要使用的持續性提供者處理站之型別。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<行為 >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定行為項目。|  
  
## <a name="remarks"></a>備註  
 這個項目會指定持續性提供者，該提供者會用來序列化 WCF 服務的狀態。 它應該搭配在 HTTP 標頭中傳遞狀態資訊的 `wsHttpContextBinding` 使用。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
