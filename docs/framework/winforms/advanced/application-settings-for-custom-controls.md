---
title: 自訂控制項的應用程式設定
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: a4e477ce1c171b514482623595b2c5565564a2cb
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040465"
---
# <a name="application-settings-for-custom-controls"></a>自訂控制項的應用程式設定
當控制項裝載于協力廠商應用程式時, 您必須完成特定工作, 讓您的自訂控制項能夠保存應用程式設定。

 大部分關於應用程式設定功能的檔, 都是根據您建立獨立應用程式的假設而撰寫。 不過, 如果您要建立其他開發人員將裝載于其應用程式中的控制項, 您必須採取一些額外的步驟, 讓您的控制項正確保存其設定。

## <a name="application-settings-and-custom-controls"></a>應用程式設定和自訂控制項
 為了讓您的控制項正確保存其設定, 它必須建立自己專用的應用程式設定包裝函式類別 (衍生自<xref:System.Configuration.ApplicationSettingsBase>), 以封裝進程。 此外, 主要控制項類別必須執行<xref:System.Configuration.IPersistComponentSettings>。 介面包含數個屬性, 以及兩個方法: <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>和<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>。 如果您使用 Visual Studio 中的**Windows Form 設計工具**將控制項加入表單中, Windows Forms 會在<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>控制項初始化時自動呼叫; 您必須在控制項<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>的`Dispose`方法中呼叫自己。

 此外, 您應該執行下列動作, 讓自訂控制項的應用程式設定在設計階段環境 (例如 Visual Studio) 中正常運作:

1. 自訂應用程式設定類別, 其中包含採用做<xref:System.ComponentModel.IComponent>為單一參數的函式。 使用此類別來儲存和載入所有的應用程式設定。 當您建立這個類別的新實例時, 請使用此函式來傳遞您的自訂控制項。

2. 建立此自訂設定類別之後, 在表單上建立並放置控制項, 例如表單的<xref:System.Windows.Forms.Form.Load>事件處理常式。

 如需建立自訂設定類別的指示, [請參閱如何:建立應用程式](how-to-create-application-settings.md)設定。

## <a name="settings-keys-and-shared-settings"></a>設定機碼和共用設定
 有些控制項可以在同一個表單中多次使用。 在大部分的情況下, 您會想要讓這些控制項保存自己的個別設定。 使用上<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> <xref:System.Configuration.IPersistComponentSettings>的屬性時, 您可以提供唯一的字串, 其可在表單上區分控制項的多個版本。

 最簡單的方法<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>是<xref:System.Windows.Forms.Control.Name%2A>使用的控制項<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>屬性。 當您載入或儲存控制項的設定時, 會將的值<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>傳遞<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>至<xref:System.Configuration.ApplicationSettingsBase>類別的屬性。 應用程式設定會在將使用者的設定保存至 XML 時, 使用此唯一索引鍵。 下列程式碼範例會示範`<userSettings>`區段如何尋找名為`CustomControl1`的自訂控制項實例, 以儲存其`Text`屬性的設定。

```xml
<userSettings>
    <CustomControl1>
        <setting name="Text" serializedAs="string">
            <value>Hello, World</value>
        </setting>
    </CustomControl1>
</userSettings>
```

 未提供值的<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>控制項的任何實例都會共用相同的設定。

## <a name="see-also"></a>另請參閱

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [應用程式設定架構](application-settings-architecture.md)
