---
title: 逐步解說：使用 Visual C# 撰寫複合控制項
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [C#]
- user controls [Windows Forms], creating with Visual C#
- UserControl class [Windows Forms], walkthroughs
- user controls [C#]
- custom controls [Windows Forms], creating
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
ms.openlocfilehash: 1de1ff4147ddb8cb3316795aefd38622de205a73
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950056"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-c"></a>逐步解說：使用 Visual C 撰寫複合控制項\#

複合控制項提供可以建立及重複使用自訂圖形介面的方法。 複合控制項基本上是具有視覺表示的元件。 因此，它可能包含一或多個 Windows Forms 控制項、元件或程式碼區塊，可以藉由驗證使用者輸入、修改顯示屬性，或執行作者需要的其他工作來擴充功能。 複合控制項可以放在 Windows Forms 上，與其他控制項的方式相同。 在本逐步解說的第一個部分中，您可以建立簡單的複合控制項，稱為 `ctlClock`。 在逐步解說的第二個部分中，您透過繼承擴充 `ctlClock` 的功能。

## <a name="creating-the-project"></a>建立專案

當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a>建立 ctlClockLib 控制項程式庫和 ctlClock 控制項

1. 在 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]，開啟 [新增專案] 對話方塊。

2. 從 Visual C#專案清單中, 選取 [ **Windows Forms 控制項程式庫**] 專案範本, `ctlClockLib`在 [**名稱**] 方塊中輸入, 然後按一下 **[確定]** 。

     專案名稱，`ctlClockLib`，預設也會指派給根命名空間。 根命名空間是用來限定組件中的元件名稱。 例如，如果兩個組件提供元件，名為 `ctlClock`，您可以使用 `ctlClockLib.ctlClock.` 指定您的 `ctlClock` 元件

3. 以滑鼠右鍵按一下 [方案總管] 中的 [UserControl1.cs]，然後按一下 [重新命名]。 將檔案名稱變更為 `ctlClock.cs`。 當系統詢問您是否要重新命名程式碼元素 "UserControl1" 的所有參考時，按一下 [是]按鈕。

    > [!NOTE]
    > 根據預設, 複合控制項會繼承系統所提供<xref:System.Windows.Forms.UserControl>的類別。 類別<xref:System.Windows.Forms.UserControl>提供所有複合控制項所需的功能, 並實作為標準方法和屬性。

4. 在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a>將 Windows 控制項和元件新增至複合控制項

視覺化介面是複合控制項不可或缺的一部分。 這個視覺化介面是藉由將一或多個 Windows 控制項新增至設計工具介面來實作。 在下列示範中，您將 Windows 控制項合併到您的複合控制項，並且撰寫程式碼來實作功能。

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a>將標籤和計時器新增至複合控制項

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClock.cs]，然後按一下 [檢視表設計工具]。

2. 在 [工具箱] 中展開 [通用控制項] 節點，然後再按兩下 [標籤]。

     <xref:System.Windows.Forms.Label> 名`label1`為的控制項會加入至設計工具介面上的控制項。

3. 在設計工具中，按一下 [label1]。 在 [屬性] 視窗中設定下列屬性。

    |屬性|變更為|
    |--------------|---------------|
    |**名稱**|`lblDisplay`|
    |**Text**|`(blank space)`|
    |**TextAlign**|`MiddleCenter`|
    |**Font.Size**|`14`|

4. 在 [工具箱] 中展開 [元件] 節點，然後再按兩下 [計時器]。

     <xref:System.Windows.Forms.Timer>因為是元件, 所以在執行時間沒有視覺表示。 因此，它不會與控制項一起出現在設計工具介面上，而是會出現在 [元件設計工具] 中 (位於設計工具介面底部的系統匣)。

5. 在**元件設計**工具中, 按一下 [ **timer1**], 然後<xref:System.Windows.Forms.Timer.Interval%2A>將屬性`1000`設為<xref:System.Windows.Forms.Timer.Enabled%2A> , 並`true`將屬性設定為。

     屬性會控制<xref:System.Windows.Forms.Timer>元件刻度的頻率。 <xref:System.Windows.Forms.Timer.Interval%2A> 每次 `timer1` 走動時，它會執行 `timer1_Tick` 事件中的程式碼。 間隔代表刻度之間的毫秒數。

