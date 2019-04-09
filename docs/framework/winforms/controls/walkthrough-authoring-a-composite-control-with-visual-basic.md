---
title: 逐步解說：使用 Visual Basic 撰寫複合控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: ed3a7dc23050412082fb10fabf6b1d5a4507973e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186104"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a>逐步解說：使用 Visual Basic 撰寫複合控制項
複合控制項提供可以建立及重複使用自訂圖形介面的方法。 複合控制項基本上是具有視覺表示的元件。 因此，它可能包含一或多個 Windows Forms 控制項、元件或程式碼區塊，可以藉由驗證使用者輸入、修改顯示屬性，或執行作者需要的其他工作來擴充功能。 複合控制項可以放在 Windows Forms 上，與其他控制項的方式相同。 在本逐步解說的第一個部分中，您可以建立簡單的複合控制項，稱為 `ctlClock`。 在逐步解說的第二個部分中，您透過繼承擴充 `ctlClock` 的功能。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="creating-the-project"></a>建立專案  
 當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。  
  
#### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>建立 ctlClockLib 控制項程式庫和 ctlClock 控制項  
  
1.  在 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]，開啟 [新增專案] 對話方塊。  
  
2.  從 Visual Basic 專案的清單中，選取**Windows 控制項程式庫**專案範本中，輸入`ctlClockLib`中**名稱**方塊，然後再按一下**確定**。  
  
     專案名稱，`ctlClockLib`，預設也會指派給根命名空間。 根命名空間是用來限定組件中的元件名稱。 例如，如果兩個組件提供元件，名為`ctlClock`，您可以指定您`ctlClock`元件使用 `ctlClockLib.ctlClock.`  
  
3.  以滑鼠右鍵按一下 [方案總管] 中的 [UserControl1.vb]，然後按一下 [重新命名]。 將檔案名稱變更為 `ctlClock.vb`。 當系統詢問您是否要重新命名程式碼元素 "UserControl1" 的所有參考時，按一下 [是]按鈕。  
  
    > [!NOTE]
    >  根據預設，複合控制項是繼承自<xref:System.Windows.Forms.UserControl>系統所提供的類別。 <xref:System.Windows.Forms.UserControl>類別提供所有複合控制項，所需的功能，並會實作標準方法和屬性。  
  
4.  在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。  
  
## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>將 Windows 控制項和元件新增至複合控制項  
 視覺化介面是複合控制項不可或缺的一部分。 這個視覺化介面是藉由將一或多個 Windows 控制項新增至設計工具介面來實作。 在下列示範中，您將 Windows 控制項合併到您的複合控制項，並且撰寫程式碼來實作功能。  
  
#### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>將標籤和計時器新增至複合控制項  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClock.vb]，然後按一下 [檢視表設計工具]。  
  
2.  在 [工具箱] 中展開 [通用控制項] 節點，然後再按兩下 [標籤]。  
  
     A<xref:System.Windows.Forms.Label>控制項，名為`Label1`新增至您的控制項設計工具介面上。  
  
3.  在設計工具中，按一下 [Label1]。 在 [屬性] 視窗中設定下列屬性。  
  
    |屬性|變更為|  
    |--------------|---------------|  
    |**名稱**|`lblDisplay`|  
    |**文字**|`(blank space)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  在 [工具箱] 中展開 [元件] 節點，然後再按兩下 [計時器]。  
  
     因為<xref:System.Windows.Forms.Timer>是元件，它有在執行階段沒有視覺表示法。 因此，它不會與控制項一起出現在設計工具介面上，而是會出現在元件設計工具中 (位於設計工具介面底部的系統匣)。  
  
5.  在元件設計工具中，按一下  **Timer1**，然後將<xref:System.Windows.Forms.Timer.Interval%2A>屬性設`1000`而<xref:System.Windows.Forms.Timer.Enabled%2A>屬性設`True`。  
  
     <xref:System.Windows.Forms.Timer.Interval%2A>屬性會控制計時器元件走動的頻率。 每次 `Timer1` 走動時，它會執行 `Timer1_Tick` 事件中的程式碼。 間隔代表刻度之間的毫秒數。  
  
6.  在元件設計工具中，按兩下 [Timer1] 以前往 `ctlClock` 的 `Timer1_Tick` 事件。  
  
7.  修改程式碼，使它類似下列程式碼範例。 請確定將存取修飾詞從 `Private` 變更為 `Protected`。  
  
    ```vb  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     此程式碼會造成目前時間在 `lblDisplay` 中顯示。 因為 `Timer1` 的間隔設為 `1000`，每一千毫秒便會發生此事件，因此每秒會更新目前時間。  
  
