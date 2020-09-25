---
title: <qualifyAssembly> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#qualifyAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/qualifyAssembly
helpviewer_keywords:
- container tags, <qualifyAssembly> element
- <qualifyAssembly> element
- qualifyAssembly element
ms.assetid: ad6442f6-1a9d-43b6-b733-04ac1b7f9b82
ms.openlocfilehash: 26b265996a059d8e52901557603bcf5e7636e596
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195216"
---
# <a name="qualifyassembly-element"></a>\<qualifyAssembly> 項目

指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<qualifyAssembly>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`partialName`|必要屬性。<br /><br /> 指定元件在程式碼中顯示的部分名稱。|  
|`fullName`|必要屬性。<br /><br /> 指定元件在全域組件快取中所顯示的完整名稱。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  

 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>使用部分元件名稱呼叫方法會導致 common language runtime 只在應用程式基底目錄中尋找元件。 **\<qualifyAssembly>** 您可以使用應用程式佈建檔中的專案，提供完整的元件資訊 (名稱、版本、公開金鑰 token 和文化特性) ，並導致 common language runtime 搜尋全域組件快取中的元件。  
  
 **FullName**屬性必須包含元件身分識別的四個欄位：名稱、版本、公開金鑰 token 和文化特性。 **PartialName**屬性必須部分參考元件。 您必須至少指定元件的文字名稱 (最常見的案例) ，但您也可以包含版本、公開金鑰 token 或文化特性 (或四個的任意組合，而不是全部四個) 。 **PartialName**必須符合您在呼叫中指定的名稱。 例如，您不能在 `"math"` 設定檔中指定作為 **partialName** 屬性，然後 `Assembly.Load("math, Version=3.3.3.3")` 在程式碼中呼叫。  
  
## <a name="example"></a>範例  

 下列範例會以邏輯方式開啟的呼叫 `Assembly.Load("math")` `Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")` 。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <qualifyAssembly partialName="math"
                         fullName=  
"math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [執行階段如何找出組件](../../../deployment/how-the-runtime-locates-assemblies.md)
- [部分組件參考](/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
