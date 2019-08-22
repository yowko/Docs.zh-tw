---
title: <generatePublisherEvidence> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caec297f8d0f6febad5cf46adb0a2658960c6bb1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663664"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence > 元素
指定執行時間是否為<xref:System.Security.Policy.Publisher>代碼啟用安全性 (CAS) 建立辨識項。  
  
 \<configuration>  
\<執行時間 >  
\<generatePublisherEvidence>  
  
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
|`enabled`|必要屬性。<br /><br /> 指定執行時間是否會<xref:System.Security.Policy.Publisher>建立辨識項。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|說明|  
|-----------|-----------------|  
|`false`|不會建立<xref:System.Security.Policy.Publisher>辨識項。|  
|`true`|建立<xref:System.Security.Policy.Publisher>辨識項。 這是預設值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  在 .NET Framework 4 和更新版本中, 這個元素不會影響元件載入時間。 如需詳細資訊, 請參閱[安全性變更](../../../security/security-changes.md)中的「安全性原則簡化」一節。  
  
 Common language runtime (CLR) 會在載入時嘗試驗證 Authenticode 簽章, 以建立<xref:System.Security.Policy.Publisher>元件的辨識項。 不過, 根據預設, 大部分的應用程式都<xref:System.Security.Policy.Publisher>不需要辨識項。 標準 CAS 原則不依賴<xref:System.Security.Policy.PublisherMembershipCondition>。 除非您的應用程式是在具有自訂 CAS 原則的電腦上執行, 或想要滿足部分信任環境中的<xref:System.Security.Permissions.PublisherIdentityPermission>要求, 否則您應該避免與驗證發行者簽章相關聯的不必要啟動成本。 (在完全信任環境中, 身分識別許可權的需求一律會成功)。  
  
> [!NOTE]
>  我們建議服務使用`<generatePublisherEvidence>`元素來改善啟動效能。  使用這個元素也有助於避免延遲, 這可能會造成超時和取消服務啟動。  
  
## <a name="configuration-file"></a>組態檔  
 這個元素只能用在應用程式佈建檔中。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用專案來停`<generatePublisherEvidence>`用應用程式的 CAS 發行者原則檢查。  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
