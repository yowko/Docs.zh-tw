---
title: 將快顯功能表與 NotifyIcon 元件關聯
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: 15a4a06726de348745e5eef03217d693db496a42
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182257"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>如何：將捷徑功能表與 Windows Form NotifyIcon 元件關聯
> [!NOTE]
> 以及<xref:System.Windows.Forms.MenuStrip>將<xref:System.Windows.Forms.ContextMenuStrip>功能替換和添加到早期版本的<xref:System.Windows.Forms.MainMenu><xref:System.Windows.Forms.ContextMenu>和 控制項，<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>保留用於向後相容性和將來使用（如果選擇）。  
  
 元件<xref:System.Windows.Forms.NotifyIcon>在工作列的狀態通知區域中顯示一個圖示。 通常，應用程式允許您按右鍵此圖示，將命令發送到它所代表的應用程式。 通過將<xref:System.Windows.Forms.ContextMenu>元件與<xref:System.Windows.Forms.NotifyIcon>元件關聯，可以將此功能添加到應用程式中。  
  
> [!NOTE]
> 如果希望在啟動時最小化應用程式，<xref:System.Windows.Forms.NotifyIcon>同時在工作列中顯示元件的實例，請將主表單的屬性<xref:System.Windows.Forms.Form.WindowState%2A>設置為<xref:System.Windows.Forms.FormWindowState.Minimized>，並確保<xref:System.Windows.Forms.NotifyIcon>元件的屬性<xref:System.Windows.Forms.NotifyIcon.Visible%2A>設置為`true`。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>在設計時將快顯功能表與 NotifyIcon 元件關聯  
  
1. 向表單<xref:System.Windows.Forms.NotifyIcon>添加元件，並設置重要屬性，如 和<xref:System.Windows.Forms.NotifyIcon.Icon%2A><xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性。  
  
     有關詳細資訊，請參閱[：使用 Windows 表單通知圖示元件將應用程式圖示添加到工作列](app-icons-to-the-taskbar-with-wf-notifyicon.md)。  
  
2. 向<xref:System.Windows.Forms.ContextMenu>Windows 表單添加元件。  
  
     將功能表項目添加到表示要在運行時提供的命令的快顯功能表中。 這也是向這些功能表項目（如便捷鍵）添加功能表增強功能的好時機。  
  
3. 將<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A><xref:System.Windows.Forms.NotifyIcon>元件的屬性設置為您添加的快顯功能表。  
  
     設置此屬性後，按一下工作列上的圖示時將顯示快顯功能表。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>以程式設計方式將快顯功能表與 NotifyIcon 元件關聯  
  
1. 創建<xref:System.Windows.Forms.NotifyIcon>類和<xref:System.Windows.Forms.ContextMenu>類的實例，包含應用程式所需的任何屬性設置（<xref:System.Windows.Forms.NotifyIcon.Icon%2A>以及<xref:System.Windows.Forms.NotifyIcon.Visible%2A><xref:System.Windows.Forms.NotifyIcon>元件的屬性、元件的<xref:System.Windows.Forms.ContextMenu>功能表項目）。  
  
2. 將<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A><xref:System.Windows.Forms.NotifyIcon>元件的屬性設置為您添加的快顯功能表。  
  
     設置此屬性後，按一下工作列上的圖示時將顯示快顯功能表。  
  
    > [!NOTE]
    > 以下代碼示例創建基本功能表結構。 您需要自訂功能表選項，以適應您正在開發的應用程式。 此外，您需要編寫代碼來處理這些功能表項目<xref:System.Windows.Forms.MenuItem.Click>的事件。  
  
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
> 您必須初始化`notifyIcon1`，`contextMenu1,`並且可以通過在表單的建構函式中包括以下語句來實現：  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon 元件](notifyicon-component-windows-forms.md)
- [NotifyIcon 元件概觀](notifyicon-component-overview-windows-forms.md)
