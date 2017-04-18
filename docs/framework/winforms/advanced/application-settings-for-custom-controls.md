---
title: "自訂控制項的應用程式設定 | Microsoft Docs"
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
  - "應用程式設定 [Windows Form], 自訂控制項"
  - "自訂控制項 [Windows Form], 應用程式設定"
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 自訂控制項的應用程式設定
當自訂控制項要裝載於協力廠商的應用程式中時，您必須先完成某些特定的工作，該控制項才能夠保存應用程式設定。  
  
 大多數關於應用程式設定功能的文件都是假設您要建立獨立應用程式 \(Standalone Application\)。  不過，如果您要建立的是其他開發人員將在他們的應用程式中裝載的控制項，則必須另外採取其他步驟，才能讓控制項正確保存它的設定。  
  
## 應用程式設定和自訂控制項  
 若要讓您的控制項能夠正確地保存它的設定，則必須建立該控制項專屬的衍生自 <xref:System.Configuration.ApplicationSettingsBase> 之應用程式設定包裝函式類別 \(Wrapper Class\)，藉此將程序封裝起來。  另外，主控制項類別必須實作 <xref:System.Configuration.IPersistComponentSettings>。  這個介面包含數個屬性以及兩個方法，即 <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> 和 <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>。  如果您是使用 Visual Studio 中的 \[**Windows Form 設計工具**\] 將控制項加入至表單，當控制項在初始化時 Windows Form 將會自動呼叫 <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A>；您必須在控制項的  `Dispose`  方法中自行呼叫 <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>。  
  
 此外，您應該實作下列項目，以便讓自訂控制項的應用程式設定能在如 Visual Studio 的設計階段環境中適當運作。  
  
1.  自訂的應用程式設定類別，其建構函式接受 <xref:System.ComponentModel.IComponent> 做為單一的參數。  請使用這個類別來儲存和載入所有的應用程式設定。  當您建立此類別的新執行個體時，請使用這個建構函式來傳遞您的自訂控制項。  
  
2.  在建立控制項並將其放置在表單上之後，建立這個自訂設定類別 \(例如在表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式中\)。  
  
 如需建立自訂設定類別的指示，請參閱 [如何：建立應用程式設定](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)。  
  
## 設定索引鍵和共用設定  
 某些控制項可以在同一表單中多次使用。  通常，您會希望這些控制項能夠保存各自的個別設定。  利用 <xref:System.Configuration.IPersistComponentSettings> 上的 <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> 屬性，您可以提供唯一的字串用以明示表單上某控制項的版本。  
  
 實作 <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> 的最簡單方法是使用控制項的 <xref:System.Windows.Forms.Control.Name%2A> 屬性做為 <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>。  載入或儲存控制項的設定時，您會將 <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> 值傳遞給 <xref:System.Configuration.ApplicationSettingsBase> 類別的 <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> 屬性。  應用程式設定使用這個唯一鍵將使用者設定保存為 XML。  下列程式碼範例會示範  `<userSettings>`  區段可以如何尋找一個名為  `CustomControl1`  的自訂控制項執行個體，此控制項是儲存其  `Text`  屬性的設定。  
  
```  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 不會把值提供給 <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> 的任何控制項執行個體將會共用相同的設定。  
  
## 請參閱  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.IPersistComponentSettings>   
 [應用程式設定架構](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)