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
ms.openlocfilehash: 74e83900c68ab4b3fe01beb3f97657b0140d78ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153915"
---
# <a name="qualifyassembly-element"></a>\<限定裝配>元素
指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<程式集綁定>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<符合條件>**  
  
## <a name="syntax"></a>語法  
  
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
|`partialName`|必要屬性。<br /><br /> 指定程式集的部分名稱，因為它出現在代碼中。|  
|`fullName`|必要屬性。<br /><br /> 指定程式集的全名，因為它出現在全域組件快取中。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 使用部分<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>程式集名稱調用 方法會導致公共語言運行時僅在應用程式基目錄中查找程式集。 使用應用程式佈建檔中的**\<限定程式集>** 元素提供完整的程式集資訊（名稱、版本、公開金鑰權杖和區域性），並導致通用語言運行時在全域組件快取中搜索程式集。  
  
 **fullName**屬性必須包括程式集標識的四個欄位：名稱、版本、公開金鑰權杖和區域性。 **部分名稱**屬性必須部分引用程式集。 必須至少指定程式集的文本名稱（最常見的情況），但還可以包括版本、公開金鑰權杖或區域性（或四者中的任何組合，但不是全部四個）。 **部分名稱**必須與呼叫中指定的名稱匹配。 例如，您不能在設定檔中`"math"`指定為**部分Name**屬性，並在代碼中調用`Assembly.Load("math, Version=3.3.3.3")`。  
  
## <a name="example"></a>範例  
 以下示例從邏輯上將調用`Assembly.Load("math")`轉換為`Assembly.Load("math,version=1.0.0.0,publicKeyToken=a1690a5ea44bab32,culture=neutral")`。  
  
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
- [部分組件參考](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0a7zy9z5(v=vs.100))
