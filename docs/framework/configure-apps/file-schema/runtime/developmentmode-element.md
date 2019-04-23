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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdf840035150f08c894c984213af9a0abe6e95af
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59192051"
---
# <a name="developmentmode-element"></a>\<developmentMode > 項目
指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。  
  
 \<configuration>  
\<執行階段 >  
\<developmentMode>  
  
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
|**true**|DEVPATH 環境變數所指定的目錄中的組件的搜尋。|  
|**false**|不會搜尋 DEVPATH 環境變數所指定的目錄中的組件。 這是預設值|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 使用此設定只在開發階段。 執行階段不會檢查在 DEVPATH 中找到的強式名稱組件的版本。 它會直接使用第一個找到的組件。  
  
## <a name="example"></a>範例  
 下列範例示範如何讓執行階段搜尋 DEVPATH 環境變數所指定的目錄中的組件。  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [如何：使用 DEVPATH 找出組件](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
