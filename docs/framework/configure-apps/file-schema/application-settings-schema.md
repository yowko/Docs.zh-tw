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
manager: markl
ms.openlocfilehash: 7af6342e9c05fc4e6c1bf4daac59db14ccdf22c7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="application-settings-schema"></a>應用程式設定結構描述

應用程式設定允許的 Windows Form 或 ASP.NET 應用程式來儲存和擷取應用程式範圍和使用者範圍設定。 在此內容中*設定*任何一項可能是應用程式特定的或目前使用者特有的資訊，從使用者的資料庫連接字串的任何項目慣用的預設視窗大小。

根據預設，Windows Forms 應用程式的應用程式設定使用<xref:System.Configuration.LocalFileSettingsProvider>類別，以將設定儲存在 XML 組態檔會使用.NET 組態系統。 如需使用應用程式設定之檔案的詳細資訊，請參閱[應用程式設定架構](~/docs/framework/winforms/advanced/application-settings-architecture.md)。

應用程式設定會定義下列項目，它會使用組態檔的一部分。

| 項目                    | 描述                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | 包含所有**\<設定 >** 應用程式特定的標記。                         |
| **\<userSettings >**        | 包含所有**\<設定 >** 特定於目前的使用者標記。                        |
| **\<設定 >**             | 定義設定。 子系 **\<applicationSettings >** 或 **\<userSettings >**。 |
| **\<value>**               | 定義設定的值。 子系**\<設定 >**。                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > 項目

這個項目包含所有**\<設定 >** 特有的用戶端電腦上的應用程式執行個體的標籤。 它不會定義任何屬性。

## <a name="usersettings-element"></a>\<userSettings > 項目

這個項目包含所有**\<設定 >** 專屬於目前正在使用應用程式之使用者的標記。 它不會定義任何屬性。

## <a name="setting-element"></a>\<設定 > 項目

這個項目定義的設定。 它有下列屬性。

| 屬性        | 描述 |
| ---------------- | ----------- |
| **name**         | 必要。 設定的唯一識別碼。 透過 Visual Studio 建立的設定會儲存具有名稱`ProjectName.Properties.Settings`。 |
| **serializedAs** | 必要。 要用於序列化成文字值的格式。 有效值為：<br><br>- `string`。 值序列化為字串，使用<xref:System.ComponentModel.TypeConverter>。<br>- `xml`。 使用 XML 序列化序列化值。<br>- `binary`。 值序列化為文字編碼的二進位檔使用二進位序列化。<br />- `custom`。 設定提供者知道固有的這項設定和序列化並將它取消序列化。 |

## <a name="value-element"></a>\<值 > 項目

這個項目包含設定的值。

## <a name="example"></a>範例

下列範例顯示定義兩個應用程式範圍的設定和兩個使用者範圍設定的應用程式設定檔：

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
