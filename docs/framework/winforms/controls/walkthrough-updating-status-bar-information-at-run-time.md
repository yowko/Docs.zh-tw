---
title: "逐步解說：在執行階段更新狀態列資訊 | Microsoft Docs"
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
  - "面板, 重新整理狀態列"
  - "狀態列, 重新整理面板"
  - "狀態列, 於執行階段更新"
  - "StatusBar 控制項 [Windows Form], 重新整理面板"
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 逐步解說：在執行階段更新狀態列資訊
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> 和 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代和加入功能至 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項；不過 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項會保留以提供回溯相容性和未來使用 \(如果您選擇要使用\)。  
  
 通常程式會根據應用程式狀態或其他使用者互動的變更，在執行時期為您呼叫以便動態更新狀態列面板的內容。  這常用來通知使用者已啟用如 CAPS LOCK、NUM LOCK 或 SCROLL LOCK 之類的按鍵，或是提供日期或時鐘以方便參考。  
  
 在下列範例，您將使用 <xref:System.Windows.Forms.StatusBarPanel> 類別的執行個體，裝載 \(Host\) 鬧鐘。  
  
### 如需取得更新用的狀態列  
  
1.  建立新的 Windows Form。  
  
2.  在表單中加入 <xref:System.Windows.Forms.StatusBar> 控制項。  如需詳細資訊，請參閱 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
3.  將狀態列面板加入至您的 <xref:System.Windows.Forms.StatusBar> 控制項。  如需詳細資訊，請參閱 [如何：將面板加入至 StatusBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)。  
  
4.  加入至您表單 <xref:System.Windows.Forms.StatusBar> 的控制項，設定 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> 屬性為 `true`。  
  
5.  將 Windows Form <xref:System.Windows.Forms.Timer> 元件加入至表單。  
  
    > [!NOTE]
    >  Windows Form <xref:System.Windows.Forms.Timer?displayProperty=fullName> 元件是設計來在 Windows Form 環境中使用的。  如需適用於伺服器環境的計時器，請參閱[Introduction to Server\-Based Timers](http://msdn.microsoft.com/zh-tw/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。  
  
6.  將 <xref:System.Windows.Forms.Timer.Enabled%2A> 屬性設定為 `true`。  
  
7.  將 <xref:System.Windows.Forms.Timer> 的 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性設定為 30000。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.Timer> 元件的 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性設定為 30 秒 \(30,000 毫秒\)，以確保顯示的時間會反映精確的時間。  
  
### 若要實作計時器來更新狀態列  
  
1.  將下列程式碼插入 <xref:System.Windows.Forms.Timer> 元件的事件處理常式來更新 <xref:System.Windows.Forms.StatusBar> 控制項的面板。  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     這時您將執行應用程式並觀察在狀態列面板中執行的時鐘。  
  
### 若要測試應用程式  
  
1.  偵錯應用程式並按 F5 來執行它。  如需偵錯的詳細資訊，請參閱 [Visual Studio 偵錯](../Topic/Debugging%20in%20Visual%20Studio.md)。  
  
    > [!NOTE]
    >  時鐘大約需要 30 秒才會顯示在狀態列。  這是為了盡可能取得最準確的時間。  相反地，若要讓時鐘快點出現，可以將上述步驟 7 中設定的 <xref:System.Windows.Forms.Timer.Interval%2A> 屬性值縮小。  
  
## 請參閱  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [如何：將面板加入至 StatusBar 控制項](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)   
 [如何：判斷在 Windows Form StatusBar 控制項中按下的面板](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)   
 [StatusBar 控制項概觀](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)