---
title: <PreferComInsteadOfManagedRemoting> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c79c76717acf7ff309375313b30534dd0aff9399
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920701"
---
# <a name="prefercominsteadofmanagedremoting-element"></a>\<PreferComInsteadOfManagedRemoting > 元素
指定執行時間是否會針對跨應用程式域界限的所有呼叫, 使用 COM Interop 而不是遠端處理。  
  
 \<configuration>  
\<執行時間 >  
\<PreferComInsteadOfManagedRemoting>  
  
## <a name="syntax"></a>語法  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指出執行時間是否會使用 COM Interop, 而不是跨應用程式域界限進行遠端處理。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|執行時間會跨應用程式域界限使用遠端功能。 這是預設值。|  
|`true`|執行時間會跨應用程式域界限使用 COM Interop。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 當您將`enabled`屬性設定為`true`時, 執行時間的行為會如下所示:  
  
- 當[iunknown](https://go.microsoft.com/fwlink/?LinkId=148003)介面透過 COM 介面進入網域時, 執行時間不會針對[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)介面呼叫[IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) 。 相反地, 它會在物件周圍建立執行時間可呼叫[包裝](../../../../standard/native-interop/runtime-callable-wrapper.md)函式 (RCW)。  
  
- 執行時間會在收到`QueryInterface`此網域中已建立之任何 COM 可呼叫[包裝](../../../../standard/native-interop/com-callable-wrapper.md)函式 (CCW) 的[IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md)介面呼叫時傳回 E_NOINTERFACE。  
  
 這兩種行為可確保跨應用程式域界限的 managed 物件之間的所有呼叫都是使用 COM 和 COM Interop, 而不是遠端處理。  
  
## <a name="example"></a>範例  
 下列範例顯示如何指定執行時間應該跨隔離界限使用 COM Interop:  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
