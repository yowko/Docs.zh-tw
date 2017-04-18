---
title: "如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TrayIcon"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "圖示, 加入到工作列"
  - "NotifyIcon 元件"
  - "狀態區圖示"
  - "工作列, 加入圖示"
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar
Windows Form <xref:System.Windows.Forms.NotifyIcon> 元件會在工作列的狀態告知區域中顯示單一圖示。  若要在狀態區中顯示多個圖示，表單中必須有多個 <xref:System.Windows.Forms.NotifyIcon> 元件。  若要設定控制項顯示的圖示，請使用 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 屬性。  您也可以在 <xref:System.Windows.Forms.NotifyIcon.DoubleClick> 事件處理常式中撰寫程式碼，以便在使用者按兩下圖示時執行某些工作。  例如，您可以為使用者顯示對話方塊，以便設定圖示所代表的背景處理序 \(Process\)。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon> 元件只供通知之用，可警告使用者有動作或事件已經發生，或是某種狀態有所變更。  您應使用功能表、工具列和其他做為與應用程式標準互動的使用者介面項目。  
  
### 若要設定圖示  
  
1.  將值指派給 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 屬性。  這個值必須是 `System.Drawing.Icon` 型別，並可自 .ico 檔案載入。  您可以在程式碼中指定圖示檔或按一下 \[**屬性**\] 視窗中 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 屬性旁的省略按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)，然後在 \[**開啟**\] 對話方塊中選取檔案。  
  
2.  將 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性設定為 `true`。  
  
3.  將 <xref:System.Windows.Forms.NotifyIcon.Text%2A> 屬性設為適當的工具提示字串。  
  
     在下列的範例程式碼中，為圖示位置所設定的路徑是 \[**我的文件**\] 資料夾。  這個位置的使用，是因為您可假設大部分執行 Windows 作業系統的電腦，都會包含這個資料夾。  選擇這個位置也可讓使用者以最基本的系統存取層級，便可安全執行應用程式。  下列範例需要已加入 <xref:System.Windows.Forms.NotifyIcon> 控制項的表單。  它還需要名為 `Icon.ico` 的圖示檔。  
  
     \[Visual Basic\]  
  
    ```  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
  
    ```  
  
     \[C\#\]  
  
    ```  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    notifyIcon1.Icon =   
       new System.Drawing.Icon (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Icon.ico");  
    notifyIcon1.Visible = true;  
    notifyIcon1.Text = "Antivirus program";  
  
    ```  
  
     \[cpp\]  
  
    ```  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    notifyIcon1->Icon = gcnew   
       System::Drawing::Icon(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Icon.ico"));  
    notifyIcon1->Visible = true;  
    notifyIcon1->Text = "Antivirus program";  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.NotifyIcon>   
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>   
 [如何：將捷徑功能表與 Windows Form NotifyIcon 元件關聯](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)   
 [NotifyIcon 元件](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)   
 [NotifyIcon 元件概觀](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)