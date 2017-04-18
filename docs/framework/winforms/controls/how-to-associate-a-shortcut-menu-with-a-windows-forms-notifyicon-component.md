---
title: "如何：將捷徑功能表與 Windows Form NotifyIcon 元件關聯 | Microsoft Docs"
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
  - "內容功能表, 背景處理序"
  - "NotifyIcon 元件, 連接快速鍵功能表"
  - "捷徑功能表, 背景處理序"
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：將捷徑功能表與 Windows Form NotifyIcon 元件關聯
> [!NOTE]
>  雖然 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 會取代和加入功能至舊版的 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 控制項，但是會保留 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 以提供回溯相容性 \(Backward Compatibility\) 和未來使用 \(如果您選擇要用\)。  
  
 <xref:System.Windows.Forms.NotifyIcon> 元件會在工作列的狀態告知區域中顯示圖示。  通常，應用程式允許您以滑鼠右鍵按一下這個圖示，將命令傳送至它所代表的應用程式。  您可將 <xref:System.Windows.Forms.ContextMenu> 元件與 <xref:System.Windows.Forms.NotifyIcon> 元件相關聯，藉此將這個功能加入至應用程式。  
  
> [!NOTE]
>  如果您希望應用程式在啟動時最小化，同時在工具列中顯示 <xref:System.Windows.Forms.NotifyIcon> 元件的執行個體，請將主要表單的 <xref:System.Windows.Forms.Form.WindowState%2A> 屬性設定為 <xref:System.Windows.Forms.FormWindowState>，並確定 <xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性是設定為 `true`。  
  
### 若要在設計階段將捷徑功能表與 NotifyIcon 元件相關聯  
  
1.  將 <xref:System.Windows.Forms.NotifyIcon> 元件加入至表單，並設定重要的屬性，例如 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性。  
  
     如需詳細資訊，請參閱 [如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)。  
  
2.  將 <xref:System.Windows.Forms.ContextMenu> 元件加入至 Windows Form。  
  
     將功能表項目加入至捷徑功能表，此功能表代表您希望在執行階段可以使用的命令。  這也是將功能表增強功能加入至這些功能表項目 \(如便捷鍵\) 的好時機。  
  
3.  將 <xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> 屬性設定為您加入的捷徑功能表。  
  
     在設定這個屬性後，當使用者按一下工作列上的圖示時，就會顯示捷徑功能表。  
  
### 若要以程式設計方式將捷徑功能表與 NotifyIcon 元件相關聯  
  
1.  建立 <xref:System.Windows.Forms.NotifyIcon> 類別 \(Class\) 和 <xref:System.Windows.Forms.ContextMenu> 類別的執行個體，使用應用程式需要的任何屬性設定 \(<xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性，以及 <xref:System.Windows.Forms.ContextMenu> 元件的功能表物件\)。  
  
2.  將 <xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> 屬性設定為您加入的捷徑功能表。  
  
     在設定這個屬性後，當使用者按一下工作列上的圖示時，就會顯示捷徑功能表。  
  
    > [!NOTE]
    >  下列程式碼範例建立基本的功能表結構。  您將需要自訂功能表選擇，以符合您正在開發的應用程式。  此外，需要撰寫程式碼以處理這些功能表項目的 <xref:System.Windows.Forms.MenuItem.Click> 事件。  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _   
          (System.Environment.GetFolderPath _   
          (System.Environment.SpecialFolder.Personal)  _   
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
>  您必須初始化 `notifyIcon1` 和 `contextMenu1,`，可藉由在表單的建構函式中加入下列陳述式的方式完成這項作業：  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## 請參閱  
 <xref:System.Windows.Forms.NotifyIcon>   
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>   
 [如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)   
 [NotifyIcon 元件](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)   
 [NotifyIcon 元件概觀](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)