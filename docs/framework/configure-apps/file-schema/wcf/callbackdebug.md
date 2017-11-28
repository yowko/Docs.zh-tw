---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 93b89787795cb58644b79ae4795e7a036741e138
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcallbackdebuggt"></a>&lt;callbackDebug&gt;
指定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 回呼物件的服務偵錯。  
  
 \<系統。ServiceModel >  
\<行為 >  
\<endpointBehaviors >  
\<行為 >  
\<callbackDebug >  
  
## <a name="syntax"></a>語法  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a>類型  
 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|這個值會指定用戶端回呼物件是否將 SOAP 錯誤中的 Managed 例外狀況資訊傳回給服務。<br /><br /> 如果您以程式設計方式將這個屬性設定為 `true`，您可以讓用戶端回呼物件中的 Managed 例外狀況資訊的流動回到服務，以達偵錯的目的。 **注意：**傳回 managed 例外狀況資訊傳回用戶端可能會有的安全性風險。 這是因為例外狀況細節會公開內部服務實作 (Implementation) 的相關資訊，可能會被未經授權的用戶端加以利用。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<行為 >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
