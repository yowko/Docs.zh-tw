---
title: "&lt;disableCachingBindingFailures&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd86bc2f58bc216f741c32a51925d3f4f8ef47df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a>&lt;disableCachingBindingFailures&gt;項目
指定是否要停用的繫結失敗發生因為由探查找不到組件快取。  
  
 \<設定 > 項目  
\<runtime > 項目  
\<disableCachingBindingFailures >  
  
## <a name="syntax"></a>語法  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|必要屬性。<br /><br /> 指定是否要停用的繫結失敗發生因為由探查找不到組件快取。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|請勿停用的繫結失敗發生因為由探查找不到組件快取。 這是從.NET Framework 2.0 版的預設繫結行為。|  
|1|停用的繫結失敗發生因為由探查找不到組件快取。 這項設定會還原為.NET Framework 1.1 版的繫結行為。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 從.NET Framework 2.0 版開始，載入組件的預設行為是快取所有的繫結和載入失敗。 也就是說，如果嘗試載入組件失敗，後續要求載入相同組件會立即失敗，而不再嘗試找出組件。 這個項目會停用繫結失敗發生因為探查路徑中找不到組件的預設的行為。 這些失敗擲回<xref:System.IO.FileNotFoundException>。  
  
 繫結的某些並載入失敗不會影響這個項目，並一律會快取。 找不到組件，但無法載入，就會發生這些失敗。 它們會擲回<xref:System.BadImageFormatException>或<xref:System.IO.FileLoadException>。 下列清單包含這類失敗的一些範例。  
  
-   如果您嘗試載入檔案不是有效的組件，載入組件的後續嘗試將會失敗，即使不正確的檔案取代正確的組件。  
  
-   如果您嘗試載入組件是由檔案系統鎖定時，後續嘗試載入組件將會失敗，即使組件由檔案系統發行。  
  
-   如果您嘗試載入的組件的一個或多個版本之探查路徑中，但是它們之間不是您所要求的特定版本，後續嘗試載入該版本將會失敗，即使正確版本會移至之探查路徑中。  
  
## <a name="example"></a>範例  
 下列範例會示範如何停用組件繫結失敗發生因為由探查找不到組件快取。  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
