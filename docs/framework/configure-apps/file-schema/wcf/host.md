---
title: "&lt;主機&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7177c62af8501258ad8709bff88cb85488b56727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="lthostgt"></a>&lt;主機&gt;
指定服務主機的設定。  
  
 \<系統。ServiceModel >  
\<服務 >  
\<服務 >  
\<主機 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<s >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|`baseAddress` 項目的集合，指定服務主機使用的基底位址。|  
|[\<逾時 >](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|組態項目，指定允許服務主機開啟或關閉的時間間隔。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<服務 >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|指定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務的設定。|  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)
