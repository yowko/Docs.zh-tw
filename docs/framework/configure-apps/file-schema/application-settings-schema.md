---
title: 應用程式設定架構
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242825"
---
# <a name="application-settings-schema"></a>應用程式設定架構

應用程式設置允許 Windows 窗體或 ASP.NET 應用程式儲存和檢索應用程式範圍和用戶範圍的設置。 在此上下文中,*設定*是可能特定於應用程式或特定於當前使用者的任何資訊 - 從資料庫連接字串到使用者首選預設視窗大小的任何資訊。

預設情況下,Windows 表單應用程式中的應用程式設置<xref:System.Configuration.LocalFileSettingsProvider>使用類,該類使用.NET 配置系統在 XML 設定檔中儲存設定。 有關應用程式設定使用的檔案的詳細資訊,請參閱[應用程式設定架構結構](../../winforms/advanced/application-settings-architecture.md)。

應用程式設定將以下元素定義為它使用的設定檔的一部分。

| 項目                    | 描述                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<應用程式設定>** | 包含特定於應用程式**\<的所有設置>** 標記。                         |
| **\<使用者設定>**        | 包含特定於當前用戶**\<的所有設置>** 標記。                        |
| **\<設定>**             | 定義設定。 應用程式>**\<或 用戶設置的子項>。** ** \<** |
| **\<值>**               | 定義設置的值。 設置>的子項。 ** \<**                                   |

## <a name="applicationsettings-element"></a>\<應用程式設定>元素

此元素包含特定於用戶端計算機上的應用程式實例的所有**\<設置>** 標記。 它不會定義任何屬性。

## <a name="usersettings-element"></a>\<使用者設定>元素

此元素包含特定於當前使用該應用程式的使用者的所有**\<設置>** 標記。 它不會定義任何屬性。

## <a name="setting-element"></a>\<設定>元素

此元素定義設置。 它具有以下屬性。

| 屬性        | 描述 |
| ---------------- | ----------- |
| **名稱**         | 必要。 設置的唯一 ID。 以視覺化工作室建立的設定將儲存與名稱`ProjectName.Properties.Settings`。 |
| **序列化** | 必要。 為序列化文字值格式。 有效值為：<br><br>- `string`. 該值使用 序列化為字串。 <xref:System.ComponentModel.TypeConverter><br>- `xml`. 該值使用 XML 序列化進行序列化。<br>- `binary`. 該值使用二進位序列化將該值序列化為文本編碼二進位。<br />- `custom`. 設置提供程式對此設置有固有的知識,並序列化並取消序列化。 |

## <a name="value-element"></a>\<數值>元素

此元素包含設置的值。

## <a name="example"></a>範例

下面的範例顯示了一個應用程式設定檔,該檔定義了兩個應用程式範圍設定和兩個使用者範圍設定:

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

- [應用程式設定概述](../../winforms/advanced/application-settings-overview.md)
- [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md)
