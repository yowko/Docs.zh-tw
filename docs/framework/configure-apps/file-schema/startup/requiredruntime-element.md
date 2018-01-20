---
title: "&lt;requiredRuntime&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2e864eec2ddf51d5cc88110654f6c23f146938d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ltrequiredruntimegt-element"></a>&lt;requiredRuntime&gt;項目
指定應用程式只支援 Common Language Runtime 1.0 版。 這個項目已被取代，無法再使用。 [ `supportedRuntime` ](supportedruntime-element.md)應該改為使用項目。
  
 \<configuration>  
\<startup>  
\<requiredRuntime>  
  
## <a name="syntax"></a>語法  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`version`|選擇性屬性。<br /><br /> 字串值，指定這個應用程式支援的.NET framework 版本。 字串值必須符合.NET Framework 安裝根目錄下的目錄名稱。 無法剖析的字串值的內容。|  
|`safemode`|選擇性屬性。<br /><br /> 指定是否執行階段啟始程式碼搜尋登錄，以判斷執行階段版本。|  
  
## <a name="safemode-attribute"></a>安全模式屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|執行階段啟始程式碼會在登錄中尋找。 這是預設值。|  
|`true`|執行階段啟始程式碼不會看起來不在登錄中。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`startup`|包含`<requiredRuntime>`項目。|  
  
## <a name="remarks"></a>備註  
 只支援 1.0 版的執行階段建置的應用程式必須使用`<requiredRuntime>`項目。 使用 1.1 版或更新版本的執行階段所建置的應用程式必須使用`<supportedRuntime>`項目。  
  
> [!NOTE]
>  如果您使用[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函式指定組態檔，您必須使用`<requiredRuntime>`執行階段的所有版本的項目。 `<supportedRuntime>`使用時，便會忽略元素[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)。  
  
 `version`屬性字串必須符合指定之版本的.NET framework 的安裝資料夾名稱。 這個字串不會解譯。 如果執行階段啟始程式碼找不到相符的資料夾，則執行階段不會載入;啟始程式碼會顯示錯誤訊息並結束。  
  
> [!NOTE]
>  裝載於 Microsoft Internet Explorer 的應用程式的啟始程式碼會忽略`<requiredRuntime>`項目。  
  
## <a name="example"></a>範例  
 下列範例顯示如何在組態檔中指定的執行階段版本。  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [啟動設定結構描述](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> 指定要使用哪一個執行階段版本](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
