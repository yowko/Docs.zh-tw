---
title: "逐步解說：使用 Visual Basic 撰寫複合控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "複合控制項, 建立"
  - "控制項 [Windows Form], 複合控制項"
  - "自訂控制項 [Visual Basic]"
  - "自訂控制項 [Windows Form], 建立"
  - "使用者控制項 [Visual Basic]"
  - "使用者控制項 [Windows Form], 使用 Visual Basic 建立"
  - "UserControl 類別, 逐步解說"
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# 逐步解說：使用 Visual Basic 撰寫複合控制項
複合控制項 \(Composite Control\) 提供了建立及重複使用自訂圖形介面的方法。  複合控制項基本上是具有視覺化表示的元件。  使用者控制項本身可包含一或多個 Windows Form 控制項、元件，或者可擴充功能的程式碼區塊，其擴充的方式為驗證使用者的輸入、修改顯示屬性或執行作者需要的其他工作。  與其他控制項的處理方式一樣，複合控制項可以放置在 Windows Form 上。  在這個逐步解說的第一個部分，您會建立名為 `ctlClock` 的簡單複合控制項。  在逐步解說的第二個部分中，您會透過繼承 \(Inheritance\) 來擴充 `ctlClock` 的功能。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
## 建立專案  
 建立新的專案時，您指定專案名稱以設定預設命名空間、組件名稱及專案名稱，並確定預設元件將會在正確的命名空間中。  
  
#### 若要建立 ctlClockLib 控制項程式庫和 ctlClock 控制項  
  
1.  在 \[**檔案**\] 功能表上，指向 \[**新增**\]，然後按一下 \[**專案**\]，開啟 \[**新增專案**\] 對話方塊。  
  
2.  從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 專案的清單中，選取 \[**Windows 控制項程式庫**\] 專案範本，在 \[**名稱**\] 方塊中輸入 `ctlClockLib`，然後按一下 \[**確定**\]。  
  
     依照預設，專案名稱 `ctlClockLib` 也會指派到根命名空間。  預設命名空間是用來限定組件中的元件名稱。  例如，假設有兩個組件提供了名為 `ctlClock` 的元件，您就可以使用 `ctlClockLib.ctlClock.`  指定 `ctlClock` 元件。  
  
3.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**UserControl1.vb**\]，再按一下 \[**重新命名**\]。  將檔案名稱變更為 `ctlClock.vb`。  當詢問您是否要重新命名程式碼項目 "UserControl1" 的所有參考時，請按一下 \[**是**\]。  
  
    > [!NOTE]
    >  根據預設，複合控制項繼承自系統提供的 <xref:System.Windows.Forms.UserControl> 類別。  <xref:System.Windows.Forms.UserControl> 類別提供所有複合控制項需要的功能，並實作標準方法與屬性。  
  
4.  在 \[**檔案**\] 功能表上，按一下 \[**全部儲存**\] 儲存專案。  
  
## 將 Windows 控制項和元件加入至複合控制項  
 視覺化介面是複合控制項的基本部分。  視覺介面的實作方法，是將一或多個 Windows 控制項加入至設計工具介面。  在下面的示範中，您會將 Windows 控制項合併至複合控制項，並撰寫程式碼以實作功能。  
  
#### 若要將標籤和計時器加入至複合控制項  
  
1.  在 \[方案總管\] 中以滑鼠右鍵按一下 \[**ctlClock.vb**\]，然後按一下 \[**設計工具檢視**\]。  
  
2.  在 \[工具箱\] 中展開 \[**通用控制項**\] 節點，然後按兩下 \[**Label**\]。  
  
     名為 `Label1` 的 <xref:System.Windows.Forms.Label> 控制項會加入至設計工具介面上的控制項。  
  
