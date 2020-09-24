---
title: <generatePublisherEvidence> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 506e7873fab8e41fce121587c22d85600a8b1760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158769"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> 項目

指定執行時間是否 <xref:System.Security.Policy.Publisher> 為代碼啟用安全性建立證據， (CAS) 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定執行時間是否要建立辨識項 <xref:System.Security.Policy.Publisher> 。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不會建立辨識項 <xref:System.Security.Policy.Publisher> 。|  
|`true`|建立辨識項 <xref:System.Security.Policy.Publisher> 。 此為預設值。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 在 .NET Framework 4 和更新版本中，此元素不會影響元件載入時間。 如需詳細資訊，請參閱 [安全性變更](/previous-versions/dotnet/framework/security/security-changes)中的「安全性原則簡化」一節。  
  
 Common language runtime (CLR) 會嘗試在載入時驗證 Authenticode 簽章，以建立元件的辨識項 <xref:System.Security.Policy.Publisher> 。 不過，根據預設，大部分的應用程式都不需要辨識項 <xref:System.Security.Policy.Publisher> 。 標準 CAS 原則不依賴 <xref:System.Security.Policy.PublisherMembershipCondition> 。 除非您的應用程式是在具有自訂 CAS 原則的電腦上執行，或想要 <xref:System.Security.Permissions.PublisherIdentityPermission> 在部分信任環境中滿足的需求，否則您應該避免與驗證發行者簽章相關的不必要啟動成本。 在完全信任環境中，身分識別許可權的 (要求一律會成功。 )   
  
> [!NOTE]
> 我們建議服務使用 `<generatePublisherEvidence>` 元素來改善啟動效能。  使用這個元素也有助於避免延遲，而這可能會導致服務啟動的時間和取消。  
  
## <a name="configuration-file"></a>組態檔  

 此元素只能用在應用程式佈建檔中。  
  
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

- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
