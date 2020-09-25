---
title: <relativeBindForResources> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: daf576488e38bed28c7c0e5222bc053659372ff0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183997"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources> 項目

最佳化附屬組件的探查。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a>Syntax  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定 common language runtime 是否優化附屬元件的探查。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|執行時間不會優化附屬元件的探查。 這是預設值。|  
|`true`|執行時間會優化附屬元件的探查。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  

 一般來說，Resource Manager 探查資源，如 [封裝和部署資源](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) 主題中所述。 這表示當 Resource Manager 探查某個特定當地語系化版本的資源時，它可能會查看全域組件快取、在應用程式的程式碼基底中尋找文化特性特定的資料夾、針對附屬元件查詢 Windows Installer，然後引發 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件。 `<relativeBindForResources>`元素會將 Resource Manager 探查附屬元件的方式優化。 當您在下列情況下探查資源時，它可以改善效能：  
  
- 當附屬元件部署在與程式碼元件相同的位置時。 換句話說，如果程式碼元件安裝在全域組件快取中，則也必須在此安裝附屬元件。 如果程式碼元件安裝在應用程式的程式碼基底中，則附屬元件也必須安裝在程式碼基底的文化特性特定資料夾中。  
  
- 當 Windows Installer 未使用時，或只用于隨選安裝附屬元件。  
  
- 當應用程式程式碼未處理 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件時。  
  
 設定 `enabled` 元素的屬性 `<relativeBindForResources>` 以 `true` 優化 Resource Manager 的附屬元件探查，如下所示：  
  
- 它會使用父程式碼元件的位置來探查附屬元件。  
  
- 它不會查詢附屬元件的 Windows Installer。  
  
- 它不會引發 <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> 事件。  
  
## <a name="see-also"></a>另請參閱

- [封裝和部署資源](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
