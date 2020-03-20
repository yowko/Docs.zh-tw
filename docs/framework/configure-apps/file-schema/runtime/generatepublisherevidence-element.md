---
title: <generatePublisherEvidence> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 24a5ea02992a5bce681b5bab4fb7f75505bd225d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154098"
---
# <a name="generatepublisherevidence-element"></a>\<generatePublisherEvidence> 元素
指定運行時是否為代碼訪問<xref:System.Security.Policy.Publisher>安全性 （CAS） 創建證據。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<生成發行者證據>**  
  
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
|`enabled`|必要屬性。<br /><br /> 指定運行時是否創建<xref:System.Security.Policy.Publisher>證據。|  
  
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
> 在 .NET 框架 4 及更高版本中，此元素對程式集載入時間沒有影響。 有關詳細資訊，請參閱[安全更改](../../../security/security-changes.md)中的"安全性原則簡化"部分。  
  
 通用語言運行時 （CLR） 嘗試在載入時驗證身份驗證簽名，以創建程式集<xref:System.Security.Policy.Publisher>的證據。 但是，預設情況下，大多數應用程式不需要<xref:System.Security.Policy.Publisher>證據。 標準 CAS 策略不依賴于<xref:System.Security.Policy.PublisherMembershipCondition>。 您應該避免與驗證發行者簽名相關的不必要的啟動成本，除非您的應用程式在具有自訂 CAS 策略的電腦上執行，或者打算滿足部分信任環境中的需求<xref:System.Security.Permissions.PublisherIdentityPermission>。 （對標識許可權的要求總是在完全信任的環境中成功。  
  
> [!NOTE]
> 我們建議服務使用 元素`<generatePublisherEvidence>`來提高啟動性能。  使用此元素還有助於避免可能導致超時和服務啟動取消的延遲。  
  
## <a name="configuration-file"></a>組態檔  
 此元素只能在應用程式佈建檔中使用。  
  
## <a name="example"></a>範例  
 下面的示例演示如何使用 元素`<generatePublisherEvidence>`來禁用檢查應用程式的 CAS 發行者策略。  
  
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
