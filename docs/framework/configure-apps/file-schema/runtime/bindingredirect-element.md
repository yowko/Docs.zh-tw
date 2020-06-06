---
title: <bindingRedirect> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154292"
---
# <a name="bindingredirect-element"></a>\<bindingRedirect> 項目
將一個組件版本重新導向至另一個版本。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bindingRedirect>**  
  
## <a name="syntax"></a>語法  
  
```xml  
   <bindingRedirect
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`oldVersion`|必要屬性。<br /><br /> 指定原本要求的組件版本。 元件版本號碼的格式為 [*主要. 次要. 組建. 修訂*]。 這個版本號碼每個部分的有效值為 0 至 65535。<br /><br /> 您也可以使用下列格式指定版本範圍：<br /><br /> *n. n-n. n. n. n*|  
|`newVersion`|必要屬性。<br /><br /> 以下列格式指定要使用的元件版本，而不是原始要求的版本： *n* . n. n. n<br /><br /> 這個值可以指定 `oldVersion` 以前的版本。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`dependentAssembly`|封裝每一個組件的繫結原則和組件位置。 針對每個組件使用一個 dependentAssembly 項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 當您對照強式名稱的組件建置 .NET Framework 應用程式時，即使有可用的新版本，應用程式仍會預設為在執行階段使用該組件版本。 不過，您可以設定應用程式以較新的組件版本執行。 如需執行時間如何使用這些檔案來判斷要使用哪個元件版本的詳細資訊，請參閱[執行時間如何找出元件](../../../deployment/how-the-runtime-locates-assemblies.md)。  
  
 您可以在 `bindingRedirect` 項目中包含多個 `dependentAssembly` 項目，藉此重新導向多個組件版本。 您也可以將組件從較新版本重新導向至較舊版本。  
  
 在應用程式組態檔中進行明確的組件繫結重新導向必須擁有安全性權限。 這適用於 .NET Framework 組件和協力廠商組件的重新導向。 許可權是藉由在上設定旗標來授與 <xref:System.Security.Permissions.SecurityPermissionFlag> <xref:System.Security.Permissions.SecurityPermission> 。 如需詳細資訊，請參閱元件系結重新導向[安全性許可權](../../assembly-binding-redirection-security-permission.md)。  
  
## <a name="example"></a>範例  
 下列範例將示範如何將某一個組件版本重新導向至另一個版本。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行時間設定架構](index.md)
- [設定檔架構](../index.md)
- [重新導向組件版本](../../redirect-assembly-versions.md)
