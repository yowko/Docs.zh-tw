---
title: <disableCachingBindingFailures> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c2ed46e1d26d829fbe832e44efb40844ae7d56f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592717"
---
# <a name="disablecachingbindingfailures-element"></a>\<disableCachingBindingFailures > 項目
指定是否要停用的繫結失敗發生因為藉由探查來找不到組件快取。  
  
 \<組態 > 項目  
\<執行階段 > 項目  
\<disableCachingBindingFailures>  
  
## <a name="syntax"></a>語法  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否要停用的繫結失敗發生因為藉由探查來找不到組件快取。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|請勿停用的繫結失敗發生因為藉由探查來找不到組件快取。 這是從.NET Framework 2.0 版開始的預設繫結行為。|  
|1|停用的繫結失敗發生因為藉由探查來找不到組件快取。 此設定會還原為.NET Framework 1.1 版的繫結行為。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從.NET Framework 2.0 版開始，載入組件的預設行為是快取所有的繫結和載入失敗。 也就是嘗試載入組件時，載入相同組件的後續要求會立即失敗，而不需要任何嘗試找出組件。 這個項目會停用繫結失敗發生因為探查路徑中找不到組件的預設行為。 這些失敗擲回<xref:System.IO.FileNotFoundException>。  
  
 繫結的某些載入失敗不會受到這個項目，並一律會快取。 找不到組件，但無法載入，就會發生這些失敗。 則會擲回<xref:System.BadImageFormatException>或<xref:System.IO.FileLoadException>。 下列清單包含這類失敗的一些範例。  
  
- 如果您嘗試載入的檔案不是有效的組件，即使不正確的檔案隨即取代成正確的組件，載入組件的後續嘗試將會失敗。  
  
- 如果您嘗試載入組件鎖定的檔案系統，後續的嘗試載入組件將會失敗，即使檔案系統所發行的組件。  
  
- 如果您嘗試載入的組件的一或多個版本是在探查路徑中，但您所要求的特定版本不是在它們之間，後續嘗試載入該版本將會失敗，即使正確的版本會移到探查路徑。  
  
## <a name="example"></a>範例  
 下列範例示範如何停用快取發生因為藉由探查來找不到組件的組件繫結失敗。  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