6. 在 [元件設計工具] 中，按兩下 [timer1] 以前往 `ctlClock` 的 `timer1_Tick` 事件。

7. 修改程式碼，使它類似下列程式碼範例。 請確定將存取修飾詞從 `private` 變更為 `protected`。

    ```csharp
    protected void timer1_Tick(object sender, System.EventArgs e)
    {
        // Causes the label to display the current time.
        lblDisplay.Text = DateTime.Now.ToLongTimeString();
    }
    ```

     此程式碼會造成目前時間在 `lblDisplay` 中顯示。 因為 `timer1` 的間隔設為 `1000`，每一千毫秒便會發生此事件，因此每秒會更新目前時間。

8. 修改方法為可使用 `virtual`關鍵字覆寫。 如需詳細資訊，請參閱以下的「從使用者控制項繼承」一節。

    ```csharp
    protected virtual void timer1_Tick(object sender, System.EventArgs e)
    ```

9. 在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。

## <a name="adding-properties-to-the-composite-control"></a>將屬性新增至複合控制項

您的時鐘控制項現在會<xref:System.Windows.Forms.Label>封裝控制項<xref:System.Windows.Forms.Timer>和元件, 每個都有自己的一組固有屬性。 雖然這些控制項的個別屬性無法供控制項的後續使用者存取，但是您可以建立並公開自訂屬性，方法是撰寫適當的程式碼區塊。 在下列程序中，您會將屬性新增至控制項，讓使用者變更背景與文字的色彩。

### <a name="to-add-a-property-to-your-composite-control"></a>若要將屬性新增至複合控制項

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClock.cs]，然後按一下 [檢視程式碼]。

     控制項的 [程式碼編輯器] 隨即開啟。

2. 尋找 `public partial class ctlClock` 陳述式。 在左大括號 (`{)` 底下，輸入下列程式碼。

    ```csharp
    private Color colFColor;
    private Color colBColor;
    ```

     這些陳述式會建立私用變數，您將用來儲存您即將建立之屬性的值。

3. 在 步驟 2 的變數宣告底下輸入下列程式碼。

    ```csharp
    // Declares the name and type of the property.
    public Color ClockBackColor
    {
        // Retrieves the value of the private variable colBColor.
        get
        {
            return colBColor;
        }
        // Stores the selected value in the private variable colBColor, and
        // updates the background color of the label control lblDisplay.
        set
        {
            colBColor = value;
            lblDisplay.BackColor = colBColor;
        }
    }
    // Provides a similar set of instructions for the foreground color.
    public Color ClockForeColor
    {
        get
        {
            return colFColor;
        }
        set
        {
            colFColor = value;
            lblDisplay.ForeColor = colFColor;
        }
    }
    ```

     上述程式碼會製作兩個自訂屬性，`ClockForeColor` 和 `ClockBackColor`，以供此控制項的後續使用者使用。 `get` 和 `set` 陳述式提供屬性值的儲存和擷取，以及用來實作適合該屬性之功能的程式碼。

4. 在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。

## <a name="testing-the-control"></a>測試控制項

控制項不是獨立應用程式；它們必須裝載在容器中。 測試控制項的執行階段行為，並且使用 **UserControl 測試容器**執行其屬性。 如需詳細資訊，請參閱[如何：測試 UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)的執行時間行為。

### <a name="to-test-your-control"></a>若要測試控制項

1. 按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。

2. 在測試容器的屬性方格中，尋找 `ClockBackColor` 屬性，然後選取屬性以顯示色彩調色盤。

3. 按一下它以選擇色彩。

     控制項的背景色彩會變更為您所選取的色彩。

4. 使用類似的一連串事件，確認 `ClockForeColor` 屬性是否如預期運作。

     在本節和先前的章節中，您已經知道元件和 Windows 控制項如何與程式碼合併並且封裝，以複合控制項的形式提供自訂功能。 您已經了解如何在您的複合控制項中公開屬性，以及如何在完成之後測試您的控制項。 在下一節中，您將學習如何使用 `ctlClock` 做為基底，建構繼承的複合控制項。

## <a name="inheriting-from-a-composite-control"></a>繼承自複合控制項

在先前章節中，您了解如何將 Windows 控制項、元件和程式碼合併成可重複使用的複合控制項。 複合控制項現在可以做為建置其他控制項的基底。 從基底類別衍生類別的處理序稱為「繼承」。 在本節中，您將建立稱為 `ctlAlarmClock` 的複合控制項。 這個控制項將會從其父控制項 (`ctlClock`) 衍生。 您將學習藉由覆寫父方法並且新增新方法和屬性，來擴充 `ctlClock` 的功能。

建立繼承的控制項的第一個步驟是從其父代衍生。 這個動作會建立新的控制項，其中具有父控制項的所有屬性、方法和圖形特性，但是也可以做為基底，以新增新的或修改功能。

### <a name="to-create-the-inherited-control"></a>若要建立繼承的控制項

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClockLib]，指向 [新增]，然後按一下 [使用者控制項]。

     [新增項目] 對話方塊隨即開啟。

