---
title: "應用程式設定結構描述 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "應用程式設定, 結構描述 [Windows Form]"
  - "組態結構描述 [.NET Framework], 應用程式設定"
  - "結構描述應用程式設定"
  - "Windows Form, 應用程式設定結構描述"
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
caps.latest.revision: 3
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 3
---
# 應用程式設定結構描述
應用程式設定可讓 Windows Form 或 ASP.NET 應用程式儲存及擷取應用程式範圍和使用者範圍的設定。  在本內容中，「設定」是指專用於應用程式或專用於目前使用者的任何一項資訊，從資料庫連接字串到使用者慣用的預設視窗大小等等都是。  
  
 根據預設，Windows Form 應用程式中的應用程式設定會使用 <xref:System.Configuration.LocalFileSettingsProvider>，其會使用 .NET 組態系統來儲存 XML 組態檔中的設定。  如需應用程式設定的檔案用法的詳細資訊，請參閱[應用程式設定架構](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)。  
  
 應用程式設定會定義下列項目做為它所使用的組態檔的一部分。  
  
|元素|說明|  
|--------|--------|  
|`<applicationSettings>` 項目|包含應用程式專用的所有 `<setting>` 標籤。|  
|`<userSettings>` 項目|包含目前使用者專用的所有 `<setting>` 標籤。|  
|`<setting>` 項目|會定義某項設定，  是 `<applicationSettings>` 或 `<userSettings>` 的子系。|  
|`<value>` 項目|會定義某項設定的值，  是 `<setting>` 的子系。|  
  
## \<applicationSettings\> 項目  
 這個項目會包含用戶端電腦上應用程式執行個體專用的所有 \<setting\> 標籤。  它不會定義任何屬性。  
  
## \<userSettings\> 項目  
 這個項目會包含目前正在使用應用程式的使用者所專用的所有 \<setting\> 標籤。  它不會定義任何屬性。  
  
## \<setting\> 項目  
 這個項目會定義某個設定。  它具有下列屬性：  
  
|元素|說明|  
|--------|--------|  
|`name`|必要項。  設定的唯一 ID。  經由 Visual Studio 所建立的設定都是以 `ProjectName``.Properties.Settings` 的名稱來儲存。|  
|`serializedAs`|必要項。  用於將值序列化為文字時要使用的格式。  有效值為：<br /><br /> -   `string`。  經由使用 <xref:System.ComponentModel.TypeConverter> 將值序列化為字串。<br />-   `xml`。  經由使用 XML 序列化將值加以序列化。<br />-   `binary`。  經由使用二進位序列化將值序列化為文字編碼的二進位碼。<br />-   `custom`。  設定提供者原本就瞭解這項設定，並且會將它序列化與還原序列化。<br />-   若要使用二進位或自訂序列化，您必須自己定義設定類別，並使用 <xref:System.Configuration.SettingsSerializeAsAttribute> 來指定二進位或自訂序列化。|  
  
## \<value\> 項目  
 這個項目會包含設定的值。  
  
## 範例  
 下列程式碼範例會示範一個應用程式設定檔，此檔會定義兩個應用程式範圍設定以及兩個使用者範圍設定。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </sectionGroup>  
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />  
        </sectionGroup>  
    </configSections>  
    <applicationSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="Cursor" serializeAs="String">  
                <value>Default</value>  
            </setting>  
            <setting name="DoubleBuffering" serializeAs="String">  
                <value>False</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </applicationSettings>  
    <userSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="FormTitle" serializeAs="String">  
                <value>Form1</value>  
            </setting>  
            <setting name="FormSize" serializeAs="String">  
                <value>595, 536</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </userSettings>  
</configuration>  
```  
  
## 請參閱  
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [應用程式設定架構](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)