---
title: 應用程式設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f11be59941759687806591feb1edcce28b2119e6
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844226"
---
# <a name="application-settings-schema"></a>應用程式設定結構描述

應用程式設定可讓 Windows Form 或 ASP.NET 應用程式儲存及擷取應用程式範圍和使用者範圍設定。 在此情況下，*設定*是任一部分程式可能是應用程式特定的或目前使用者特定的資訊 — 來自使用者的資料庫連接字串的所有一切的慣用預設的視窗大小。

根據預設，Windows Forms 應用程式中的應用程式設定會使用<xref:System.Configuration.LocalFileSettingsProvider>類別，它會使用.NET 組態系統儲存在 XML 組態檔中的設定。 如需使用應用程式設定之檔案的詳細資訊，請參閱[應用程式設定架構](~/docs/framework/winforms/advanced/application-settings-architecture.md)。

應用程式設定會定義下列項目，它會使用組態檔的一部分。

| 元素                    | 描述                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | 包含所有**\<設定 >** 應用程式特定的標記。                         |
| **\<userSettings >**        | 包含所有**\<設定 >** 目前使用者特定的標記。                        |
| **\<設定 >**             | 定義設定。 子系 **\<applicationSettings >** 或是 **\<userSettings >**。 |
| **\<value>**               | 定義設定的值。 子系**\<設定 >**。                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > 項目

這個項目包含所有**\<設定 >** 特有的用戶端電腦上的應用程式的執行個體的標籤。 它不會定義任何屬性。

## <a name="usersettings-element"></a>\<userSettings > 項目

這個項目包含所有**\<設定 >** 專屬於目前正在使用應用程式之使用者的標記。 它不會定義任何屬性。

## <a name="setting-element"></a>\<設定 > 項目

這個項目定義的設定。 它具有下列屬性。

| 屬性        | 描述 |
| ---------------- | ----------- |
| **name**         | 必要。 設定的唯一識別碼。 透過 Visual Studio 所建立的設定會儲存名稱`ProjectName.Properties.Settings`。 |
| **serializedAs** | 必要。 要用來序列化成文字值的格式。 有效值為：<br><br>- `string`。 值序列化為字串，使用<xref:System.ComponentModel.TypeConverter>。<br>- `xml`。 值會使用 XML 序列化進行序列化。<br>- `binary`。 值會序列化為文字編碼的二進位檔使用二進位序列化。<br />- `custom`。 設定提供者的這項設定的固有知識和序列化和還原序列化它。 |

## <a name="value-element"></a>\<值 > 項目

這個項目包含設定的值。

## <a name="example"></a>範例

下列範例示範定義兩個應用程式範圍的設定和兩個使用者範圍設定的應用程式設定檔：

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
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

## <a name="see-also"></a>另請參閱

[應用程式設定概觀](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[應用程式設定架構](~/docs/framework/winforms/advanced/application-settings-architecture.md)
