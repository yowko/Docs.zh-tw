---
title: <developmentMode> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117624"
---
# <a name="developmentmode-element"></a>\<developmentMode > 元素
指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<developmentMode >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**developerInstallation**|指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。|  
  
## <a name="developerinstallation-attribute"></a>developerInstallation 屬性  
  
|值|描述|  
|-----------|-----------------|  
|**true**|在 DEVPATH 環境變數所指定的目錄中搜尋元件。|  
|**false**|不會在 DEVPATH 環境變數所指定的目錄中搜尋元件。 這是預設值|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 請只在開發階段使用此設定。 執行時間不會檢查在 DEVPATH 中找到的強式名稱元件上的版本。 它只會使用所找到的第一個元件。  
  
## <a name="example"></a>範例  
 下列範例顯示如何讓執行時間在 DEVPATH 環境變數所指定的目錄中搜尋元件。  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [如何：使用 DEVPATH 找出組件](../../how-to-locate-assemblies-by-using-devpath.md)
