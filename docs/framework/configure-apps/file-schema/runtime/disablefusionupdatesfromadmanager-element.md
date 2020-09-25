---
title: <disableFusionUpdatesFromADManager> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: c3971379b358ae16fc463df2b8d6288cf8881391
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91205031"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager> 項目

指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a>Syntax  
  
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
|1|停用覆寫融合設定的功能。 這會還原為舊版 .NET Framework 的行為。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  

 從 .NET Framework 4 開始，預設行為是允許 <xref:System.AppDomainManager> 物件覆寫設定，方法是使用 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性或 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 物件的方法，該 <xref:System.AppDomainSetup> 物件會傳遞至您的子 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 類別中的方法執行 <xref:System.AppDomainManager> 。 針對預設的應用程式域，您所變更的設定會覆寫應用程式佈建檔所指定的設定。 針對其他應用程式域，它們會覆寫傳遞給 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> 或方法的設定 <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 。  
  
 您可以傳遞新的設定資訊，或 `Nothing` 在 Visual Basic) 中傳遞 null (，以消除傳入的設定資訊。  
  
 請勿將設定資訊傳遞給 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性和 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法。 如果您將設定資訊傳遞至兩者，則會忽略您傳遞給屬性的資訊 <xref:System.AppDomainSetup.ConfigurationFile%2A> ，因為 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法會覆寫應用程式佈建檔中的設定資訊。 如果您使用 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性，則可以將 Visual Basic) 中的 null (傳遞 `Nothing` 給 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法，以排除呼叫或方法時所指定的任何設定位元組 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> 。  
  
 除了設定資訊之外，您還可以變更 <xref:System.AppDomainSetup> 傳遞給方法之實值的物件上的下列設定 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> ：、、、、、、、、、、、 <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 和 <xref:System.AppDomainSetup.ShadowCopyFiles%2A> 。  
  
 除了使用專案以外 `<disableFusionUpdatesFromADManager>` ，您也可以藉由建立登錄設定或設定環境變數來停用預設行為。 在登錄中，建立名為或的 DWORD 值， `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` `HKLM\Software\Microsoft\.NETFramework` 並將值設定為1。 在命令列中，將環境變數設定 `COMPLUS_disableFusionUpdatesFromADManager` 為1。  
  
## <a name="example"></a>範例  

 下列範例示範如何使用元素停用覆寫融合設定的功能 `<disableFusionUpdatesFromADManager>` 。  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
- [執行階段如何找出組件](../../../deployment/how-the-runtime-locates-assemblies.md)