2. 選取**繼承的使用者控制項**範本。

3. 在 [名稱] 方塊中，輸入 `ctlAlarmClock.cs` 然後按一下 [新增]。

     [繼承選取器] 對話方塊隨即出現。

4. 在 [元件名稱] 底下，按兩下 [ctlClock]。

5. 在 [方案總管] 中，瀏覽目前的專案。

    > [!NOTE]
    > 名為 **ctlAlarmClock.cs** 的檔案已新增至目前的專案。

### <a name="adding-the-alarm-properties"></a>新增警示屬性

屬性會以新增至複合控制項的相同方式，新增至繼承的控制項。 您現在會使用屬性宣告語法將兩個屬性新增至您的控制項︰`AlarmTime`，它將會儲存警示停止之日期和時間的值，以及 `AlarmSet`，它將會指示是否已設定警示。

#### <a name="to-add-properties-to-your-composite-control"></a>若要將屬性新增至複合控制項

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock]，然後按一下 [檢視程式碼]。

2. 尋找 `public class` 陳述式。 請注意，您的控制項繼承自`ctlClockLib.ctlClock`。 在左大括號 (`{)` 陳述式底下，輸入下列程式碼。

    ```csharp
    private DateTime dteAlarmTime;
    private bool blnAlarmSet;
    // These properties will be declared as public to allow future
    // developers to access them.
    public DateTime AlarmTime
    {
        get
        {
            return dteAlarmTime;
        }
        set
        {
            dteAlarmTime = value;
        }
    }
    public bool AlarmSet
    {
        get
        {
            return blnAlarmSet;
        }
        set
        {
            blnAlarmSet = value;
        }
    }
    ```

### <a name="adding-to-the-graphical-interface-of-the-control"></a>新增至控制項的圖形化介面

繼承的控制項具有視覺化介面，與它所繼承的控制項相同。 它擁有與其父控制項相同的組成控制項，但是無法使用組成控制項的屬性，除非特別公開。 您可以使用新增至任何複合控制項的相同方式，新增至繼承的複合控制項的圖形化介面。 若要繼續新增至警示時鐘的視覺化介面，您要新增標籤控制項，該控制項會在警示響起時閃爍。

#### <a name="to-add-the-label-control"></a>若要新增標籤控制項

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock]，然後按一下 [檢視表設計工具]。

     `ctlAlarmClock` 的設計工具隨即在主視窗中開啟。

2. 按一下控制項的顯示部分，並檢視 [屬性] 視窗。

    > [!NOTE]
    > 所有屬性顯示時，它們會以灰色顯示。 這表示這些屬性是 `lblDisplay` 的原生屬性，而且無法修改或在 [屬性] 視窗中存取。 根據預設，包含在複合控制項中的控制項是 `private`，而且其屬性無法使用任何方法存取。

    > [!NOTE]
    > 如果您想要讓複合控制項的後續使用者可以存取其內部控制項，請將它們宣告為 `public` 或 `protected`。 這可讓您使用適當的程式碼，設定及修改包含在複合控制項中的控制項屬性。

