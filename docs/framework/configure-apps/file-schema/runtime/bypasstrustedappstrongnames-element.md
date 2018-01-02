---
title: "&lt;bypassTrustedAppStrongNames&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0343aef083076249325b9577f90964d066867f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a>&lt;bypassTrustedAppStrongNames&gt;項目
指定是否略過強式名稱的完全信任組件載入至完全信任的驗證<xref:System.AppDomain>。  
  
 \<configuration>  
\<執行階段 >  
\<bypassTrustedAppStrongNames >  
  
## <a name="syntax"></a>語法  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否啟用不驗證完全信任組件的強式名稱略過功能。 啟用這項功能時，強式名稱不會驗證正確載入組件時。 預設為 `true`。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`true`|載入至完全信任組件時，不會驗證完整信任組件的強式名稱簽章<xref:System.AppDomain>。 這是預設值。|  
|`false`|在完全信任組件的強式名稱簽章會驗證載入至完全信任組件時<xref:System.AppDomain>。 強式名稱簽章只會檢查簽章正確。它不會與另一個的強式名稱的相符項目。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  
 強式名稱略過功能可以避免完全信任組件的強式名稱簽章驗證的額外負荷。  
  
 略過功能適用於任何以強式名稱簽署並具有下列特性的組件：  
  
-   不完全受信任<xref:System.Security.Policy.StrongName>辨識項 (例如，具有`MyComputer`區域辨識項)。  
  
-   載入到完全信任的 <xref:System.AppDomain>。  
  
-   從 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性下的位置載入。  
  
-   不延遲簽署。  
  
> [!NOTE]
>  如果略過功能已關閉的電腦上的所有應用程式使用的登錄機碼，此組態檔設定沒有任何作用。 如需詳細資訊，請參閱[如何： 停用強式名稱略過功能](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)。  
  
## <a name="example"></a>範例  
 下列範例會示範如何指定會在完全信任組件的強式名稱簽章驗證的行為。  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [如何：停用強式名稱略過功能](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
