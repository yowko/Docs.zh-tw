---
title: <relativeBindForResources> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15156eaf883fc9ec162e0a85525564d49522b01d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592662"
---
# <a name="relativebindforresources-element"></a>\<Relativebindforresources> > 項目
最佳化附屬組件的探查。  
  
 \<組態 > 項目  
\<執行階段 > 項目  
\<Relativebindforresources> > 項目  
  
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
|`enabled`|必要屬性。<br /><br /> 指定 common language runtime 是否最佳化附屬組件的探查。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|執行階段不會最佳化附屬組件的探查。 這是預設值。|  
|`true`|執行階段最佳化附屬組件的探查。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 一般情況下，Resource Manager 來探查資源，如中所述[封裝和部署資源](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)主題。 這表示當資源管理員會探查特定資源的當地語系化版本，它可能在全域組件快取中尋找、 附屬組件，尋找應用程式的程式碼基底，查詢 Windows 安裝程式中的特定文化特性資料夾中，會引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。 `<relativeBindForResources>`項目最佳化資源管理員探查附屬組件的方式。 當探查資源在下列情況下，它可以改善效能：  
  
- 當附屬組件會部署在與程式碼組件相同的位置。 換句話說，如果程式碼組件會安裝在全域組件快取，附屬組件也必須安裝那里。 如果程式碼組件會安裝在應用程式的程式碼基底，也必須安裝附屬組件中的程式碼基底中的特定文化特性資料夾。  
  
- 當 Windows 安裝程式未使用或很少使用依需求安裝附屬組件。  
  
- 應用程式程式碼未處理的當<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。  
  
 設定`enabled`的屬性`<relativeBindForResources>`項目`true`Resource Manager 的探查最佳化附屬組件，如下所示：  
  
- 它會使用父程式碼組件的位置來探查附屬組件。  
  
- 它不會查詢 Windows Installer 附屬組件。  
  
- 它不會引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。  
  
## <a name="see-also"></a>另請參閱

- [封裝和部署資源](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
