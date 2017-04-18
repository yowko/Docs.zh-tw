---
title: "如何：驗證應用程式設定 | Microsoft Docs"
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
  - "應用程式設定, 驗證"
  - "應用程式設定, Windows Form"
  - "驗證應用程式設定"
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：驗證應用程式設定
這個範例示範如何在保存應用程式設定之前先對它們進行驗證。  
  
 由於應用程式設定屬於強型別 \(Strongly Typed\)，所以，在某種程度上，您可以信任使用者不會將錯誤型別的資料指派給指定的設定。  但是，使用者仍然可以嘗試將落於可接受界限之外的值指派給設定，例如提供一個未來的出生日期。  所有應用程式設定類別的父類別 <xref:System.Configuration.ApplicationSettingsBase>，會公開四個事件以啟用如範圍檢查等工作。  處理這些事件時會將所有驗證程式碼置於單一位置，而不是將它四散於專案各處。  
  
 所使用的事件是取決於您需要驗證設定的時機，如以下表所示。  
  
|事件|發生時機和使用方法|  
|--------|---------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|發生於初始載入設定屬性群組之後。<br /><br /> 若要先驗證全部屬性群組的初始值然後才在應用程式中使用此值，請使用這個事件。|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|發生於變更單一設定屬性值之前。<br /><br /> 若要在變更單一屬性之前先進行驗證，請使用這個事件。  它可以提供使用者與其動作和選擇相關的即時回應。|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|發生於變更單一設定屬性值之後。<br /><br /> 若要在變更單一屬性之後才進行驗證，請使用這個事件。  除非是需要冗長的非同步驗證過程，否則驗證時鮮少使用這個事件。|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|發生於儲存設定屬性群組之前。<br /><br /> 若要先驗證全部屬性群組的值然後才將它們保存於磁碟中，請使用這個事件。|  
  
 進行驗證時這些事件通常不會在相同應用程式內全部同時使用。  例如，只處理 <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> 事件即可能符合所有驗證需求。  
  
 當事件處理常式偵測到無效值時，它通常會執行下列其中一項動作：  
  
-   自動提供已知的正確值，例如預設值。  
  
-   重新詢問伺服端程式碼的使用者以取得資訊。  
  
-   如果是在執行相關動作前即先引發的事件，例如 <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> 和 <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>，會使用 <xref:System.ComponentModel.CancelEventArgs> 引數來取消作業。  
  
 如需事件處理的詳細資訊，請參閱 [事件處理常式概觀](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)。  
  
 在下列程序中，示範了如何使用 <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> 或 <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> 事件來測試是否為有效的出生日期。  此程序的假設是您已經建立了應用程式設定，而且在這個範例中，將會對名為  `DateOfBirth` 的設定執行範圍檢查。  如需建立設定的詳細資訊，請參閱 [如何：建立應用程式設定](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)。  
  
### 若要取得應用程式設定物件  
  
-   請完成下列其中一項，以取得應用程式設定物件 \(包裝函式執行個體\) 的參考：  
  
    -   如果您是使用 \[**屬性編輯器**\] 中的 \[Visual Studio 應用程式設定\] 對話方塊來建立設定，則可利用以下運算式擷取配合程式語言而產生的預設設定物件。  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         \-或\-  
  
    -   如果您是 Visual Basic 開發人員而且使用專案設計工具來建立應用程式設定，則可使用 [My.Settings 物件](../../../../ocs/visual-basic/language-reference/objects/my-settings-object.md) 擷取設定。  
  
         \-或\-  
  
    -   如果您是藉由直接從 <xref:System.Configuration.ApplicationSettingsBase> 衍生的方式來建立設定，則需要手動產生 \(Instantiate\) 類別。  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 下列程序的依據假設是，您採取了本程序的最後一個項目來取得應用程式設定物件。  
  
### 若要在設定變更時驗證應用程式設定  
  
1.  如果您是 C\# 開發人員，請在表單或控制項的  `Load`  事件中加入 <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> 事件的事件處理常式。  
  
     \-或\-  
  
     如果您是 Visual Basic 開發人員，則應使用 `WithEvents` 關鍵字宣告 `Settings` 變數。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(sender as Object, e as EventArgs)  
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging  
    End Sub   
    ```  
  
2.  定義事件處理常式，然後在其中撰寫程式碼以根據出生日期執行範圍檢查。  
  
    ```csharp  
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)  
    {  
        if (e.SettingName.Equals("DateOfBirth")) {  
            Date newDate = (Date)e.NewValue;  
            If (newDate > Date.Now) {  
                e.Cancel = true;  
                // Inform the user.  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging  
        If (e.SettingName.Equals("DateOfBirth")) Then  
            Dim NewDate as Date = CType(e.NewValue, Date)  
            If (NewDate > Date.Now) Then  
                e.Cancel = True  
                ' Inform the user.  
            End If  
        End If  
    End Sub  
    ```  
  
### 若要在發生儲存行為時驗證應用程式設定  
  
1.  請在表單或控制項的  `Load`  事件中加入 <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> 事件的事件處理常式。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(Sender as Object, e as EventArgs)  
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving  
    End Sub  
    ```  
  
2.  定義事件處理常式，然後在其中撰寫程式碼以根據出生日期執行範圍檢查。  
  
    ```csharp  
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)  
    {  
        if (this["DateOfBirth"] > Date.Now) {  
            e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)  
        If (Me["DateOfBirth"] > Date.Now) Then  
            e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## 請參閱  
 [在 Windows Form 中建立事件處理常式](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [如何：建立應用程式設定](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)