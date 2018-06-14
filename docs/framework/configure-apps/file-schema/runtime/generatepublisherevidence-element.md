---
title: '&lt;generatePublisherEvidence&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f56bbef6ed6decf6be4246f649665db4cf0f766
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746016"
---
# <a name="ltgeneratepublisherevidencegt-element"></a>&lt;generatePublisherEvidence&gt;項目
指定執行階段是否會建立<xref:System.Security.Policy.Publisher>用於程式碼存取安全性 (CAS) 的辨識項。  
  
 \<configuration>  
\<執行階段 >  
\<generatePublisherEvidence >  
  
## <a name="syntax"></a>語法  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否會建立<xref:System.Security.Policy.Publisher>辨識項。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會建立<xref:System.Security.Policy.Publisher>辨識項。|  
|`true`|建立<xref:System.Security.Policy.Publisher>辨識項。 這是預設值。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  在[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本中，這個項目具有組件載入時間不會影響。 如需詳細資訊，請參閱中的 「 安全性原則簡化 」 一節[安全性變更](../../../../../docs/framework/security/security-changes.md)。  
  
 Common language runtime (CLR) 會嘗試驗證 Authenticode 簽章在載入時間，以建立<xref:System.Security.Policy.Publisher>組件的辨識項。 不過，根據預設，大部分的應用程式不需要<xref:System.Security.Policy.Publisher>辨識項。 標準的 CAS 原則不會依賴<xref:System.Security.Policy.PublisherMembershipCondition>。 您應該避免與驗證的簽章，除非應用程式具有自訂的 CAS 原則的電腦上執行，或想要滿足需求的相關聯的不必要的啟動成本<xref:System.Security.Permissions.PublisherIdentityPermission>在部分信任環境中。 （一律要求的識別權限成功在完全信任環境中）。  
  
> [!NOTE]
>  我們建議，服務會使用`<generatePublisherEvidence>`項目，以改善啟動效能。  使用這個項目，也有助於避免逾時和服務啟動後取消可能會造成的延遲。  
  
## <a name="configuration-file"></a>組態檔  
 此項目只能用於應用程式組態檔中。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`<generatePublisherEvidence>`停用檢查 CA 發行者原則中的應用程式的項目。  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
