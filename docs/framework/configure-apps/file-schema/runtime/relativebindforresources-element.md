---
title: <relativeBindForResources> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153902"
---
# <a name="relativebindforresources-element"></a>\<相對綁定資源>元素
最佳化附屬組件的探查。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<相對綁定資源>**  
  
## <a name="syntax"></a>語法  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定通用語言運行時是否優化了附屬程式集的探測。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|運行時不優化衛星元件的探測。 這是預設值。|  
|`true`|運行時優化了衛星元件的探測。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 通常，資源管理器會調查資源，如["打包和部署資源](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)"主題中所述。 這意味著，當資源管理器探測資源的特定當地語系化版本時，它可能會查看全域組件快取、在應用程式代碼庫中查看特定于區域性的資料夾、查詢 Windows 安裝程式以查找附屬程式集以及引發<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>事件。 該`<relativeBindForResources>`元素優化了資源管理器探測附屬程式集的方式。 在以下條件下探測資源時，它可以提高性能：  
  
- 當附屬程式集部署在同一位置的代碼程式集時。 換句話說，如果代碼程式集安裝在全域組件快取中，則還必須在那裡安裝附屬程式集。 如果代碼程式集安裝在應用程式的代碼庫中，則附屬程式集也必須安裝在代碼庫中特定于區域性的資料夾中。  
  
- 當不使用 Windows 安裝程式或很少用於按需安裝附屬程式集時。  
  
- 當應用程式代碼不處理事件<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>時。  
  
 設置`enabled``<relativeBindForResources>`元素的屬性以`true`優化資源管理器對附屬程式集的探測，如下所示：  
  
- 它使用父代碼程式集的位置來探測附屬程式集。  
  
- 它不查詢 Windows 安裝程式的附屬程式集。  
  
- 它不引發事件<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>另請參閱

- [封裝和部署資源](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
