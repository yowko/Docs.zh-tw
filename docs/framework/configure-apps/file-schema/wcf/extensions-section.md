---
title: "&lt;extensions&gt; 區段"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a564b85609ca289f382789844d4e78252bb66482
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltextensionsgt-section"></a>&lt;extensions&gt; 區段
這個組態區段包含延伸的集合，可讓使用者建立使用者定義的繫結、行為和其他方面的延伸。  
  
\<系統。ServiceModel >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.serviceModel>  
  <extensions>  
    <bindingExtensions>  
    </bindingExtensions>  
    <behaviorExtensions>  
    </behaviorExtensions>  
    <bindingElementExtensions>  
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<behaviorExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|這個區段包含指定行為延伸的子項目，可讓使用者自訂服務或端點行為。|  
|[\<bindingElementExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|這個區段會啟用電腦或應用程式組態檔中自訂繫結項目的使用。|  
|[\<bindingExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|這個區段包含指定繫結延伸的子項目，可讓使用者自訂繫結。|  
|[\<endpointExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|這個區段包含會註冊標準端點的子項目。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|system.ServiceModel|所有 WCF 組態項目的根項目。|
