---
title: <disableFusionUpdatesFromADManager> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1923e70143ea2a158447eccdb35d347fe4f51ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663775"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager > 元素
指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。  
  
 \<configuration > 元素  
\<執行時間 > 元素  
\<disableFusionUpdatesFromADManager>  
  
## <a name="syntax"></a>語法  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否停用覆寫融合設定的預設功能。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|請勿停用覆寫融合設定的功能。 這是預設行為, 從 .NET Framework 4 開始。|  
|1|停用覆寫融合設定的功能。 這會還原成舊版 .NET Framework 的行為。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從 .NET Framework 4 開始, 預設行為是<xref:System.AppDomainManager>允許物件<xref:System.AppDomainSetup.ConfigurationFile%2A>使用屬性或<xref:System.AppDomainSetup.SetConfigurationBytes%2A>傳遞至您的<xref:System.AppDomainSetup>實作為物件的方法來覆寫設定在的子<xref:System.AppDomainManager>類別中的方法。<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 針對預設應用程式域, 您所變更的設定會覆寫應用程式佈建檔所指定的設定。 若是其他應用程式域, 則會覆寫傳遞至<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法的設定。  
  
 您可以傳遞新的設定資訊, 或傳遞 null (`Nothing`在 Visual Basic 中), 以排除傳入的設定資訊。  
  
 請勿將設定資訊同時<xref:System.AppDomainSetup.ConfigurationFile%2A>傳遞給屬性<xref:System.AppDomainSetup.SetConfigurationBytes%2A>和方法。 如果您將設定資訊傳遞至兩者, 則會忽略傳遞給<xref:System.AppDomainSetup.ConfigurationFile%2A>屬性的資訊, <xref:System.AppDomainSetup.SetConfigurationBytes%2A>因為方法會覆寫應用程式佈建檔中的設定資訊。 如果<xref:System.AppDomainSetup.ConfigurationFile%2A>您使用屬性, 您可以將 null ( <xref:System.AppDomainSetup.SetConfigurationBytes%2A> `Nothing`在 Visual Basic 中) 傳遞至方法, 以排除呼叫<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>或<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>方法時所指定的任何設定位元組。  
  
 除了設定資訊之外, 您還<xref:System.AppDomainSetup>可以在傳遞給<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法之執行的物件上變更下列設定: <xref:System.AppDomainSetup.ApplicationBase%2A>、 <xref:System.AppDomainSetup.ApplicationName%2A>、 <xref:System.AppDomainSetup.CachePath%2A>、、 <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>、 <xref:System.AppDomainSetup.DisallowCodeDownload%2A>、 <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> 、<xref:System.AppDomainSetup.DynamicBase%2A>、 、<xref:System.AppDomainSetup.PrivateBinPath%2A>、、和<xref:System.AppDomainSetup.ShadowCopyFiles%2A>。 <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>  
  
 除了使用`<disableFusionUpdatesFromADManager>`專案以外, 您還可以藉由建立登錄設定或設定環境變數, 來停用預設行為。 在登錄中, 建立名為`COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework`或`HKLM\Software\Microsoft\.NETFramework`的 DWORD 值, 並將值設定為1。 在命令列中, 將環境變數`COMPLUS_disableFusionUpdatesFromADManager`設定為1。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用專案停用`<disableFusionUpdatesFromADManager>`覆寫融合設定的功能。  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [執行階段如何找出組件](../../../deployment/how-the-runtime-locates-assemblies.md)
