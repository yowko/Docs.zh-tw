---
title: "應用程式設定屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "應用程式設定 [Windows Form], 屬性"
  - "屬性 [Windows Form], 應用程式設定"
  - "包裝函式類別, 應用程式設定"
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 應用程式設定屬性
應用程式設定架構提供了許多屬性 \(Attribute\)，可套用至應用程式設定包裝函式類別 \(Wrapper Class\) 或其個別屬性 \(Property\)。  應用程式設定基礎結構 \(尤其經常是設定提供者\) 會在執行階段檢查這些屬性 \(Attribute\)，將屬性 \(Attribute\) 的運作修改為符合自訂包裝函式所敍述的需求。  
  
 下表列出了可套用至應用程式設定包裝函式類別、該類別之個別屬性 \(Property\) 或這兩者的屬性 \(Attribute\)。  根據定義，唯有單一範圍屬性 \(Attribute\)，**UserScopedSettingAttribute** 或 **ApplicationScopedSettingAttribute**，才必須一一套用至所有設定屬性 \(Property\)。  
  
> [!NOTE]
>  只有在識別 **ApplicationScopedSettingAttribute**、**UserScopedSettingAttribute** 和 **DefaultSettingValueAttribute** 這三個屬性 \(Attribute\) 的時候才需要衍生自 <xref:System.Configuration.SettingsProvider> 類別的自訂設定提供者。  
  
|屬性|目標|描述|  
|--------|--------|--------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Both|指定保存時所使用的設定提供者之簡短名稱。<br /><br /> 如果未提供這個屬性 \(Attribute\)，則會假設為預設提供者 <xref:System.Configuration.LocalFileSettingsProvider>。|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Both|將屬性 \(Property\) 定義為使用者範圍的應用程式設定。|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Both|將屬性 \(Property\) 定義為應用程式範圍的應用程式設定。|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|屬性|指定字串，此字串可由提供者還原序列化，而直接編寫成這個屬性 \(Property\) 的預設值。<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> 並不需要這個屬性 \(Attribute\)，而且如果已有保存的數值那麼它將覆寫此屬性所提供的任何值。|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|屬性|提供個別設定的描述性測試，主要供執行階段工具和設計階段工具使用。|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|類別|提供設定群組的明確名稱。  如果找不到這個屬性 \(Attribute\)，則 <xref:System.Configuration.ApplicationSettingsBase> 使用包裝函式類別名稱。|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|類別|提供設定群組的描述性測試，主要供執行階段工具和設計階段工具使用。|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Both|指定零或多個管理性服務，此服務應提供給設定群組或設定屬性 \(Property\)。  可用的服務是由 <xref:System.Configuration.SettingsManageability> 列舉型別描述。|  
|<xref:System.Configuration.SpecialSettingAttribute>|屬性|指定設定屬於某一特殊預先定義的分類，例如連接字串 \(Connection String\)，該分類建議由設定提供者進行特別處理。  這個屬性 \(Attribute\) 的預先定義分類是由 <xref:System.Configuration.SpecialSetting> 列舉型別定義。|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Both|指定設定群組或設定屬性 \(Property\) 的慣用序列化 \(Serialization\) 機制。  可用的序列化機制是由 <xref:System.Configuration.SettingsSerializeAs> 列舉型別定義。|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|屬性|指定設定提供者應該停用已標記屬性 \(Property\) 的所有應用程式升級功能。|  
  
 *類別*表示該屬性 \(Attribute\) 只能套用至應用程式設定包裝函式類別。  「*屬性*」\(Property\) 表示該屬性 \(Attribute\) 只能套用至設定屬性 \(Property\)。  「*兩者*」\(Both\) 表示該屬性 \(Attribute\) 可以套用至兩者之中任一層級。  
  
## 請參閱  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.SettingsProvider>   
 [應用程式設定架構](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)   
 [How to: Create Application Settings](http://msdn.microsoft.com/zh-tw/53b3af80-1c02-4e35-99c6-787663148945)