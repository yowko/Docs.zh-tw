---
title: "&lt;啟動&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: bd2356845c76e81ce2efe87bdf247de293d6115d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltstartupgt-element"></a>&lt;啟動&gt;項目
指定 common language runtime 啟動資訊。  
  
 \<configuration>  
\<啟動 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|選擇性屬性。<br /><br /> 指定是否要啟用[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]執行階段啟用原則，或使用[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]啟用原則。|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy 屬性  
  
|值|說明|  
|-----------|-----------------|  
|`true`|啟用[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]所選的執行階段，也就是繫結舊版執行階段啟用技術的執行階段啟用原則 (例如[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) 至執行階段從組態檔，而不是選擇須它們在 CLR 2.0 版。 因此，如果選擇 4 或更新版本的 CLR 版本，則從組態檔，建立與舊版.NET Framework 的混合模式組件會載入與所選的 CLR 版本。 將此值設定防止 CLR 1.1 版或 CLR 2.0 版載入到相同的程序，確實停用的同處理序並存的功能。|  
|`false`|使用預設的啟用原則的[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]和更新版本中，也就是允許舊版執行階段啟用技術，載入程序中的 CLR 版本 1.1 或 2.0。 設定此值可防止在載入到.NET Framework 4 或更新版本，除非其建置.NET Framework 4 或更新版本的混合模式組件。 預設值為這個值。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|說明|  
|-------------|-----------------|  
|[\<requiredRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|指定應用程式只支援 Common Language Runtime 1.0 版。 執行階段版本 1.1 或更新版本建置的應用程式應該使用 **\<supportedRuntime >**項目。|  
|[\<supportedRuntime>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|指定應用程式支援的通用語言執行平台版本。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="remarks"></a>備註  
 **\<SupportedRuntime >**使用 1.1 版或更新版本的執行階段所建置的所有應用程式應該使用項目。 只支援 1.0 版的執行階段建置的應用程式必須使用 **\<requiredRuntime >**項目。  
  
 在 Microsoft Internet Explorer 所裝載的應用程式的啟動程式碼會忽略**\<啟動 >**項目和其子項目。  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy 屬性  
 這個屬性很有用，如果您的應用程式使用舊版啟用路徑，例如[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)，而且希望這些路徑啟用 CLR，而不是較早的版本中，第 4 版或如果您的應用程式使用建置[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]但具有相依性的較舊版本的.NET framework 建置的混合模式組件。 在這些情況下，將屬性設定為`true`。  
  
> [!NOTE]
>  將屬性設定為`true`CLR 1.1 版或 CLR 2.0 版可防止載入到相同的程序，確實停用的同處理序並存的功能 (請參閱[-並存執行 COM interop](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32))。  
  
## <a name="example"></a>範例  
 下列範例顯示如何在組態檔中指定的執行階段版本。  
  
```xml  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [啟動設定結構描述](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> 指定要使用哪一個執行階段版本](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [COM interop-並存執行](http://msdn.microsoft.com/en-us/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [同處理序並存執行](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
