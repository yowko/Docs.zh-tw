---
title: <generatePublisherEvidence> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645350"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> 元素
指定運行時是否為代碼存<xref:System.Security.Policy.Publisher>取 安全性 (CAS) 創建證據。  
  
[**\<設定>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<執行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<產生發行者證據>**  
  
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
|`enabled`|必要屬性。<br /><br /> 指定執行時是否創建<xref:System.Security.Policy.Publisher>證據。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|不創建<xref:System.Security.Policy.Publisher>證據。|  
|`true`|創建<xref:System.Security.Policy.Publisher>證據。 這是預設值。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 在 .NET 框架 4 及更高版本中,此元素對程式集載入時間沒有影響。 有關詳細資訊,請參閱[安全更改](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)中的"安全策略簡化"部分。  
  
 通用語言執行時 (CLR) 嘗試在載入時驗證身份驗證簽名,以創建<xref:System.Security.Policy.Publisher>程式集 的證據。 但是,默認情況下,大多數應用程式不需要<xref:System.Security.Policy.Publisher>證據。 標準 CAS 政策不<xref:System.Security.Policy.PublisherMembershipCondition>依賴於 。 您應該避免與驗證發行者簽名相關的不必要的啟動成本,除非您的應用程式在具有自訂 CAS 策略的電腦上執行,或者打算滿足部分信任環境<xref:System.Security.Permissions.PublisherIdentityPermission>中的需求 。 (對標識許可權的要求總是在完全信任的環境中成功。  
  
> [!NOTE]
> 我們建議服務使用`<generatePublisherEvidence>`元素來提高啟動性能。  使用此元素還有助於避免可能導致超時和服務啟動取消的延遲。  
  
## <a name="configuration-file"></a>組態檔  
 此元素只能在應用程式配置檔中使用。  
  
## <a name="example"></a>範例  
 下面的範例展示如何使用`<generatePublisherEvidence>`元素來禁用檢查應用程式的 CAS 發行者策略。  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行時設定架構](index.md)
- [設定檔案架構](../index.md)