8.  修改方法為可覆寫。 如需詳細資訊，請參閱以下的「從使用者控制項繼承」一節。  
  
    ```vb  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. 在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。  
  
## <a name="adding-properties-to-the-composite-control"></a>將屬性新增至複合控制項  
 您的時鐘控制項現在會封裝<xref:System.Windows.Forms.Label>控制項和<xref:System.Windows.Forms.Timer>元件，各有其自己的固有的屬性集。 雖然這些控制項的個別屬性無法供控制項的後續使用者存取，但是您可以建立並公開自訂屬性，方法是撰寫適當的程式碼區塊。 在下列程序中，您會將屬性新增至控制項，讓使用者變更背景與文字的色彩。  
  
#### <a name="to-add-a-property-to-your-composite-control"></a>若要將屬性新增至複合控制項  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClock.vb]，然後按一下 [檢視程式碼]。  
  
     控制項的程式碼編輯器隨即開啟。  
  
2.  尋找 `Public Class ctlClock` 陳述式。 在其下輸入下列程式碼。  
  
    ```vb  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     這些陳述式會建立私用變數，您將用來儲存您即將建立之屬性的值。  
  
3.  在 步驟 2 的變數宣告底下插入下列程式碼。  
  
    ```vb  
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
  
     上述程式碼會製作兩個自訂屬性，`ClockForeColor` 和 `ClockBackColor`，藉由叫用 `Property` 陳述式，以供此控制項的後續使用者使用。 `Get` 和 `Set` 陳述式提供屬性值的儲存和擷取，以及用來實作適合該屬性之功能的程式碼。  
  
4.  在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。  
  
## <a name="testing-the-control"></a>測試控制項  
 控制項不是獨立專案；它們必須裝載在容器中。 測試控制項的執行階段行為，並且使用 **UserControl 測試容器**執行其屬性。 如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
#### <a name="to-test-your-control"></a>若要測試控制項  
  
1.  按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。  
  
2.  在測試容器的屬性方格中，選取 `ClockBackColor` 屬性，然後按一下下拉箭號以顯示色彩調色盤。  
  
3.  按一下它以選擇色彩。  
  
     控制項的背景色彩會變更為您所選取的色彩。  
  
4.  使用類似的一連串事件，確認 `ClockForeColor` 屬性是否如預期運作。  
  
5.  按一下 [關閉] 以關閉 **UserControl 測試容器**。  
  
     在本節和先前的章節中，您已經知道元件和 Windows 控制項如何與程式碼合併並且封裝，以複合控制項的形式提供自訂功能。 您已經了解如何在您的複合控制項中公開屬性，以及如何在完成之後測試您的控制項。 在下一節中，您將學習如何使用 `ctlClock` 做為基底，建構繼承的複合控制項。  
  
## <a name="inheriting-from-a-composite-control"></a>繼承自複合控制項  
 在先前章節中，您了解如何將 Windows 控制項、元件和程式碼合併成可重複使用的複合控制項。 複合控制項現在可以做為建置其他控制項的基底。 從基底類別衍生類別的處理序稱為「繼承」。 在本節中，您將建立稱為 `ctlAlarmClock` 的複合控制項。 這個控制項將會從其父控制項 (`ctlClock`) 衍生。 您將學習藉由覆寫父方法並且新增新方法和屬性，來擴充 `ctlClock` 的功能。  
  
 建立繼承的控制項的第一個步驟是從其父代衍生。 這個動作會建立新的控制項，其中具有父控制項的所有屬性、方法和圖形特性，但是也可以做為基底，以新增新的或修改功能。  
  
#### <a name="to-create-the-inherited-control"></a>若要建立繼承的控制項  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClockLib]，指向 [新增]，然後按一下 [使用者控制項]。  
  
     [新增項目] 對話方塊隨即開啟。  
  
2.  選取**繼承的使用者控制項**範本。  
  
3.  在 [名稱] 方塊中，輸入 `ctlAlarmClock.vb` 然後按一下 [新增]。  
  
     [繼承選取器] 對話方塊隨即出現。  
  
4.  在 [元件名稱] 底下，按兩下 [ctlClock]。  
  
5.  在 [方案總管] 中，瀏覽目前的專案。  
  
    > [!NOTE]
    >  名為 **ctlAlarmClock.vb** 的檔案已新增至目前的專案。  
  
### <a name="adding-the-alarm-properties"></a>新增警示屬性  
 屬性會以新增至複合控制項的相同方式，新增至繼承的控制項。 您現在會使用屬性宣告語法將兩個屬性新增至您的控制項︰`AlarmTime`，它將會儲存警示停止之日期和時間的值，以及 `AlarmSet`，它將會指示是否已設定警示。  
  
##### <a name="to-add-properties-to-your-composite-control"></a>若要將屬性新增至複合控制項  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock]，然後按一下 [檢視程式碼]。  
  
2.  尋找 ctlAlarmClock 控制項的類別宣告，它會顯示為 `Public Class ctlAlarmClock`。  在類別宣告中插入下列程式碼。  
  
    ```vb  
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
  