3. <xref:System.Windows.Forms.Label>將控制項新增至您的複合控制項。

4. 使用滑鼠, 將<xref:System.Windows.Forms.Label>控制項拖曳到顯示方塊的正下方。 在 [屬性] 視窗中設定下列屬性。

    |屬性|設定|
    |--------------|-------------|
    |**名稱**|`lblAlarm`|
    |**Text**|**Alarm!**|
    |**TextAlign**|`MiddleCenter`|
    |**可見**|`false`|

### <a name="adding-the-alarm-functionality"></a>新增警示功能

在先前的程序中，您新增屬性和控制項，在您的複合控制項中啟用警示功能。 在此程序中，您將會新增程式碼以比較目前時間與警示時間，如果它們相同，則讓警示閃爍。 藉由覆寫 `ctlClock` 的 `timer1_Tick` 方法，並且將額外程式碼新增至其中，您就可以擴充 `ctlAlarmClock` 的功能，同時保留 `ctlClock` 的所有固有功能。

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a>若要覆寫 ctlClock 的 timer1_Tick 方法

1. 在 [程式碼編輯器] 中，尋找 `private bool blnAlarmSet;` 陳述式。 緊接著在其下新增下列陳述式。

    ```csharp
    private bool blnColorTicker;
    ```

2. 在 [程式碼編輯器] 中，在類別結尾尋找右大括號 (`})`。 緊接在大括號之前，新增下列程式碼。

    ```csharp
    protected override void timer1_Tick(object sender, System.EventArgs e)
    {
        // Calls the Timer1_Tick method of ctlClock.
        base.timer1_Tick(sender, e);
        // Checks to see if the alarm is set.
        if (AlarmSet == false)
            return;
        else
            // If the date, hour, and minute of the alarm time are the same as
            // the current time, flash an alarm.
        {
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)
            {
                // Sets lblAlarmVisible to true, and changes the background color based on
                // the value of blnColorTicker. The background color of the label
                // will flash once per tick of the clock.
                lblAlarm.Visible = true;
                if (blnColorTicker == false)
                {
                    lblAlarm.BackColor = Color.Red;
                    blnColorTicker = true;
                }
                else
                {
                    lblAlarm.BackColor = Color.Blue;
                    blnColorTicker = false;
                }
            }
            else
            {
                // Once the alarm has sounded for a minute, the label is made
                // invisible again.
                lblAlarm.Visible = false;
            }
        }
    }
    ```

     新增這個程式碼會完成幾項工作。 `override` 陳述式會指示控制項使用這個方法來取代繼承自基底控制項的方法。 呼叫這個方法時，它會呼叫它藉由叫用 `base.timer1_Tick` 陳述式覆寫的方法，確保併入原始控制項的所有功能在此控制項中重現。 接著，它會執行其他程式碼以併入警示功能。 發生警示時，閃爍標籤控制項就會出現。

     警示時鐘控制項已接近完成。 唯一剩餘的事項是實作將它關閉的方式。 若要這樣做，您要將程式碼新增至 `lblAlarm_Click` 方法。

#### <a name="to-implement-the-shutoff-method"></a>若要實作關閉方法

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock.cs]，然後按一下 [檢視表設計工具]。

     設計工具隨即開啟。

2. 將按鈕新增至控制項。 將按鈕的屬性設定如下。

    |屬性|值|
    |--------------|-----------|
    |**名稱**|`btnAlarmOff`|
    |**Text**|**停用警示**|

3. 在設計工具中，按兩下 [btnAlarmOff]。

     [程式碼編輯器] 隨即開啟至 `private void btnAlarmOff_Click` 行。

4. 修改此方法，使它類似下列程式碼。

    ```csharp
    private void btnAlarmOff_Click(object sender, System.EventArgs e)
    {
        // Turns off the alarm.
        AlarmSet = false;
        // Hides the flashing label.
        lblAlarm.Visible = false;
    }
    ```

5. 在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。

### <a name="using-the-inherited-control-on-a-form"></a>在表單上使用繼承的控制項

您可以依照測試基類控制項`ctlClock`的相同方式來測試繼承的控制項:按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。 如需詳細資訊，請參閱[如何：測試 UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)的執行時間行為。

