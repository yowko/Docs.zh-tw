---
title: '&lt;relativeBindForResources&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ae5d1ca6403d84c9828dcf9550e9fbf40b28e1b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltrelativebindforresourcesgt-element"></a>&lt;relativeBindForResources&gt;項目
最佳化附屬組件的探查。  
  
 \<設定 > 項目  
\<runtime > 項目  
\<> 項目  
  
## <a name="syntax"></a>語法  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定 common language runtime 是否會探查最佳化附屬組件。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|執行階段不會最佳化附屬組件探查。 這是預設值。|  
|`true`|執行階段會探查最佳化附屬組件。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 一般而言，資源管理員來探查資源，如中所述[封裝和部署資源](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)主題。 這表示，當資源管理員來探查特定資源的當地語系化版本，可能會在全域組件快取中尋找、 尋找應用程式的程式碼基底，查詢 Windows Installer 的特定文化特性資料夾中的附屬組件，並引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。 `<relativeBindForResources>`項目最佳化資源管理員探查附屬組件的方式。 在下列情況下的資源的探查時，它可以改善效能：  
  
-   當附屬組件部署在與程式碼組件相同的位置。 換句話說，如果程式碼組件會安裝在全域組件快取，附屬組件也必須安裝那里。 如果程式碼組件會安裝在應用程式的程式碼基底，附屬組件也必須安裝的程式碼基底中的特定文化特性資料夾中。  
  
-   當 Windows 安裝程式不會使用或很少使用隨安裝的附屬組件。  
  
-   當應用程式程式碼未處理<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。  
  
 設定`enabled`屬性`<relativeBindForResources>`元素`true`資源管理員的探查最佳化附屬組件，如下所示：  
  
-   它會使用父程式碼組件位置的附屬組件探查。  
  
-   它不會查詢 Windows Installer 的附屬組件。  
  
-   它不會引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。  
  
## <a name="see-also"></a>另請參閱  
 [封裝和部署資源](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
