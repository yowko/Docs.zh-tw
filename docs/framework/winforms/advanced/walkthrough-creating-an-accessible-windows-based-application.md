---
title: "逐步解說：建立 Windows 架構的可及性應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5b52f9f06e2a4adf401367e337be81684f661e1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a>逐步解說：建立 Windows 架構的可及性應用程式
建立協助工具應用程式具有重要的商業含意， 許多政府對於市售軟體訂定有協助工具法規， 而擁有「Windows 憑證」標誌就表示符合有關協助工具的要求。 據估計光是美國便有約三千萬居民受到軟體協助工具的影響，而其中大部分是潛在客戶。  
  
 本逐步解說將提出「Windows 憑證」標誌的五項協助工具需求。 根據這些需求，協助工具應用程式將會：  
  
-   支援 [控制台] 的大小、色彩、字型和輸入設定。 當使用者變更 [控制台] 的設定時，功能表列、標題列、框線和狀態列的大小也會隨著調整。 不需要在這個應用程式中對控制項或程式碼進行其他變更。  
  
-   支援高對比模式。  
  
-   提供具備輔助說明的所有功能鍵盤存取。  
  
-   以視覺呈現和程式設計方式顯示鍵盤焦點的位置。  
  
-   避免只以音效傳達重要資訊。  
  
 如需詳細資訊，請參閱[設計可及性應用程式的資源](/visualstudio/ide/reference/resources-for-designing-accessible-applications)。  
  
 如需支援各種鍵盤配置的資訊，請參閱[開發世界性的應用程式的最佳做法](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)。  
  
## <a name="creating-the-project"></a>建立專案  
 本逐步解說會建立一個接受披薩訂單的應用程式使用者介面， 其中包含輸入顧客名稱的 <xref:System.Windows.Forms.TextBox>、選取披薩尺寸的 <xref:System.Windows.Forms.RadioButton> 群組、選取配料的 <xref:System.Windows.Forms.CheckedListBox>、兩個標示為 [訂購] 和 [取消] 的 Button 控制項，以及一個含有結束命令的功能表。  
  
 使用者會輸入顧客名稱、披薩尺寸和想要的配料。 當使用者按一下 [訂購] 按鈕時，訊息方塊中會顯示訂單摘要及其費用，然後會清除控制項並準備接受下一筆訂單。 當使用者按一下 [取消] 按鈕時，會清除控制項並準備接受下一筆訂單。 當使用者按一下 [結束] 功能表項目時，程式會關閉。  
  
 本逐步解說的重點不在於零售訂單系統的程式碼，而是在於使用者介面的協助工具。 本逐步解說示範數個常用控制項的協助工具功能，這些控制項包括按鈕、選項按鈕、文字方塊和標籤。  
  
#### <a name="to-begin-making-the-application"></a>開始建立應用程式  
  
-   在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 中建立新的 Windows 應用程式。 將專案命名為 **PizzaOrder** (如需詳細資訊，請參閱[建立新的方案和專案](/visualstudio/ide/creating-solutions-and-projects))。  
  
## <a name="adding-the-controls-to-the-form"></a>將控制項加入表單  
 將控制項加入表單時，請注意下列建立協助工具應用程式的方針：  
  
-   設定 <xref:System.Windows.Forms.Control.AccessibleDescription%2A> 和 <xref:System.Windows.Forms.Control.AccessibleName%2A> 屬性。 在這個範例中，<xref:System.Windows.Forms.Control.AccessibleRole%2A> 的預設值便已足夠。 如需協助工具屬性的詳細資訊，請參閱[提供 Windows Forms 上控制項的協助工具資訊](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md)。  
  
-   將字型大小設定為 10 或更大的點數。  
  
    > [!NOTE]
    >  如果您一開始將表單的字型大小設定為 10，之後加入表單之所有控制項的字型大小都將是 10。  
  
-   確定任何描述 TextBox 控制項的 Label 控制項都是依定位順序，緊接著位於 TextBox 控制項之前。  
  
-   使用 "&" 字元，將便捷鍵加入使用者可能想要巡覽之任何控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性。  
  
-   使用 "&" 字元，將便捷鍵加入使用者可能想要巡覽的控制項前面之標籤的 <xref:System.Windows.Forms.Control.Text%2A> 屬性。 將標籤的 <xref:System.Windows.Forms.Label.UseMnemonic%2A> 屬性設定為 `true`如此一來，當使用者按下便捷鍵時，焦點便會設定為定位順序的下一個控制項。  
  
-   將便捷鍵加入所有功能表項目。  
  
#### <a name="to-make-your-windows-application-accessible"></a>讓 Windows 應用程式具備協助功能  
  