### <a name="adding-to-the-graphical-interface-of-the-control"></a>新增至控制項的圖形化介面  
 繼承的控制項具有視覺化介面，與它所繼承的控制項相同。 它擁有與其父控制項相同的組成控制項，但是無法使用組成控制項的屬性，除非特別公開。 您可以使用新增至任何複合控制項的相同方式，新增至繼承的複合控制項的圖形化介面。 若要繼續新增至警示時鐘的視覺化介面，您要新增標籤控制項，該控制項會在警示響起時閃爍。  
  
##### <a name="to-add-the-label-control"></a>若要新增標籤控制項  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock]，然後按一下 [檢視表設計工具]。  
  
     `ctlAlarmClock` 的設計工具隨即在主視窗中開啟。  
  
2.  按一下 `lblDisplay` (控制項的顯示部分)，並檢視 [屬性] 視窗。  
  
    > [!NOTE]
    >  所有屬性顯示時，它們會以灰色顯示。 這表示這些屬性是 `lblDisplay` 的原生屬性，而且無法修改或在 [屬性] 視窗中存取。 根據預設，包含在複合控制項中的控制項是 `Private`，而且其屬性無法使用任何方法存取。  
  
    > [!NOTE]
    >  如果您想要讓複合控制項的後續使用者可以存取其內部控制項，請將它們宣告為 `Public` 或 `Protected`。 這可讓您使用適當的程式碼，設定及修改包含在複合控制項中的控制項屬性。  
  
3.  新增<xref:System.Windows.Forms.Label>至複合控制項的控制項。  
  
4.  使用滑鼠，拖曳<xref:System.Windows.Forms.Label>正下方的顯示方塊中的控制項。 在 [屬性] 視窗中設定下列屬性。  
  
    |屬性|設定|  
    |--------------|-------------|  
    |**名稱**|`lblAlarm`|  
    |**文字**|**警示 ！**|  
    |**TextAlign**|`MiddleCenter`|  
    |**Visible**|`False`|  
  
### <a name="adding-the-alarm-functionality"></a>新增警示功能  
 在先前的程序中，您新增屬性和控制項，在您的複合控制項中啟用警示功能。 在此程序中，您將會新增程式碼以比較目前時間與警示時間，如果它們相同，則讓警示發出聲響與閃爍。 藉由覆寫 `ctlClock` 的 `Timer1_Tick` 方法，並且將額外程式碼新增至其中，您就可以擴充 `ctlAlarmClock` 的功能，同時保留 `ctlClock` 的所有固有功能。  
  
##### <a name="to-override-the-timer1tick-method-of-ctlclock"></a>若要覆寫 ctlClock 的 Timer1_Tick 方法  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock.vb]，然後按一下 [檢視程式碼]。  
  
2.  尋找 `Private blnAlarmSet As Boolean` 陳述式。 緊接著在其下新增下列陳述式。  
  
    ```vb  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  在頁面底部尋找 `End Class` 陳述式。 緊接在 `End Class` 陳述式之前，新增下列程式碼。  
  
    ```vb  
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
  
     新增這個程式碼會完成幾項工作。 `Overrides` 陳述式會指示控制項使用這個方法來取代繼承自基底控制項的方法。 呼叫這個方法時，它會呼叫它藉由叫用 `MyBase.Timer1_Tick` 陳述式覆寫的方法，確保併入原始控制項的所有功能在此控制項中重現。 接著，它會執行其他程式碼以併入警示功能。 發生警示時，閃爍標籤控制項就會出現，而且會聽到嗶聲。  
  
    > [!NOTE]
    >  因為您正在覆寫繼承的事件處理常式，您不需要指定事件與 `Handles` 關鍵字。 事件已傳入。 您覆寫的所有項目是處理常式的實作。  
  
     警示時鐘控制項已接近完成。 唯一剩餘的事項是實作將它關閉的方式。 若要這樣做，您要將程式碼新增至 `lblAlarm_Click` 方法。  
  
##### <a name="to-implement-the-shutoff-method"></a>若要實作關閉方法  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock.vb]，然後按一下 [檢視表設計工具]。  
  
