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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4aa90a378630c9aff74923d8e8600aed15a77a5e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663494"
---
# <a name="qualifyassembly-element"></a>\<qualifyAssembly > 元素
指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。  
  
 \<configuration>  
\<執行時間 >  
\<assemblyBinding>  
\<qualifyAssembly>  
  
## <a name="syntax"></a>語法  
  
```xml  
      <qualifyAssembly partialName=  
      "PartialAssemblyName"  
                 fullName="FullAssemblyName"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`partialName`|必要屬性。<br /><br /> 指定元件出現在程式碼中的部分名稱。|  
|`fullName`|必要屬性。<br /><br /> 指定元件出現在全域組件快取中的完整名稱。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 使用部分元件名稱呼叫方法,會導致commonlanguageruntime只在應用程式基底目錄中尋找元件。<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 使用應用程式佈建檔中的 **\<qualifyAssembly >** 專案, 提供完整的元件資訊 (名稱、版本、公開金鑰標記和文化特性), 並導致 common language runtime 在中搜尋元件。全域組件快取。  
  
 **FullName**屬性必須包含元件識別的四個欄位: 名稱、版本、公開金鑰標記和文化特性。 **PartialName**屬性必須部分參考元件。 您至少必須指定元件的文字名稱 (最常見的情況), 但您也可以包含版本、公開金鑰標記或文化特性 (或四個 (但不是全部四個) 的任何組合。 **PartialName**必須符合您的呼叫中所指定的名稱。 例如, 您無法在配置`"math"`檔中指定做為**partialName**屬性, 並在`Assembly.Load("math, Version=3.3.3.3")`您的程式碼中呼叫。  
  
## <a name="example"></a>範例  
 下列範例會以邏輯方式將`Assembly.Load("math")`呼叫`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`變成。  
  
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
- [部分元件參考](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
