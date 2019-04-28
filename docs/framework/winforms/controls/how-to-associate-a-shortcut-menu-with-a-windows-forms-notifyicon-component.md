---
title: HOW TO：建立捷徑功能表與 Windows Forms NotifyIcon 元件的關聯
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
ms.openlocfilehash: f2a086cc25eb6996b2643742a887bccf481916d6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010939"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>HOW TO：建立捷徑功能表與 Windows Forms NotifyIcon 元件的關聯
> [!NOTE]
>  雖然<xref:System.Windows.Forms.MenuStrip>並<xref:System.Windows.Forms.ContextMenuStrip>取代及新增功能<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>控制項的舊版本中，<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>會保留回溯相容性以及供未來使用，如果您選擇。  
  
 <xref:System.Windows.Forms.NotifyIcon>元件會顯示在工作列的狀態通知區域中的圖示。 通常，應用程式可讓您以滑鼠右鍵按一下此圖示可將命令傳送至它所代表的應用程式。 產生關聯<xref:System.Windows.Forms.ContextMenu>元件與<xref:System.Windows.Forms.NotifyIcon>元件，您可以將這項功能新增至您的應用程式。  
  
> [!NOTE]
>  如果您想要在啟動時顯示的執行個體最小化您的應用程式<xref:System.Windows.Forms.NotifyIcon>元件，在工作列上，設定主要表單<xref:System.Windows.Forms.Form.WindowState%2A>屬性設<xref:System.Windows.Forms.FormWindowState.Minimized>，並確定<xref:System.Windows.Forms.NotifyIcon>元件的<xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性設定為`true`。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>若要使用 NotifyIcon 元件關聯的捷徑功能表，在設計階段  
  
1. 新增<xref:System.Windows.Forms.NotifyIcon>元件至表單，以及設定重要的屬性，例如<xref:System.Windows.Forms.NotifyIcon.Icon%2A>和<xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性。  
  
     如需詳細資訊，請參閱[如何：新增應用程式圖示加入工作列使用 Windows Form NotifyIcon 元件](app-icons-to-the-taskbar-with-wf-notifyicon.md)。  
  
2. 新增<xref:System.Windows.Forms.ContextMenu>元件至您的 Windows 表單。  
  
     加入功能表項目代表您想要在執行階段提供之命令的捷徑功能表。 這也是功能表增強功能加入這些功能表項目，例如存取金鑰的好時機。  
  
3. 設定<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>屬性<xref:System.Windows.Forms.NotifyIcon>元件至您新增的捷徑功能表。  
  
     設定這個屬性，按一下工作列上的圖示時，將會顯示快顯功能表。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>若要以程式設計方式使用 NotifyIcon 元件關聯的捷徑功能表  
  
1. 建立的執行個體<xref:System.Windows.Forms.NotifyIcon>類別和<xref:System.Windows.Forms.ContextMenu>類別，且任何屬性設定所需的應用程式 (<xref:System.Windows.Forms.NotifyIcon.Icon%2A>並<xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性<xref:System.Windows.Forms.NotifyIcon>元件，功能表項目<xref:System.Windows.Forms.ContextMenu>元件）。  
  
2. 設定<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>屬性<xref:System.Windows.Forms.NotifyIcon>元件至您新增的捷徑功能表。  
  
     設定這個屬性，按一下工作列上的圖示時，將會顯示快顯功能表。  
  
    > [!NOTE]
    >  下列程式碼範例會建立基本的功能表結構。 您必須自訂以符合您正在開發的應用程式的功能表選項。 此外，您會想要撰寫程式碼來處理<xref:System.Windows.Forms.MenuItem.Click>事件的這些功能表項目。  
  
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
>  您必須先初始化`notifyIcon1`和`contextMenu1,`可執行下列陳述式併入您的表單的建構函式：  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [如何：應用程式圖示加入工作列使用 Windows Forms NotifyIcon 元件](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon 元件](notifyicon-component-windows-forms.md)
- [NotifyIcon 元件概觀](notifyicon-component-overview-windows-forms.md)
