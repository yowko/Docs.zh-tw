---
title: "&lt;p&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 654887c870a7f620c52fa402d6324de39fdb2feb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltpublisherpolicygt-element"></a>&lt;p&gt;項目
指定執行階段是否套用發行者原則。  
  
 \<configuration>  
\<執行階段 >  
\<assemblyBinding >  
\<y >  
\<p >  
  
## <a name="syntax"></a>語法  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`apply`|指定是否套用發行者原則。|  
  
## <a name="apply-attribute"></a>套用屬性  
  
|值|說明|  
|-----------|-----------------|  
|`yes`|套用發行者原則。 這是預設設定。|  
|`no`|不套用發行者原則。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 當元件廠商發行新版的組件時，廠商可以包含發行者原則，因此現在使用舊版本的應用程式使用新的版本。 若要指定是否要針對特定的組件套用發行者原則，請將 **\<p >**中的項目 **\<dependentAssembly >**項目。  
  
 預設設定**套用**屬性是**是**。 設定**套用**屬性**沒有**覆寫任何先前**是**組件的設定。  
  
 若要明確地略過發行者原則使用的應用程式需要的權限[ \<p 套用 ="no"/ >](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)應用程式組態檔中的項目。 藉由設定授與權<xref:System.Security.Permissions.SecurityPermissionFlag>加上旗標上<xref:System.Security.Permissions.SecurityPermission>。 如需詳細資訊，請參閱[組件繫結重新導向安全性權限](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)。  
  
## <a name="example"></a>範例  
 下列範例會關閉發行者原則組件， `myAssembly`。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
