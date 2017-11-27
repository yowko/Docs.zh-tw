---
title: "&lt;程式碼基底&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5b30f1dc3ccade3028c31c57ffdab521802f086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcodebasegt-element"></a>&lt;程式碼基底&gt;項目
指定 common language runtime 可以找到組件的位置。  
  
 \<configuration>  
\<執行階段 >  
\<assemblyBinding >  
\<y >  
\<程式碼基底 >  
  
## <a name="syntax"></a>語法  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`href`|必要屬性。<br /><br /> 指定執行階段可以找到指定的版本的組件的 URL。|  
|`version`|必要屬性。<br /><br /> 指定程式碼基底套用至組件的版本。 組件版本號碼的格式是*major.minor.build.revision*。|  
  
## <a name="version-attribute"></a>版本屬性  
  
|值|描述|  
|-----------|-----------------|  
|每個部分的版本號碼的有效值為 0 到 65535 之間。|不適用。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`buildproviders`|定義用來編譯自訂資源檔的組建提供者集合。 組建提供者的數量不限。|  
|`compilation`|設定 ASP.NET 使用的所有編譯設定。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`System.web`|指定 ASP.NET 組態區段的根項目。|  
  
## <a name="remarks"></a>備註  
 為了讓執行階段使用**\<程式碼基底 >**設定在電腦組態檔或發行者原則檔中，檔案也必須重新導向組件版本。 應用程式組態檔可能不需要重新導向組件版本的程式碼基底設定。 決定之後要使用的組件版本，執行階段適用於決定版本的檔案中的程式碼基底設定。 如果指示沒有程式碼基底，執行階段會以一般方式探查組件。  
  
 如果組件具有強式名稱，程式碼基底設定可以位於任何位置近端內部網路或網際網路。 如果組件私用組件，程式碼基底設定必須是相對於應用程式的目錄路徑。  
  
 對於沒有強式名稱組件，版本會被忽略，則載入器會使用第一個出現的\<程式碼基底 > 內\<y >。 如果將繫結重新導向至另一個組件的應用程式組態檔中沒有項目，重新導向將會優先，即使組件版本不符合繫結要求。  
  
## <a name="example"></a>範例  
 下列範例會示範如何指定執行階段可以找到組件的位置。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [指定組件的位置](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
