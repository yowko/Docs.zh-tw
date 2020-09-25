---
title: <publisherPolicy> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
ms.openlocfilehash: bd6ab1123ef3f84f7e8a06b25ce48aed37e4bef7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195255"
---
# <a name="publisherpolicy-element"></a>\<publisherPolicy> 項目

指定執行階段是否套用發行者原則。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<publisherPolicy>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`apply`|指定是否要套用發行者原則。|  
  
## <a name="apply-attribute"></a>apply 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`yes`|套用發行者原則。 這是預設值。|  
|`no`|不會套用發行者原則。|  
  
### <a name="child-elements"></a>子元素  

無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`dependentAssembly`|封裝每一個組件的繫結原則和組件位置。 `<dependentAssembly>`針對每個元件使用一個元素。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  

 當元件廠商發行新版本的元件時，廠商可以包含發行者原則，因此使用舊版本的應用程式現在會使用新的版本。 若要指定是否要將發行者原則套用至特定元件，請將專案放 **\<publisherPolicy>** 在 **\<dependentAssembly>** 元素中。  
  
 **Apply**屬性的預設值為 **[是]**。 **將 [套用**] 屬性設定為 [**否**] 會覆寫元件的任何先前的 **[是]** 設定。  
  
 應用程式需要許可權，才能使用 [\<publisherPolicy apply="no"/>](publisherpolicy-element.md) 應用程式佈建檔中的元素明確地忽略發行者原則。 藉由在上設定旗標來授與許可權 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。 如需詳細資訊，請參閱元件系結重新導向 [安全性許可權](../../assembly-binding-redirection-security-permission.md)。  
  
## <a name="example"></a>範例  

 下列範例會關閉元件的發行者原則 `myAssembly` 。  
  
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

- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
- [執行階段如何找出組件](../../../deployment/how-the-runtime-locates-assemblies.md)
- [重新導向組件版本](../../redirect-assembly-versions.md)