2.  在設計工具中，按兩下 [lblAlarm]。 [程式碼編輯器] 隨即開啟至 `Private Sub lblAlarm_Click` 行。  
  
3.  修改此方法，使它類似下列程式碼。  
  
    ```vb  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。  
  
### <a name="using-the-inherited-control-on-a-form"></a>在表單上使用繼承的控制項  
 您可以測試繼承的控制項相同的方式測試基底類別的控制項， `ctlClock`:按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。 如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
 若要使用控制項，您必須將它裝載在表單上。 如同標準複合控制項，繼承的複合控制項無法獨立存在，而且必須裝載在表單或其他容器。 由於 `ctlAlarmClock` 有更深入的功能，需要額外的程式碼來進行測試。 在此程序中，您將撰寫一個簡單的程式來測試 `ctlAlarmClock` 的功能。 您將撰寫程式碼以設定及顯示 `ctlAlarmClock` 的 `AlarmTime` 屬性，然後測試其固有功能。  
  
##### <a name="to-build-and-add-your-control-to-a-test-form"></a>若要建置控制項並且新增至測試表單  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClockLib]，然後按一下 [建置]。  
  
2.  在 [檔案]  功能表上，指向 [加入] ，然後按一下 [新增專案] 。  
  
3.  將新的 **Windows 應用程式**專案新增至解決方案，並且將它命名為 `Test`。  
  
     [測試] 專案隨即新增至 [方案總管]。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下 `Test` 專案節點，然後按一下 [加入參考]以顯示 [加入參考] 對話方塊。  
  
5.  按一下標籤為 [專案] 的索引標籤。 專案 **ctlClockLib** 會列在 [專案名稱] 底下。 按兩下 [ctlClockLib] 以將參考新增至測試專案。  
  
6.  在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後按一下 [建置]。  
  
7.  在 [工具箱] 中，展開 [ctlClockLib 元件] 節點。  
  
8.  按兩下 [ctlAlarmClock] 以將 `ctlAlarmClock` 的執行個體新增至表單。  
  
9. 在**工具箱**，找出並按兩下**DateTimePicker**加入<xref:System.Windows.Forms.DateTimePicker>控制項至表單，然後再加入<xref:System.Windows.Forms.Label>按兩下控制項**標籤**.  
  
10. 使用滑鼠將控制項放置在表單上方便的位置。  
  
11. 以下列方式設定這些控制項的屬性。  
  
    |控制項|屬性|值|  
    |-------------|--------------|-----------|  
    |`label1`|**文字**|`(blank space)`|  
    ||**名稱**|`lblTest`|  
    |`dateTimePicker1`|**名稱**|`dtpTest`|  
    ||**格式**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|  
  
12. 在設計工具中，按兩下 [dtpTest]。  
  
     [程式碼編輯器] 隨即開啟至 `Private Sub dtpTest_ValueChanged`。  
  
13. 修改此程式碼，使它類似下列程式碼。  
  
    ```vb  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. 在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後按一下 [設定為啟始專案]。  
  
15. 按一下 [偵錯] 功能表上的 [開始偵錯]。  
  
     測試程式隨即啟動。 請注意，目前的時間在更新`ctlAlarmClock`控制項，以及開始時間所示<xref:System.Windows.Forms.DateTimePicker>控制項。  
  
16. 按一下 <xref:System.Windows.Forms.DateTimePicker>其中會顯示在一小時的分鐘。  
  
17. 使用鍵盤，將分鐘值設定為大於 `ctlAlarmClock` 顯示的目前時間一分鐘。  
  
     警示設定的時間會在 `lblTest` 中顯示。 等候顯示的時間達到警示設定時間。 當顯示的時間達到警示設定時間，則會響起嗶聲且 `lblAlarm` 會閃爍。  
  
18. 按一下 `lblAlarm` 來關閉警示。 您現在可以重設警示。  
  
     本逐步解說涵蓋了數個重要概念。 您已經了解藉由將控制項和元件合併成複合控制項容器，來建立複合控制項。 您已經了解將屬性新增至您的控制項，以及撰寫程式碼來實作自訂功能。 在最後一節中，您會了解透過繼承擴充指定複合控制項的功能，並且藉由覆寫這些方法來變更主方法的功能。  
  
## <a name="see-also"></a>另請參閱

- [各種自訂控制項](varieties-of-custom-controls.md)
- [HOW TO：撰寫複合控制項](how-to-author-composite-controls.md)
- [HOW TO：在 [選擇工具箱項目] 對話方塊中顯示控制項](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
