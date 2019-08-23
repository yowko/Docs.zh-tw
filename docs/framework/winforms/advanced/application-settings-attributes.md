---
title: 應用程式設定屬性
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: b38ed931cab3a333a56dd027d5843b1c8f00dcb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916688"
---
# <a name="application-settings-attributes"></a>應用程式設定屬性
應用程式設定架構提供許多可套用至應用程式設定包裝函式類別或其個別屬性的屬性。 這些屬性會在執行時間由應用程式設定基礎結構進行檢查, 通常是設定提供者, 以便根據自訂包裝函式的指定需求來量身打造。  
  
 下表列出可套用至應用程式設定包裝函式類別、這個類別的個別屬性或兩者的屬性。 根據定義, 只有單一範圍屬性 (**system.configuration.userscopedsettingattribute>** 或**system.configuration.applicationscopedsettingattribute>** ) 必須套用至每個設定屬性。  
  
> [!NOTE]
> 從<xref:System.Configuration.SettingsProvider>類別衍生的自訂設定提供者, 只需要辨識下列三個屬性:**System.configuration.applicationscopedsettingattribute>** 、 **system.configuration.userscopedsettingattribute>** 和**system.configuration.defaultsettingvalueattribute>** 。  
  
|屬性|目標|描述|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|兩者|指定要用於持續性之設定提供者的簡短名稱。<br /><br /> 如果未提供這個屬性, 則會假設為預設<xref:System.Configuration.LocalFileSettingsProvider>的提供者。|  
|<xref:System.Configuration.UserScopedSettingAttribute>|兩者|將屬性定義為使用者範圍的應用程式設定。|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|兩者|將屬性定義為應用程式範圍的應用程式設定。|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|屬性|指定可由提供者還原序列化為此屬性之硬式編碼預設值的字串。<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider>不需要這個屬性, 而且如果有值已經保存, 將會覆寫這個屬性所提供的任何值。|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|屬性|提供個別設定的描述性測試, 主要是由執行時間和設計階段工具所使用。|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|類別|提供設定群組的明確名稱。 如果遺漏此屬性, <xref:System.Configuration.ApplicationSettingsBase>則會使用包裝函式類別名稱。|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|類別|提供設定群組的描述性測試, 主要用於執行時間和設計階段工具。|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|兩者|指定應該提供給設定群組或屬性的零個或多個管理服務。 <xref:System.Configuration.SettingsManageability>列舉會描述可用的服務。|  
|<xref:System.Configuration.SpecialSettingAttribute>|屬性|表示設定屬於特殊的預先定義類別, 例如連接字串, 這會建議由設定提供者進行特殊處理。 這個屬性的預先定義類別是由<xref:System.Configuration.SpecialSetting>列舉所定義。|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|兩者|為設定群組或屬性指定慣用的序列化機制。 可用的序列化機制是由<xref:System.Configuration.SettingsSerializeAs>列舉所定義。|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|屬性|指定設定提供者應該停用標示屬性的所有應用程式升級功能。|  
  
 *類別*指出屬性只能套用至應用程式設定包裝函式類別。 *屬性*表示屬性只能套用設定屬性。 *這兩個都*表示屬性可以在任一層級套用。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [應用程式設定架構](application-settings-architecture.md)
- [如何：建立應用程式設定](how-to-create-application-settings.md)
