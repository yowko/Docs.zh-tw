---
title: <codeBase> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: 475b7df55ed509157c1da0aeb8f979de238c72b5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971879"
---
# <a name="codebase-element"></a>\<程式碼基底 > 元素

指定通用語言執行時間可以找到元件的位置。

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<codeBase>**

## <a name="syntax"></a>語法

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`href`|必要屬性。<br /><br /> 指定執行時間可以找到元件之指定版本的 URL。|
|`version`|必要屬性。<br /><br /> 指定程式碼基底適用的元件版本。 元件版本號碼的格式為 [*主要. 次要. 組建. 修訂*]。|

## <a name="version-attribute"></a>version 屬性

|值|說明|
|-----------|-----------------|
|版本號碼的每個部分的有效值為0到65535。|不適用。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`buildproviders`|定義用來編譯自訂資源檔的組建提供者集合。 組建提供者的數量不限。|
|`compilation`|設定 ASP.NET 使用的所有編譯設定。|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`System.web`|指定 ASP.NET 組態區段的根項目。|

## <a name="remarks"></a>備註

若要使用執行階段 **\<程式碼基底>**  設定在電腦組態檔或發行者原則檔中，檔案也必須重新導向組件版本。 應用程式佈建檔可以有 codebase 設定，而不需要重新導向元件版本。 決定要使用哪個元件版本之後，執行時間會從判斷版本的檔案套用程式碼基底設定。 如果未指出程式碼基底，則執行時間會以一般方式探查元件。

如果元件具有強式名稱，則程式碼基底設定可以是近端內部網路或網際網路上的任何位置。 如果元件是私用元件，則程式碼基底設定必須是相對於應用程式目錄的路徑。

針對沒有強式名稱的元件，會忽略 version，而載入器會在 dependentAssembly > \<內\<使用程式碼基底的第一個外觀 >。 如果應用程式佈建檔中有一個專案會將系結重新導向至另一個元件，則即使元件版本不符合系結要求，重新導向也會優先。

## <a name="example"></a>範例

下列範例顯示如何指定執行時間可以找到元件的位置。

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

- [執行時間設定架構](index.md)
- [組態檔結構描述](../index.md)
- [指定元件的位置](../../../../standard/assembly/location.md)
- [執行階段如何找出組件](../../../deployment/how-the-runtime-locates-assemblies.md)