若要使用控制項，您必須將它裝載在表單上。 如同標準複合控制項，繼承的複合控制項無法獨立存在，而且必須裝載在表單或其他容器。 由於 `ctlAlarmClock` 有更深入的功能，需要額外的程式碼來進行測試。 在此程序中，您將撰寫一個簡單的程式來測試 `ctlAlarmClock` 的功能。 您將撰寫程式碼以設定及顯示 `ctlAlarmClock` 的 `AlarmTime` 屬性，然後測試其固有功能。

#### <a name="to-build-and-add-your-control-to-a-test-form"></a>若要建置控制項並且新增至測試表單

1. 在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClockLib]，然後按一下 [建置]。

2. 將新的 **Windows 應用程式**專案新增至解決方案，並且將它命名為 `Test`。

3. 在 [方案總管] 中，以滑鼠右鍵按一下測試專案的 [參考] 節點。 按一下 [加入參考]以顯示 [加入參考] 對話方塊。 按一下標籤為 [專案] 的索引標籤。 您的 `ctlClockLib` 專案會列在 [專案名稱] 底下。 按兩下專案以將參考新增至測試專案。

4. 在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後按一下 [建置]。

5. 在 [工具箱] 中，展開 [ctlClockLib 元件] 節點。

6. 按兩下 [ctlAlarmClock] 以將 `ctlAlarmClock` 的複本新增至表單。

7. 在 [**工具箱**] 中, 找出並按兩下 [ **DateTimePicker** ] <xref:System.Windows.Forms.DateTimePicker>將控制項新增至<xref:System.Windows.Forms.Label>表單, 然後按兩下 [**標籤**] 來加入控制項。

8. 使用滑鼠將控制項放置在表單上方便的位置。

9. 以下列方式設定這些控制項的屬性。

    |控制項|屬性|值|
    |-------------|--------------|-----------|
    |`label1`|**Text**|`(blank space)`|
    ||**名稱**|`lblTest`|
    |`dateTimePicker1`|**名稱**|`dtpTest`|
    ||**格式**|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

10. 在設計工具中，按兩下 [dtpTest]。

     [程式碼編輯器] 隨即開啟至 `private void dtpTest_ValueChanged`。

11. 修改此程式碼，使它類似下列程式碼。

    ```csharp
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)
    {
        ctlAlarmClock1.AlarmTime = dtpTest.Value;
        ctlAlarmClock1.AlarmSet = true;
        lblTest.Text = "Alarm Time is " +
            ctlAlarmClock1.AlarmTime.ToShortTimeString();
    }
    ```

12. 在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後按一下 [設定為啟始專案]。

13. 按一下 [偵錯] 功能表上的 [開始偵錯]。

     測試程式隨即啟動。 請注意, `ctlAlarmClock`控制項中的目前時間已更新, 而且開始時間會顯示<xref:System.Windows.Forms.DateTimePicker>在控制項中。

14. 按一下顯示<xref:System.Windows.Forms.DateTimePicker>該小時分鐘數的。

15. 使用鍵盤，將分鐘值設定為大於 `ctlAlarmClock` 顯示的目前時間一分鐘。

     警示設定的時間會在 `lblTest` 中顯示。 等候顯示的時間達到警示設定時間。 當顯示的時間達到警示設定時間，則 `lblAlarm` 會閃爍。

16. 按一下 `btnAlarmOff` 來關閉警示。 您現在可以重設警示。

     本逐步解說涵蓋了數個重要概念。 您已經了解藉由將控制項和元件合併成複合控制項容器，來建立複合控制項。 您已經了解將屬性新增至您的控制項，以及撰寫程式碼來實作自訂功能。 在最後一節中，您會了解透過繼承擴充指定複合控制項的功能，並且藉由覆寫這些方法來變更主方法的功能。

## <a name="see-also"></a>另請參閱

- [各種自訂控制項](varieties-of-custom-controls.md)
- [如何：在 [選擇工具箱專案] 對話方塊中顯示控制項](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [逐步解說：使用視覺效果從 Windows Forms 控制項繼承C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
