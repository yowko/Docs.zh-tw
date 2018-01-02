---
title: "&lt;gcAllowVeryLargeObjects&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5db777f147e2eca7644d5b5f1a4bc18c8401ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltgcallowverylargeobjectsgt-element"></a>&lt;gcAllowVeryLargeObjects&gt;項目
在 64 位元平台上，啟用總大小大於 2 GB 的陣列。  
  
 \<設定 > 項目  
\<runtime > 項目  
\<gcAllowVeryLargeObjects > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否在 64 位元平台上啟用的總大小大於 2 GB 的陣列。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會啟用大於 2 GB 的總大小的陣列。 這是預設值。|  
|`true`|在 64 位元平台時啟用大於 2 GB 的總大小的陣列。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 在應用程式組態檔中使用這個項目可讓陣列是大於 2 GB 的大小，但不會變更其他物件的大小或陣列大小的限制：  
  
-   陣列中元素的數目上限是<xref:System.UInt32.MaxValue?displayProperty=nameWithType>。  
  
-   2,147,483,591 (0x7FFFFFC7) 的位元組陣列和陣列的單一位元組結構，而其他類型的 2,146,435,071 (0X7FEFFFFF) 中任何單一維度的最大索引。  
  
-   字串和其他非陣列物件的大小上限不會變更。  
  
> [!CAUTION]
>  之前啟用此功能，請確定您的應用程式不包含假設所有陣列都都小於 2 GB 大小的 unsafe 程式碼。 例如，使用陣列做為緩衝區的 unsafe 程式碼可能容易受到緩衝區滿溢如果撰寫假設陣列將不會超過 2 GB。  
  
## <a name="example"></a>範例  
 下列範例會示範如何為應用程式啟用此功能。  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