3.  在設計工具中，按一下 \[**Label1**\]。  在 \[屬性\] 視窗中設定下列屬性。  
  
    |屬性|變更為|  
    |--------|---------|  
    |**名稱**|`lblDisplay`|  
    |**文字**|`(空白)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  在 \[**工具箱**\] 中展開 \[**元件**\] 節點，然後按兩下 \[**計時器**\]。  
  
     由於 <xref:System.Windows.Forms.Timer> 是一個元件，所以在執行階段時沒有視覺化表示。  因此，它不會和控制項一起出現在設計工具介面，而是顯示在 \[元件設計工具\] 中 \(設計工具介面底部的區塊\)。  
  
5.  在 \[元件設計工具\] 中，按一下 \[**Timer1**\]，然後將 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性設定為 `1000`，並將 <xref:System.Windows.Forms.Timer.Enabled%2A> 屬性設定為 `True`。  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> 屬性會控制計時器元件的刻度頻率。  `Timer1_Tick` 每移動一個刻度，便會執行 `Timer1` 事件中的程式碼。  這個間隔代表刻度之間的毫秒數。  
  
6.  在 \[元件設計工具\] 中按兩下 \[**Timer1**\]，移至 `ctlClock` 的 `Timer1_Tick` 事件。  
  
7.  修改程式碼，使其與以下的程式碼範例類似。  務必要將存取修飾詞從 `Private` 變更成 `Protected`。  
  
     \[Visual Basic\]  
  
    ```  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     此程式碼會讓目前的時間顯示在 `lblDisplay` 中。  由於 `Timer1` 的間隔是設為 `1000`，每一千毫秒就會引發一次這個事件，因此會每秒更新目前的時間。  
  
8.  將方法修改為可覆寫。  如需詳細資訊，請參閱下列的＜繼承自使用者控制項＞章節。  
  
     \[Visual Basic\]  
  
    ```  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. 在 \[**檔案**\] 功能表上，按一下 \[**全部儲存**\] 儲存專案。  
  
## 將屬性加入至複合控制項  
 您的時鐘控制項現在封裝有一個 <xref:System.Windows.Forms.Label> 控制項和一個 <xref:System.Windows.Forms.Timer> 元件，每個都有自己的繼承屬性集。  雖然控制項的後續使用者無法存取這些控制項的個別屬性，但是您可以建立及公開自訂屬性，方法是撰寫適當的程式碼區塊。  在下列程序中，您會將屬性加入至控制項，這些屬性讓使用者能夠變更背景色彩及文字。  
  
#### 若要將屬性加入至複合控制項  
  
1.  在 \[方案總管\] 中以滑鼠右鍵按一下 \[**ctlClock.vb**\]，然後按一下 \[**檢視程式碼**\]。  
  
     您控制項的 \[程式碼編輯器\] 將會開啟。  
  
2.  找出 `Public Class ctlClock` 陳述式。  在下方輸入下列程式碼。  
  
     \[Visual Basic\]  
  
    ```  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     這些陳述式會建立私用變數，可用來儲存您即將建立的屬性的值。  
  
