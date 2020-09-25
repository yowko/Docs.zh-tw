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
ms.openlocfilehash: c9e608bfd54b641564a9095076455e10dd8653fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91176119"
---
# <a name="disablecachingbindingfailures-element"></a>\<disableCachingBindingFailures> 項目

指定是否要停用因為探查找不到元件而發生之系結失敗的快取。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCachingBindingFailures>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|已啟用|必要屬性。<br /><br /> 指定是否要停用因為探查找不到元件而發生之系結失敗的快取。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|0|請勿停用發生系結失敗的快取，因為探查找不到元件。 這是從 .NET Framework 版本2.0 開始的預設系結行為。|  
|1|停用發生系結失敗的快取，因為探查找不到元件。 這項設定會還原為 .NET Framework 版本1.1 的系結行為。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  

 從 .NET Framework 版本2.0 開始，載入元件的預設行為是快取所有的系結和載入失敗。 也就是說，如果嘗試載入元件失敗，後續載入相同元件的要求都會立即失敗，而不會嘗試找出元件。 這個元素會停用發生系結失敗的預設行為，因為在探查路徑中找不到元件。 這些失敗都會擲回 <xref:System.IO.FileNotFoundException> 。  
  
 某些系結和載入失敗不受此元素影響，且一律會進行快取。 因為找到元件，但無法載入，所以會發生這些失敗。 它們會擲回 <xref:System.BadImageFormatException> 或 <xref:System.IO.FileLoadException> 。 下列清單包含這類失敗的一些範例。  
  
- 如果您嘗試載入的檔案不是有效的元件，則即使錯誤的檔案被正確的元件所取代，後續載入元件的嘗試也會失敗。  
  
- 如果您嘗試載入檔案系統所鎖定的元件，則即使檔案系統發行元件之後，後續載入元件的嘗試也會失敗。  
  
- 如果您嘗試載入的一或多個元件版本是在探查路徑中，但是您要求的特定版本不在其中，則即使將正確的版本移到探查路徑中，後續載入該版本的嘗試也會失敗。  
  
## <a name="example"></a>範例  

 下列範例示範如何停用因為探查找不到元件而發生的元件系結失敗的快取。  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
- [執行階段如何找出組件](../../../deployment/how-the-runtime-locates-assemblies.md)
