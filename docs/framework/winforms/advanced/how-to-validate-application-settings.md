---
title: "如何：驗證應用程式設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating application settings
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], validating
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e12620a5079efaba4faa9101253a3a586965b7e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-application-settings"></a>如何：驗證應用程式設定
本主題示範如何在保存應用程式設定之前先行驗證。  
  
 因為應用程式設定為強型別，對於使用者無法將型別不正確的資料指派給指定的設定這一點，您可以有些信心。 不過，使用者仍然可以嘗試將超出可接受界限的值指派給設定，例如，提供未來時間的出生日期。 <xref:System.Configuration.ApplicationSettingsBase>所有的應用程式設定類別的父類別公開的四個事件，若要啟用這類繫結檢查。 在處理這些事件時，您所有的驗證程式碼會放在單一位置，而不是零散分佈在整個專案。  
  
 您所使用的事件取決於何時需要驗證設定，如下表所述。  
  
|Event - 事件|發生時機和用途|  
|-----------|------------------------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|在初次載入設定屬性群組之後發生。<br /><br /> 使用此事件可先驗證整個屬性群組的初始值，然後才將值用於應用程式。|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|在單一設定屬性值變更之前發生。<br /><br /> 使用此事件可先驗證單一屬性，然後才將它變更。 它可立即為使用者提供有關其動作和選擇的意見回應。|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|在單一設定屬性值變更之後發生。<br /><br /> 使用此事件可在單一屬性變更後，對此屬性進行驗證。 除非系統需要冗長的非同步驗證程序，否則此事件很少會用於進行驗證。|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|在儲存設定屬性群組之前發生。<br /><br /> 使用此事件可先驗證整個屬性群組的值，然後再儲存到磁碟中予以保存。|  
  
 一般而言，您不會在相同應用程式內將這些事件全都用於進行驗證。 例如，它通常是藉由只處理符合所有的驗證需求可能<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>事件。  
  
 當事件處理常式偵測到無效值時，它通常會執行下列其中一個動作︰  
  
-   自動提供已知正確的值，例如預設值。  
  
-   重新查詢伺服器程式碼的使用者以獲得資訊。  
  
-   事件引發之前及其相關聯的動作，例如<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>和<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>，會使用<xref:System.ComponentModel.CancelEventArgs>取消作業的引數。  
  
 如需處理事件的詳細資訊，請參閱[事件處理常式概觀](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)。  
  
 下列程序顯示如何使用正確的出生日期測試<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>或<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>事件。 我們在撰寫這些程序時，是假設您已建立應用程式設定；在此範例中，我們會對名為 `DateOfBirth` 的設定執行界限檢查。 如需建立設定的詳細資訊，請參閱[如何：建立應用程式設定](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)。  
  
### <a name="to-obtain-the-application-settings-object"></a>取得應用程式設定物件  
  
-   請完成下列其中一項來取得應用程式設定物件 (包裝函式執行個體) 的參考︰  
  
    -   如果您是使用**屬性編輯器**中的 [Visual Studio 應用程式設定] 對話方塊來建立您的設定，您可以透過下列運算式擷取針對您的語言所產生的預設設定物件。  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         -或-  
  
    -   如果您是 Visual Basic 開發人員，並且使用專案設計工具來建立應用程式設定，您可以使用 [My.Settings 物件](~/docs/visual-basic/language-reference/objects/my-settings-object.md)來擷取您的設定。  
  
         -或-  
  
    -   如果您建立您的設定由衍生自<xref:System.Configuration.ApplicationSettingsBase>直接管理，您必須手動將您的類別具現化。  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 我們在撰寫下列程序時，是假設您已透過完成此程序中的最後一項來取得應用程式設定物件。  
  
### <a name="to-validate-application-settings-when-a-setting-is-changing"></a>在有設定變更時驗證應用程式設定  
  
1.  如果您是 C# 開發人員，在您的表單或控制項的`Load`事件，加入事件處理常式<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>事件。  
  
     -或-  
  
     如果您是 Visual Basic 開發人員，您應該使用 `WithEvents` 關鍵字來宣告 `Settings` 變數。  
  
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
  
2.  定義事件處理常式，並在其內部撰寫程式碼以執行出生日期界限檢查。  
  
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
  
### <a name="to-validate-application-settings-when-a-save-occurs"></a>在發生儲存時驗證應用程式設定  
  
1.  在您的表單或控制項的`Load`事件，加入事件處理常式<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>事件。  
  
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
  
2.  定義事件處理常式，並在其內部撰寫程式碼以執行出生日期界限檢查。  
  
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
  
## <a name="see-also"></a>請參閱  
 [在 Windows Forms 中建立事件處理常式](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [如何：建立應用程式設定](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)
