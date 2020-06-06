---
title: <disableFusionUpdatesFromADManager> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117449"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager> 項目
指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|已啟用|必要屬性。<br /><br /> 指定是否停用覆寫融合設定的預設功能。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|請勿停用覆寫融合設定的功能。 這是預設行為，從 .NET Framework 4 開始。|  
|1|停用覆寫融合設定的功能。 這會還原成舊版 .NET Framework 的行為。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從 .NET Framework 4 開始，預設行為是允許 <xref:System.AppDomainManager> 物件 <xref:System.AppDomainSetup.ConfigurationFile%2A> <xref:System.AppDomainSetup.SetConfigurationBytes%2A> <xref:System.AppDomainSetup> <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 在的子類別中，使用傳遞給方法的屬性或物件的方法來覆寫設定設定 <xref:System.AppDomainManager> 。 針對預設應用程式域，您所變更的設定會覆寫應用程式佈建檔所指定的設定。 若是其他應用程式域，則會覆寫傳遞至 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> 或方法的設定 <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 。  
  
 您可以傳遞新的設定資訊，或傳遞 null （ `Nothing` 在 Visual Basic 中），以排除傳入的設定資訊。  
  
 請勿將設定資訊同時傳遞給 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性和 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法。 如果您將設定資訊傳遞至兩者，則會忽略傳遞給 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性的資訊，因為 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法會覆寫應用程式佈建檔中的設定資訊。 如果您使用 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性，您可以將 null （ `Nothing` 在 Visual Basic 中）傳遞至 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法，以排除呼叫或方法時所指定的任何設定位元組 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 。  
  
 除了設定資訊之外，您還可以在 <xref:System.AppDomainSetup> 傳遞給方法之執行的物件上變更下列設定 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> ： <xref:System.AppDomainSetup.ApplicationBase%2A> 、 <xref:System.AppDomainSetup.ApplicationName%2A> 、 <xref:System.AppDomainSetup.CachePath%2A> 、 <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> 、 <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> 、 <xref:System.AppDomainSetup.DisallowCodeDownload%2A> 、 <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> <xref:System.AppDomainSetup.ShadowCopyFiles%2A> 、、、、、和。  
  
 除了使用專案以外 `<disableFusionUpdatesFromADManager>` ，您還可以藉由建立登錄設定或設定環境變數，來停用預設行為。 在登錄中，建立名為或的 DWORD 值， `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` `HKLM\Software\Microsoft\.NETFramework` 並將值設定為1。 在命令列中，將環境變數設定 `COMPLUS_disableFusionUpdatesFromADManager` 為1。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用專案停用覆寫融合設定的功能 `<disableFusionUpdatesFromADManager>` 。  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行時間設定架構](index.md)
- [設定檔架構](../index.md)
- [執行階段如何找出組件](../../../deployment/how-the-runtime-locates-assemblies.md)
