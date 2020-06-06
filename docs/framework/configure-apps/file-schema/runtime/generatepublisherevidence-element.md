---
title: <generatePublisherEvidence> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "81645350"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> 項目
指定執行時間是否 <xref:System.Security.Policy.Publisher> 為代碼啟用安全性（CAS）建立辨識項。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定執行時間是否會建立辨識項 <xref:System.Security.Policy.Publisher> 。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會建立辨識項 <xref:System.Security.Policy.Publisher> 。|  
|`true`|建立辨識項 <xref:System.Security.Policy.Publisher> 。 此為預設值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 在 .NET Framework 4 和更新版本中，這個元素不會影響元件載入時間。 如需詳細資訊，請參閱[安全性變更](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)中的「安全性原則簡化」一節。  
  
 Common language runtime （CLR）會在載入時嘗試驗證 Authenticode 簽章，以建立元件的辨識項 <xref:System.Security.Policy.Publisher> 。 不過，根據預設，大部分的應用程式都不需要辨識項 <xref:System.Security.Policy.Publisher> 。 標準 CAS 原則不依賴 <xref:System.Security.Policy.PublisherMembershipCondition> 。 除非您的應用程式是在具有自訂 CAS 原則的電腦上執行，或想要滿足 <xref:System.Security.Permissions.PublisherIdentityPermission> 部分信任環境中的要求，否則您應該避免與驗證發行者簽章相關聯的不必要啟動成本。 （在完全信任環境中，身分識別許可權的需求一律會成功）。  
  
> [!NOTE]
> 我們建議服務使用 `<generatePublisherEvidence>` 元素來改善啟動效能。  使用這個元素也有助於避免延遲，這可能會造成超時和取消服務啟動。  
  
## <a name="configuration-file"></a>組態檔  
 這個元素只能用在應用程式佈建檔中。  
  
## <a name="example"></a>範例  
 下列範例顯示如何使用專案 `<generatePublisherEvidence>` 來停用應用程式的 CAS 發行者原則檢查。  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行時間設定架構](index.md)
- [設定檔架構](../index.md)
