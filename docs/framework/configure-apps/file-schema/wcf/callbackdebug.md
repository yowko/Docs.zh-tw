---
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 02632cc3f668bb9e4cc6f8c9726d7bcb3cab2c5d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183815"
---
# \<callbackDebug>

指定 Windows Communication Foundation (WCF) 回呼物件的服務偵錯工具。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a>類型  

 `Type`  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|這個值會指定用戶端回呼物件是否將 SOAP 錯誤中的 Managed 例外狀況資訊傳回給服務。<br /><br /> 如果您以程式設計方式將這個屬性設定為 `true`，您可以讓用戶端回呼物件中的 Managed 例外狀況資訊的流動回到服務，以達偵錯的目的。 **注意：**  將 managed 例外狀況資訊傳回給用戶端可能會有安全性風險。 這是因為例外狀況細節會公開內部服務實作 (Implementation) 的相關資訊，可能會被未經授權的用戶端加以利用。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|指定端點行為。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