-   如下所述將控制項加入表單並設定屬性。 如需如何在表單上排列控制項的模型，請參閱表格下方的圖片。  
  
    |物件|屬性|值|  
    |------------|--------------|-----------|  
    |Form1|AccessibleDescription|訂購表單|  
    ||AccessibleName|訂購表單|  
    ||字型大小|10|  
    ||Text|比薩訂購表單|  
    |PictureBox|名稱|標誌|  
    ||AccessibleDescription|一片披薩|  
    ||AccessibleName|公司標誌|  
    ||Image|任何圖示或點陣圖|  
    |標籤|名稱|companyLabel|  
    ||Text|好吃披薩|  
    ||TabIndex|1|  
    ||AccessibleDescription|公司名稱|  
    ||AccessibleName|公司名稱|  
    ||Backcolor|藍色|  
    ||Forecolor|黃色|  
    ||Font size|18|  
    |標籤|名稱|customerLabel|  
    ||Text|名稱(&N)|  
    ||TabIndex|2|  
    ||AccessibleDescription|顧客名稱標籤|  
    ||AccessibleName|顧客名稱標籤|  
    ||UseMnemonic|True|  
    |TextBox|名稱|customerName|  
    ||Text|(無)|  
    ||TabIndex|3|  
    ||AccessibleDescription|顧客名稱|  
    ||AccessibleName|顧客名稱|  
    |GroupBox|名稱|sizeOptions|  
    ||AccessibleDescription|披薩尺寸選擇|  
    ||AccessibleName|披薩尺寸選擇|  
    ||Text|披薩尺寸|  
    ||TabIndex|4|  
    |RadioButton|名稱|smallPizza|  
    ||Text|小披薩美金 $6.00 元(&S)|  
    ||已核取|True|  
    ||TabIndex|0|  
    ||AccessibleDescription|小披薩|  
    ||AccessibleName|小披薩|  
    |RadioButton|名稱|largePizza|  
    ||Text|大批薩美金 $10.00 元(&L)|  
    ||TabIndex|1|  
    ||AccessibleDescription|大批薩|  
    ||AccessibleName|大批薩|  
    |標籤|名稱|toppingsLabel|  
    ||Text|配料 (每份美金 $0.75 元)(&T)|  
    ||TabIndex|5|  
    ||AccessibleDescription|配料標籤|  
    ||AccessibleName|配料標籤|  
    ||UseMnemonic|True|  
    |CheckedListBox|名稱|配料|  
    ||TabIndex|6|  
    ||AccessibleDescription|可供選擇的配料|  
    ||AccessibleName|可供選擇的配料|  
    ||項目|辣肉腸、臘腸、蘑菇|  
    |按鈕|名稱|順序|  
    ||Text|順序(&O)|  
    ||TabIndex|7|  
    ||AccessibleDescription|合計訂單|  
    ||AccessibleName|訂單總計|  
    |按鈕|名稱|cancel|  
    ||Text|取消(&C)|  
    ||TabIndex|8|  
    ||AccessibleDescription|取消訂單|  
    ||AccessibleName|取消訂單|  
    |MainMenu|名稱|theMainMenu|  
    |MenuItem|名稱|fileCommands|  
    ||Text|檔案(&F)|  
    |MenuItem|名稱|exitApp|  
    ||Text|結束(&X)|  
  
     ![比薩訂購表單](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")  
您的表單看起來會如下所示：  
  
## <a name="supporting-high-contrast-mode"></a>支援高對比模式  
 高對比模式是 Windows 系統的一項設定，使用對比色彩和字型大小以提升可讀性，對於視覺受損的使用者很有幫助。 <xref:System.Windows.Forms.SystemInformation.HighContrast%2A>屬性會提供用來判斷是否設定為高對比模式。  
  
 如果 SystemInformation.HighContrast 為 `true`，應用程式應該：  
  
-   使用系統色彩配置來顯示所有使用者介面項目。  
  
-   藉由視覺提示或音效來傳達原本由色彩傳達的任何資訊。 例如，如果使用紅色字型醒目提示特定清單項目，您也可以將粗體套用至字型，讓使用者透過非色彩提示得知該項目已醒目提示。  
  
-   省略文字後的任何影像或圖樣。  
  
 當應用程式啟動並回應 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 系統事件時，應該會檢查 <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> 的設定。 只要 <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> 的值變更，便會引發 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件。  
  
 在應用程式中，唯一不使用色彩系統設定的項目是 `lblCompanyName`。 <xref:System.Drawing.SystemColors>類別用來為使用者選取系統色彩變更標籤的色彩設定。  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a>有效啟用高對比模式  
  
1.  建立一個方法，將標籤的色彩設定為系統色彩。  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
    private void SetColorScheme()  
    {  
       if (SystemInformation.HighContrast)  
       {  
          companyLabel.BackColor = SystemColors.Window;  
          companyLabel.ForeColor = SystemColors.WindowText;  
       }  
       else  
       {  
          companyLabel.BackColor = Color.Blue;  
          companyLabel.ForeColor = Color.Yellow;  
       }  
    }  
    ```  
  
2.  在表單建構函式 (Visual Basic 中為 `Public Sub New()`，Visual C# 中為 `public class Form1`) 中呼叫 `SetColorScheme` 程序。 若要存取 Visual Basic 中的建構函式，您必須展開標示為 [Windows Forms 設計工具產生的程式碼] 的區域。  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3.  使用適當的簽章建立事件程序，以回應 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件。  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4.  呼叫 `InitializeComponents` 之後，在表單建構函式中新增程式碼，將事件程序與系統事件連結。 這個方法會呼叫 `SetColorScheme` 程序。  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5.  先將程式碼加入表單的 <xref:System.Windows.Forms.Control.Dispose%2A> 方法，再呼叫基底類別的 <xref:System.Windows.Forms.Control.Dispose%2A> 方法，以便在應用程式關閉時釋放事件。 若要存取 Visual Basic 中的 <xref:System.Windows.Forms.Control.Dispose%2A> 方法，您必須展開標示為 [Windows Form 設計工具產生的程式碼] 的區域。  
  
    > [!NOTE]
    >  系統事件程式碼會執行獨立於主應用程式的執行緒。 如果您沒有釋放該事件，即使關閉程式之後，連結至該事件的程式碼仍會繼續執行。  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6.  按 F5 執行應用程式。  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a>透過音效以外的其他方式傳達重要資訊  
 在這個應用程式中，資訊不只以音效傳達。 如果您在應用程式中使用音效，應該也可以使用其他方式來提供資訊。  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a>透過音效以外的其他方式提供資訊  
  
1.  使用 Windows 應用程式開發介面函式 FlashWindow 讓標題列閃爍。 如需如何呼叫 Windows 應用程式開發介面函式的範例，請參閱[逐步解說：呼叫 Windows API](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)。  
  
    > [!NOTE]
    >  使用者可以啟動 Windows 聲音感測服務，當系統音效透過電腦內建喇叭播放時，同時能使視窗閃爍。  
  
2.  在非強制回應視窗中顯示重要資訊，讓使用者可以有所回應。  
  
3.  顯示取得鍵盤焦點的訊息方塊， 但是如果使用者可能會輸入資料，則應避免使用這個方法。  
  
4.  在工作列的狀態通知區域中顯示狀態標記。 如需詳細資訊，請參閱[如何：使用 Windows Forms NotifyIcon 元件將應用程式圖示新增至工作列](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)。  
  
## <a name="testing-the-application"></a>測試應用程式  
 在部署應用程式之前，您應該測試已實作的協助工具功能。  
  
#### <a name="to-test-accessibility-features"></a>測試協助工具功能  
  
1.  若要測試鍵盤存取，請拔除滑鼠，然後只利用鍵盤逐一測試使用者介面中的每一項功能。 請確定所有工作都可以只使用鍵盤執行。  
  
2.  若要測試是否支援高對比，請在 [控制台] 中選擇協助工具選項圖示。 按一下 [顯示] 索引標籤，然後選取 [使用高對比] 核取方塊。 巡覽所有使用者介面項目，確保色彩和字型變更均已正確反映。 同時確保已省略文字後的影像或圖樣。  
  
    > [!NOTE]
    >  Windows NT 4 的 [控制台] 中並沒有協助工具選項圖示。 因此，這個變更 SystemInformation.HighContrast 設定的程序不適用於 Windows NT 4。  
  
3.  另外還有其他工具可以測試應用程式的協助工具。  
  
4.  若要測試鍵盤焦點的顯示，請執行放大鏡 (若要開啟 [放大鏡]，請按一下 [開始] 功能表，然後依序指向 [程式集]、[附屬應用程式] 和 [協助工具]，然後按一下 [放大鏡])。 同時使用鍵盤 Tab 鍵和滑鼠來巡覽使用者介面。 確保 [放大鏡] 正確追蹤所有巡覽。  
  
5.  若要測試螢幕項目的顯示，請執行 [檢查]，然後同時使用滑鼠和 TAB 鍵跳到每個項目。 針對 UI 中的每個物件，確保 [檢查] 視窗的 [名稱]、[狀態]、[角色]、[位置] 和 [值] 欄位所顯示的資訊，對使用者都是有意義的。
