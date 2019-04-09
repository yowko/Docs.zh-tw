---
title: 應用程式設定屬性
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: f945d8e6918c271eeb5fdf3cf9c357b1c2bbca66
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079639"
---
# <a name="application-settings-attributes"></a>應用程式設定屬性
應用程式設定架構提供許多可套用至應用程式設定包裝函式類別或其個別屬性的屬性。 這些屬性會檢查在執行階段應用程式設定基礎結構，通常會特別設定提供者，才能調整其運作的自訂包裝函式所述的需求。  
  
 下表列出的屬性可以套用到應用程式設定包裝函式類別，這個類別的個別屬性，或兩者。 根據定義，只是單一的 scope 屬性 —**UserScopedSettingAttribute**或是**ApplicationScopedSettingAttribute**— 必須套用至每個設定屬性。  
  
> [!NOTE]
>  為自訂設定提供者中，衍生自<xref:System.Configuration.SettingsProvider>類別中，只有需要辨識下列的三個屬性：**ApplicationScopedSettingAttribute**， **UserScopedSettingAttribute**，以及**DefaultSettingValueAttribute**。  
  
|屬性|Target|描述|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|兩者|指定要用於持續性設定提供者的簡短名稱。<br /><br /> 如果未提供這個屬性，預設的提供者， <xref:System.Configuration.LocalFileSettingsProvider>，會假設。|  
|<xref:System.Configuration.UserScopedSettingAttribute>|兩者|為使用者範圍的應用程式設定中定義的屬性。|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|兩者|做為應用程式範圍的應用程式設定中定義的屬性。|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|屬性|指定可以還原序列化提供者的硬式編碼預設值，這個屬性的字串。<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider>不需要這個屬性，而且將會覆寫任何值，提供這個屬性是否有值已保存。|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|屬性|有個別的設定，主要是由執行階段和設計階段工具提供描述性的測試。|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|類別|提供明確的設定群組的名稱。 如果這個屬性已遺失，<xref:System.Configuration.ApplicationSettingsBase>使用包裝函式類別名稱。|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|類別|設定群組中，主要是由執行階段和設計階段工具提供描述性的測試。|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|兩者|指定應該提供給屬性的設定群組的零或多個可管理性服務。 可用的服務描述<xref:System.Configuration.SettingsManageability>列舉型別。|  
|<xref:System.Configuration.SpecialSettingAttribute>|屬性|指出設定屬於特殊的預先定義的類別，例如連接字串，所建議的設定提供者的特殊處理。 預先定義的類別，這個屬性由定義<xref:System.Configuration.SpecialSetting>列舉型別。|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|兩者|指定的設定群組或屬性的慣用的序列化機制。 可用的序列化機制由定義<xref:System.Configuration.SettingsSerializeAs>列舉型別。|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|屬性|指定設定提供者，應該停用所有的應用程式升級功能以標示屬性。|  
  
 *類別*指出，屬性可以只套用至應用程式設定包裝函式類別。 *屬性*指出屬性可以套用唯一的設定屬性。 *兩者*指出屬性可以套用在任一個層級。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [應用程式設定架構](application-settings-architecture.md)
- [HOW TO：建立應用程式設定](how-to-create-application-settings.md)
