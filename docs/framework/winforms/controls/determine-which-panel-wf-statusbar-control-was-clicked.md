---
title: "如何：判斷在 Windows Form StatusBar 控制項中按下的面板 | Microsoft Docs"
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
  - "Panel 控制項 [Windows Form], 判斷按下"
  - "PanelClick 事件, 判斷按下的面板"
  - "面板, 判斷按下"
  - "狀態列, 判斷按下的面板"
  - "StatusBar 控制項 [Windows Form], 程式碼面板 Click 事件"
  - "StatusBar 控制項 [Windows Form], 判斷按下的面板"
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：判斷在 Windows Form StatusBar 控制項中按下的面板
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> 和 <xref:System.Windows.Forms.ToolStripStatusLabel> 控制項會取代和加入功能至 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項；不過 <xref:System.Windows.Forms.StatusBar> 和 <xref:System.Windows.Forms.StatusBarPanel> 控制項會保留以提供回溯相容性和未來使用 \(如果您選擇要使用\)。  
  
 若要程式化 [StatusBar 控制項](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) 控制項來回應使用者按滑鼠的動作，要在 <xref:System.Windows.Forms.StatusBar.PanelClick> 事件中使用 case 陳述式。  這個事件包含 panel 引數，其中又包含所按的 <xref:System.Windows.Forms.StatusBarPanel> 物件之參考。  您可使用這個參考來判斷所按面板的索引，然後依此進行程式設計。  
  
> [!NOTE]
>  確認 <xref:System.Windows.Forms.StatusBar> 控制項的 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> 屬性已設定為 `true`。  
  
### 若要判斷按下的是哪個面板  
  
1.  在 <xref:System.Windows.Forms.StatusBar.PanelClick> 事件處理常式中，使用 `Select Case` \(在 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 中\) 或者 `switch case` \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 或 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 陳述式，藉由驗證檢查事件引數中按下面板的索引，以決定哪個面板被滑鼠按了一下。  
  
     下列程式碼範例需要有表單、<xref:System.Windows.Forms.StatusBar> 控制項、`StatusBar1`，以及兩個 <xref:System.Windows.Forms.StatusBarPanel> 物件 \(`StatusBarPanel1`  和 `StatusBarPanel2`\)。  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,   
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) 將下列程式碼加入表單的建構函式以註冊事件處理常式。  
  
    ```csharp  
    this.statusBar1.PanelClick += new   
       System.Windows.Forms.StatusBarPanelClickEventHandler   
       (this.statusBar1_PanelClick);  
  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [如何：設定狀態列面板的大小](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)   
 [逐步解說：在執行階段更新狀態列資訊](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)   
 [StatusBar 控制項概觀](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)