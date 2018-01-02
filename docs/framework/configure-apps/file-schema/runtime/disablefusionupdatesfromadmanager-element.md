---
title: "&lt;disableFusionUpdatesFromADManager&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1d3a1214b4aecf56c9a6440e31459573a5922676
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a>&lt;disableFusionUpdatesFromADManager&gt;項目
指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。  
  
 \<設定 > 項目  
\<runtime > 項目  
\<disableFusionUpdatesFromADManager >  
  
## <a name="syntax"></a>語法  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否要停用覆寫融合設定的預設功能。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|請勿停用覆寫融合設定的功能。 這是預設行為，開頭[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]。|  
|1|停用覆寫融合設定的功能。 這會還原為舊版.NET Framework 的行為。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從開始[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，預設行為是允許<xref:System.AppDomainManager>物件來覆寫使用的組態設定<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性或<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法<xref:System.AppDomainSetup>物件傳遞至您的實作<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法，在您的子類別<xref:System.AppDomainManager>。 預設應用程式定義域中，您所變更的設定覆寫應用程式組態檔所指定的設定。 其他應用程式定義域，它們會覆寫的組態設定，傳遞給<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法。  
  
 您可以傳遞新組態資訊，或傳遞 null (`Nothing`在 Visual Basic 中) 若要消除傳入的組態資訊。  
  
 不要將組態資訊傳遞給兩者<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性和<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法。 如果您同時將組態資訊，資訊您傳遞給<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性會被忽略，因為<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法會覆寫來自應用程式組態檔的組態資訊。 如果您使用<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性，您可以將傳遞 null (`Nothing`在 Visual Basic 中) 以<xref:System.AppDomainSetup.SetConfigurationBytes%2A>方法，以排除指定的呼叫中的任何組態位元組<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法。  
  
 除了設定資訊，您可以變更下列設定<xref:System.AppDomainSetup>物件傳遞至您的實作<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法： <xref:System.AppDomainSetup.ApplicationBase%2A>， <xref:System.AppDomainSetup.ApplicationName%2A>， <xref:System.AppDomainSetup.CachePath%2A>， <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>， <xref:System.AppDomainSetup.DisallowBindingRedirects%2A><xref:System.AppDomainSetup.DisallowCodeDownload%2A>， <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>， <xref:System.AppDomainSetup.DynamicBase%2A>， <xref:System.AppDomainSetup.LoaderOptimization%2A>， <xref:System.AppDomainSetup.PrivateBinPath%2A>， <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>， <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>，和<xref:System.AppDomainSetup.ShadowCopyFiles%2A>。  
  
 做為使用替代`<disableFusionUpdatesFromADManager>`項目，您可以停用的預設行為建立登錄設定，或設定環境變數。 在登錄中，建立名為的 DWORD 值`COMPLUS_disableFusionUpdatesFromADManager`下`HKCU\Software\Microsoft\.NETFramework`或`HKLM\Software\Microsoft\.NETFramework`，並將值設定為 1。 在命令列中，設定環境變數`COMPLUS_disableFusionUpdatesFromADManager`設為 1。  
  
## <a name="example"></a>範例  
 下列範例示範如何停用的功能使用覆寫融合設定`<disableFusionUpdatesFromADManager>`項目。  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