3.  在步驟 2 的變數宣告下方插入下列程式碼。  
  
     \[Visual Basic\]  
  
    ```  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     上述程式碼會建立 `ClockForeColor` 和 `ClockBackColor` 兩個自訂屬性，以供此控制項的後續使用者透過叫用 `Property` 來使用。  `Get` 和 `Set` 陳述式提供屬性值的儲存與擷取，以及實作適合該屬性之功能的程式碼。  
  
4.  在 \[**檔案**\] 功能表上，按一下 \[**全部儲存**\] 儲存專案。  
  
## 測試控制項  
 控制項不是獨立的專案，必須裝載在容器中。  測試控制項的執行階段行為，並使用 \[**使用者控制項測試容器**\] 執行該控制項的屬性。  如需詳細資訊，請參閱 [如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
#### 若要測試您的控制項  
  
1.  按下 F5 鍵以建置專案，並在 \[**使用者控制項測試容器**\] 中執行控制項。  
  
2.  在測試容器的屬性方格中，選取 \[`ClockBackColor`\] 屬性，然後按一下下拉箭號以顯示色板。  
  
3.  按一下想要選擇的色彩。  
  
     控制項的背景色彩會變更為選取的色彩。  
  
4.  使用類似的事件序列來驗證 `ClockForeColor` 屬性是否如預期般的運作。  
  
5.  按一下 \[**關閉**\] 關閉 \[**使用者控制項測試容器**\]。  
  
     在本章節和先前的章節中，您已經知道如何將元件和 Windows 控制項與程式碼組合，並進行封裝以複合控制項的形式來提供自訂功能。  您已經學會如何在複合控制項公開 \(Expose\) 屬性，以及如何在控制項完成後加以測試。  在接下來的章節中，則將學習如何使用 `ctlClock` 做為基底 \(Base\) 來建構繼承的複合控制項。  
  
## 繼承自複合控制項  
 在前一個章節中，學到如何將 Windows 控制項、元件以及程式碼組合成可重複使用的複合控制項。  您的複合控制項現在可以做為建置其他控制項的基礎。  從基底類別衍生類別的程序稱為「*繼承*」\(Inheritance\)。  在本章節中，您將會建立稱為 `ctlAlarmClock` 的複合控制項。  這個控制項將衍生自父控制項 `ctlClock`。  您將學習如何藉由覆寫父代方法和加入新方法與屬性來擴充 `ctlClock` 的功能。  
  
 建立繼承控制項的第一步，就是從父控制項衍生出該控制項。  這個動作會建立具備父控制項中所有屬性、方法和圖形特性的新控制項，但是也可以做為加入新功能及修改功能的基礎。  
  
#### 若要建立繼承的控制項  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**ctlClockLib**\]，指向 \[**加入**\]，然後按一下 \[**使用者控制項**\]。  
  
     \[**加入新項目**\] 對話方塊隨即開啟。  
  
2.  選取 \[**繼承的使用者控制項**\] 範本。  
  
3.  在 \[**名稱**\] 方塊中輸入 `ctlAlarmClock.vb`，然後按一下 \[**加入**\]。  
  
     \[**繼承選取器**\] 對話方塊隨即出現。  
  
4.  在 \[**元件名稱**\] 下面，按兩下 \[**ctlClock**\]。  
  
5.  在 \[方案總管\] 中瀏覽目前的專案。  
  
    > [!NOTE]
    >  稱為 \[**ctlAlarmClock.vb**\] 的檔案已經加入至目前的專案。  
  
### 加入警示屬性  
 屬性加入至繼承控制項的方法與加入至複合控制項的方法相同。  現在，您將使用屬性宣告語法，將下列兩個屬性加入至控制項中：`AlarmTime` 和 `AlarmSet`；前者會儲存警示響起的日期和時間值，後者則指出是否已設定警示。  
  
##### 若要將屬性加入至複合控制項  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**ctlAlarmClock**\]，然後按一下 \[**檢視程式碼**\]。  
  
2.  找出 ctlAlarmClock 控制項的類別宣告，出現的方式為 `Public Class ctlAlarmClock`。  在類別宣告中插入下列程式碼。  
  
     \[Visual Basic\]  
  
    ```  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### 加入至控制項的圖形介面  
 繼承控制項的視覺介面與它的父控制項的視覺介面相同。  它擁有與父控制項相同的組成控制項，但是組成控制項的屬性除非特別公開，否則無法使用。  加入到繼承複合控制項圖形介面的方法與加入到任何複合控制項的方法相同。  若要繼續加入到警示時鐘的視覺介面，您將會加入當警示響起時會閃爍的標籤控制項。  
  
##### 若要加入標籤控制項  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**ctlAlarmClock**\]，然後按一下 \[**設計工具檢視**\]。  
  
     `ctlAlarmClock` 的設計工具會在主視窗中開啟。  
  
2.  按一下 \[`lblDisplay`\] \(控制項的顯示部分\)，然後檢視 \[屬性\] 視窗。  
  
    > [!NOTE]
    >  請注意，雖然會顯示出所有屬性，但它們是暗灰色的 \(Dimmed\)。  這表示這些屬性對 `lblDisplay` 是原生的，在 \[屬性\] 視窗中不能修改或存取。  根據預設，包含在複合控制項的控制項是 `Private`，其屬性無法使用任何方法存取。  
  
    > [!NOTE]
    >  如果希望控制項的後續使用者可以存取它的內部控制項，請將這些內部控制項宣告為 `Public` 或 `Protected`。  這麼做將可讓您使用適當的程式碼設定及修改包含在複合控制項中的控制項屬性。  
  
