---
title: 自訂控制項的應用程式設定
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: 46300f679471874ac5046d0a1077d8abca57f2c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="application-settings-for-custom-controls"></a>自訂控制項的應用程式設定
您必須完成特定工作，讓您的自訂控制項能夠保存應用程式設定，在第三方應用程式中裝載控制項時。  
  
 大部分的應用程式設定功能的相關文件會假設您要建立的獨立應用程式寫入。 不過，如果您要建立其他開發人員將裝載的控制項在其應用程式，您需要採取一些額外的步驟，才能讓控制項保存它的設定正確。  
  
## <a name="application-settings-and-custom-controls"></a>應用程式設定和自訂控制項  
 您要讓控制項正確保存它的設定，它必須封裝程序，藉由建立它自己專用的應用程式設定包裝函式類別，衍生自<xref:System.Configuration.ApplicationSettingsBase>。 此外，主控制項類別必須實作<xref:System.Configuration.IPersistComponentSettings>。 介面包含數個屬性，以及兩個方法：<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>和<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>。 如果您將控制項加入表單使用**Windows Form 設計工具**在 Visual Studio 中，會呼叫 Windows Form<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>自動初始化控制項時，您必須呼叫<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>自行在`Dispose`控制項的方法。  
  
 此外，您應該實作下列自訂控制項，例如 Visual Studio 設計階段環境中正常運作的應用程式設定的順序：  
  
1.  自訂應用程式設定類別的建構函式與<xref:System.ComponentModel.IComponent>做為單一參數。 使用這個類別來儲存及載入的所有應用程式設定。 當您建立這個類別的新執行個體時，傳遞您的自訂控制項的建構函式。  
  
2.  已建立並放置在表單中，例如在表單的控制項之後，建立此自訂設定類別<xref:System.Windows.Forms.Form.Load>事件處理常式。  
  
 如需建立自訂的設定類別的指示，請參閱[How to： 建立應用程式設定](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)。  
  
## <a name="settings-keys-and-shared-settings"></a>設定索引鍵和共用的設定  
 有些控制項可用於多次相同的格式。 大部分的情況下，您會想要保存其自己的個別設定這些控制項。 與<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>屬性<xref:System.Configuration.IPersistComponentSettings>，您可以提供用來釐清多個版本的表單上控制項的唯一字串。  
  
 最簡單的方式實作<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>是使用<xref:System.Windows.Forms.Control.Name%2A>的控制項屬性<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>。 當您載入或儲存控制項的設定時，您將值傳遞<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>入<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>屬性<xref:System.Configuration.ApplicationSettingsBase>類別。 它會保存為 XML 的使用者的設定時，應用程式設定就會使用這個唯一索引鍵。 下列程式碼範例示範如何`<userSettings>`區段可能會尋找名為自訂控制項的執行個體`CustomControl1`，將儲存的設定及其`Text`屬性。  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 未提供的值之控制項的任何執行個體<xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A>會共用相同的設定。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [應用程式設定架構](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
