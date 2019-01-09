---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: a024ca89bd766681f25b992f1d2c66a92e3b31b7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150197"
---
# <a name="datacontractserializer"></a>dataContractSerializer
包含 <xref:System.Runtime.Serialization.DataContractSerializer> 的組態資料。  
  
 \<system.ServiceModel>  
\<行為 >  
\<endpointBehaviors>  
\<行為 >  
\<dataContractSerializer >  
  
## <a name="syntax"></a>語法  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|元素|描述|  
|-------------|-----------------|  
|ignoreExtensionDataObject|布林值，指定當端點序列化或還原序列化時，是否略過端點所提供的資料。|  
|maxItemsInObjectGraph|整數，指定要序列化或還原序列化的項目數上限。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<行為 >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## <a name="remarks"></a>備註  
 如需已知型別的詳細資訊，請參閱 <xref:System.Runtime.Serialization.DataContractSerializer> 文件。  
  
> [!CAUTION]
>  `<dataContractSerializer>` 行為項目 (如果有的話) 必須永遠出現在組態檔中 `<enableWebScript>` 行為項目之前。 否則，產生的行為未定義。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [資料合約已知類型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [資料傳輸與序列化](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