3.  在複合控制項中加入 <xref:System.Windows.Forms.Label> 控制項。  
  
4.  使用滑鼠，將 <xref:System.Windows.Forms.Label> 控制項拖曳至緊接在顯示方塊的下方。  在 \[屬性\] 視窗中設定下列屬性。  
  
    |屬性|設定|  
    |--------|--------|  
    |**名稱**|`lblAlarm`|  
    |**文字**|Alarm\!|  
    |**TextAlign**|`MiddleCenter`|  
    |**Visible**|`False`|  
  
### 加入警示功能  
 在之前的程序中，您加入了可啟用複合控制項之警示功能的屬性及控制項。  本程序中，您將加入程式碼來比較目前時間與警示時間，以及警示的響音與閃燈是否相同。  藉由覆寫 `ctlClock` 的 `Timer1_Tick` 方法，並在其中加入其他程式碼，您將擴充 `ctlAlarmClock` 的功能，且同時保留 `ctlClock` 的所有繼承功能。  
  
##### 若要覆寫 ctlClock 的 Timer1\_Tick 方法  
  
1.  在 \[方案總管\] 中以滑鼠右鍵按一下 \[**ctlAlarmClock.vb**\]，然後按一下 \[**檢視程式碼**\]。  
  
2.  找出 `Private blnAlarmSet As Boolean` 陳述式。  緊接著在它的下方，加入下列陳述式。  
  
     \[Visual Basic\]  
  
    ```  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  在頁面底部找出 `End Class` 陳述式。  緊接在 `End Class` 陳述式之前，加入下列程式碼。  
  
     \[Visual Basic\]  
  
    ```  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     加入這個程式碼即完成了數項工作。  `Overrides` 陳述式會引導控制項使用此方法，而不使用繼承自基底控制項的方法。  當此方法被呼叫時，會叫用 `MyBase.Timer1_Tick` 陳述式呼叫它覆寫的方法，確保所有包含在原始控制項中的功能會重新在此控制項中產生。  接著，它會執行其他程式碼併入警示功能。  當警示發生時，將會出現閃爍的標籤控制項，並會聽見嗶聲。  
  
    > [!NOTE]
    >  由於您所要覆寫的是繼承的事件處理常式，所以並不需要使用 `Handles` 關鍵字指定事件。  因為原本就已經連接至事件，  而您的覆寫動作只是將處理常式實作而已。  
  
     您的警示時鐘控制項已接近完成。  最後剩下的是實作將它關閉的方法。  要這麼做，您要加入程式碼至 `lblAlarm_Click` 方法。  
  
##### 若要實作關閉方法  
  
1.  在 \[方案總管\] 中以滑鼠右鍵按一下 \[**ctlAlarmClock.vb**\]，然後按一下 \[**設計工具檢視**\]。  
  
2.  在設計工具中按兩下 \[**lblAlarm**\]。  \[**程式碼編輯器**\] 會開啟至 `Private Sub lblAlarm_Click` 行。  
  
3.  修改此方法，使它類似下列程式碼。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  在 \[**檔案**\] 功能表上，按一下 \[**全部儲存**\] 儲存專案。  
  
