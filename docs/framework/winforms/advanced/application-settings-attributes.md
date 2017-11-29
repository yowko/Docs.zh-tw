---
title: "應用程式設定屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1879ac6704619092c4c0d9cd6fab0356ea07a13d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="application-settings-attributes"></a>應用程式設定屬性
應用程式設定架構提供許多可套用至應用程式設定包裝函式類別或其個別屬性的屬性。 這些屬性會檢查在執行階段應用程式設定基礎結構，通常會特別設定提供者，才能調整其運作所述需求的自訂包裝函式。  
  
 下表列出可以套用到應用程式設定包裝函式類別，這個類別的個別屬性，或兩者的屬性。 根據定義，只是單一領域屬性 —**UserScopedSettingAttribute**或**ApplicationScopedSettingAttribute**— 必須套用至每個設定的屬性。  
  
> [!NOTE]
>  自訂設定提供者會衍生自<xref:System.Configuration.SettingsProvider>類別，只需辨識下列三個屬性： **ApplicationScopedSettingAttribute**， **UserScopedSettingAttribute**，和**DefaultSettingValueAttribute**。  
  
|屬性|目標|說明|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|兩種模式|指定要用於持續性的設定提供者的簡短名稱。<br /><br /> 如果未提供這個屬性，預設的提供者， <xref:System.Configuration.LocalFileSettingsProvider>，會假設。|  
|<xref:System.Configuration.UserScopedSettingAttribute>|兩種模式|做為使用者範圍的應用程式設定中定義的屬性。|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|兩種模式|為應用程式範圍的應用程式設定中定義的屬性。|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|屬性|指定可以還原序列化提供者為此屬性的硬式編碼預設值的字串。<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider>不需要此屬性，而且將覆寫任何值，提供這個屬性如果沒有已經保存值。|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|屬性|提供個別的設定，主要是由執行階段和設計階段工具使用描述性的測試。|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|類別|提供明確的設定群組名稱。 如果這個屬性已遺失，<xref:System.Configuration.ApplicationSettingsBase>使用包裝函式類別名稱。|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|類別|提供描述性的測試設定群組，主要是供執行階段和設計階段工具。|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|兩種模式|指定應提供給屬性的設定群組的零或多個管理服務。 可用的服務會描述<xref:System.Configuration.SettingsManageability>列舉型別。|  
|<xref:System.Configuration.SpecialSettingAttribute>|屬性|表示設定屬於特殊的預先定義的類別，例如連接字串，所建議的設定提供者的特殊處理。 預先定義的類別，這個屬性會由<xref:System.Configuration.SpecialSetting>列舉型別。|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|兩種模式|指定的設定群組或內容的慣用的序列化機制。 可用的序列化機制會由<xref:System.Configuration.SettingsSerializeAs>列舉型別。|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|屬性|指定的設定提供者應該停用所有應用程式升級功能 [標記] 屬性。|  
  
 *類別*表示屬性可以套用至應用程式設定包裝函式類別只。 *屬性*指出屬性可以套用的設定內容。 *同時*表示可以在其中一個層級套用屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 [應用程式設定架構](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [如何：建立應用程式設定](http://msdn.microsoft.com/en-us/53b3af80-1c02-4e35-99c6-787663148945)
