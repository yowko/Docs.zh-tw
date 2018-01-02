---
title: "&lt;PreferComInsteadOfManagedRemoting&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ad60d73e30bf02fd52f9c8f3bd707b571959bdd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a>&lt;PreferComInsteadOfManagedRemoting&gt;項目
指定是否執行階段會使用 COM interop 而不是遠端執行功能的所有呼叫跨越應用程式定義域界限。  
  
 \<configuration>  
\<執行階段 >  
\<PreferComInsteadOfManagedRemoting >  
  
## <a name="syntax"></a>語法  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
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
 當您將`enabled`屬性`true`，執行階段行為，如下所示：  
  
-   執行階段不會呼叫[iunknown:: Queryinterface](http://go.microsoft.com/fwlink/?LinkID=144867)如[IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)介面[IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003)介面進入透過 COM 介面的網域。 相反地，它是由建構[執行階段可呼叫包裝函式](../../../../../docs/framework/interop/runtime-callable-wrapper.md)(RCW) 的物件周圍。  
  
-   執行階段收到時，它會傳回 E_NOINTERFACE`QueryInterface`呼叫[IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)任何介面[COM 可呼叫包裝函式](../../../../../docs/framework/interop/com-callable-wrapper.md)(CCW)，已在這個網域中建立。  
  
 這些兩種行為可確保所有的呼叫，透過 COM 介面之間受管理的物件，跨應用程式定義域界限使用 COM 和 COM interop，而不是遠端執行功能。  
  
## <a name="example"></a>範例  
 下列範例示範如何指定執行階段應該使用 COM interop 跨隔離界限：  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