### 在表單上使用繼承控制項  
 您可以使用測試基底類別控制項 `ctlClock` 的相同方法來測試繼承控制項：按下 F5 以建置專案，並在 \[**使用者控制項測試容器**\] 中執行控制項。  如需詳細資訊，請參閱 [如何：測試 UserControl 的執行階段行為](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
 若要讓控制項能夠使用，您需要將它裝載在表單上。  和標準複合控制項一樣，繼承的複合控制項無法獨立存在，必須裝載在表單中或其他容器中。  由於 `ctlAlarmClock` 具有較具深度的功能，所以需要其他程式碼來加以測試。  在本程序中，您將撰寫簡單的程式來測試 `ctlAlarmClock` 的功能。  您將撰寫程式碼來設定及顯示 `ctlAlarmClock` 的 `AlarmTime` 屬性，並且測試其繼承功能。  
  
##### 若要建置控制項並將它加入至測試表單  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**ctlClockLib**\]，然後按一下 \[**建置**\]。  
  
2.  在 \[**檔案**\] 功能表上指向 \[**加入**\]，然後按一下 \[**新增專案**\]。  
  
3.  將新的 \[**Windows 應用程式**\] 專案加入至方案，並命名為 `Test`。  
  
     **Test** 專案會加入至 \[方案總管\] 中。  
  
4.  在 \[方案總管\] 中，以滑鼠右鍵按一下 `Test` 專案節點，然後按一下 \[**加入參考**\] 以顯示 \[**加入參考**\] 對話方塊。  
  
5.  按一下標示為 \[**專案**\] 的索引標籤。  \[**ctlClockLib**\] 專案將列在 \[**專案名稱**\] 下。  按兩下 \[**ctlClockLib**\]，將參考加入至測試專案。  
  
6.  在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**測試**\]，然後按一下 \[**建置**\]。  
  
7.  在 \[**工具箱**\] 中展開 \[**ctlClockLib 元件**\] 節點。  
  
8.  按兩下 \[**ctlAlarmClock**\]，將 \[`ctlAlarmClock`\] 執行個體加入至表單中。  
  
9. 在 \[**工具箱**\] 中，找出 \[**DateTimePicker**\] 並按兩下，以便將 <xref:System.Windows.Forms.DateTimePicker> 控制項加入至表單，然後再按兩下 \[**標籤**\]，藉此加入 <xref:System.Windows.Forms.Label> 控制項。  
  
10. 使用滑鼠將控制項放置在表單上方便的地方。  
  
11. 以下列方法設定這些控制項的屬性。  
  
    |控制項|屬性|值|  
    |---------|--------|-------|  
    |`label1`|**文字**|`(空白)`|  
    ||**名稱**|`lblTest`|  
    |`dateTimePicker1`|**名稱**|`dtpTest`|  
    ||**Format**|<xref:System.Windows.Forms.DateTimePickerFormat>|  
  
12. 在設計工具中，按兩下 \[**dtpTest**\]。  
  
     \[**程式碼編輯器**\] 會開啟至 `Private Sub dtpTest_ValueChanged`。  
  
13. 修改程式碼，使它類似下列程式碼。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. 在 \[方案總管\] 中，以滑鼠右鍵按一下 \[**測試**\]，然後按一下 \[**設定為啟始專案**\]。  
  
15. 按一下 \[**偵錯**\] 功能表上的 \[**開始偵錯**\]。  
  
     測試程式啟動。  請注意，`ctlAlarmClock` 控制項中的目前時間會更新，而且啟動時間會顯示在 <xref:System.Windows.Forms.DateTimePicker> 控制項中。  
  
16. 按一下會顯示小時之分鐘數的 <xref:System.Windows.Forms.DateTimePicker>。  
  
17. 使用鍵盤，將分鐘值設定成比 `ctlAlarmClock` 顯示的目前時間快一分鐘。  
  
     `lblTest` 內會顯示警示設定的時間。  等候顯示的時間達到警示設定時間。  當顯示的時間到達警示設定的時間時，嗶聲將響起而 `lblAlarm` 會閃爍。  
  
18. 按一下 `lblAlarm` 以關閉警示。  您現在可以重新設定警示。  
  
     這個逐步解說涵蓋了數個重要概念。  您已經學會如何結合控制項及元件到複合控制項容器中，以建立複合控制項。  也學習到如何加入屬性至控制項，以及如何撰寫程式碼以實作自訂功能。  在上述章節中，則學會了透過繼承方式來擴充指定使用者控制項的功能，以及藉由覆寫方法來變更主方法的功能。  
  
## 請參閱  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [如何：撰寫複合控制項](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)   
 [如何：在選擇工具箱項目對話方塊中顯示控制項](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)   
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)