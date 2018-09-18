---
title: '&lt;PreferComInsteadOfManagedRemoting&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c05e27226a58086c806e8977ba50a55873d1167e
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46002069"
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a>&lt;PreferComInsteadOfManagedRemoting&gt;項目
指定是否執行階段會使用 COM interop 而不是遠端處理的所有呼叫跨越應用程式定義域界限。  
  
 \<configuration>  
\<執行階段 >  
\<PreferComInsteadOfManagedRemoting >  
  
## <a name="syntax"></a>語法  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指出是否執行階段會使用 COM interop 而不是遠端處理跨應用程式定義域界限。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|執行階段會使用遠端處理跨應用程式定義域界限。 這是預設值。|  
|`true`|執行階段會跨應用程式定義域界限使用 COM interop。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 當您設定`enabled`屬性設定為`true`，執行階段行為，如下所示：  
  
-   執行階段不會呼叫[iunknown:: Queryinterface](https://go.microsoft.com/fwlink/?LinkID=144867) for [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)介面[IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003)介面進入網域透過 COM 介面。 相反地，它會建構[執行階段可呼叫包裝函式](../../../../../docs/framework/interop/runtime-callable-wrapper.md)(RCW) 物件周圍。  
  
-   執行階段會接收時，會傳回 E_NOINTERFACE`QueryInterface`呼叫[IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)介面的任何[COM 可呼叫包裝函式](../../../../../docs/framework/interop/com-callable-wrapper.md)(CCW)，已建立在這個網域中。  
  
 這些兩種行為可確保所有呼叫 com 都介面之間受管理的物件，在應用程式定義域界限使用 COM 和 COM interop，而不是遠端執行功能。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定執行階段應該使用 COM interop 跨越隔離界限：  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
