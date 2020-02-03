---
title: 將快捷方式功能表與 NotifyIcon 元件產生關聯
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
ms.openlocfilehash: 392c04f73feaec201033ad76f9419a0e070bec70
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742043"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>如何：將捷徑功能表與 Windows Form NotifyIcon 元件關聯
> [!NOTE]
> 雖然 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 將功能取代並加入舊版的 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 控制項，但如果您選擇，<xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 會保留供回溯相容性及未來使用。  
  
 <xref:System.Windows.Forms.NotifyIcon> 元件會在工作列的狀態通知區域中顯示圖示。 通常，應用程式可讓您以滑鼠右鍵按一下此圖示，將命令傳送至它所代表的應用程式。 藉由將 <xref:System.Windows.Forms.ContextMenu> 元件與 <xref:System.Windows.Forms.NotifyIcon> 元件建立關聯，您就可以將此功能新增至應用程式。  
  
> [!NOTE]
> 如果您想要在啟動時將應用程式最小化，同時在工作列中顯示 <xref:System.Windows.Forms.NotifyIcon> 元件的實例，請將主要表單的 [<xref:System.Windows.Forms.Form.WindowState%2A>] 屬性設定為 [<xref:System.Windows.Forms.FormWindowState.Minimized>]，並確定 <xref:System.Windows.Forms.NotifyIcon> 元件的 [<xref:System.Windows.Forms.NotifyIcon.Visible%2A>] 屬性已設定為 [`true`]。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>在設計階段將快捷方式功能表與 NotifyIcon 元件產生關聯  
  
1. 將 <xref:System.Windows.Forms.NotifyIcon> 元件新增至您的表單，並設定重要屬性，例如 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性。  
  
     如需詳細資訊，請參閱[如何：使用 Windows Forms NotifyIcon 元件將應用程式圖示新增至工作列](app-icons-to-the-taskbar-with-wf-notifyicon.md)。  
  
2. 將 <xref:System.Windows.Forms.ContextMenu> 元件新增至您的 Windows Form。  
  
     將功能表項目新增至快捷方式功能表，代表您想要在執行時間提供的命令。 這也是將功能表增強功能新增至這些功能表項目的好時機，例如存取金鑰。  
  
3. 將 <xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> 屬性設定為您新增的快捷方式功能表。  
  
     設定此屬性後，按一下工作列上的圖示時，就會顯示快捷方式功能表。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>以程式設計方式將快捷方式功能表與 NotifyIcon 元件產生關聯  
  
1. 建立 <xref:System.Windows.Forms.NotifyIcon> 類別和 <xref:System.Windows.Forms.ContextMenu> 類別的實例，其中包含應用程式所需的任何屬性設定（<xref:System.Windows.Forms.NotifyIcon.Icon%2A>，以及 <xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性（<xref:System.Windows.Forms.ContextMenu> 元件的功能表項目）。  
  
2. 將 <xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> 屬性設定為您新增的快捷方式功能表。  
  
     設定此屬性後，按一下工作列上的圖示時，就會顯示快捷方式功能表。  
  
    > [!NOTE]
    > 下列程式碼範例會建立基本功能表結構。 您必須自訂功能表選項，使其符合您正在開發的應用程式。 此外，您也會想要撰寫程式碼來處理這些功能表項目的 <xref:System.Windows.Forms.MenuItem.Click> 事件。  
  
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
> 您必須將下列語句包含在表單的函式中，以初始化 `notifyIcon1` 和 `contextMenu1,` 可以執行的動作：  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [操作說明：使用 Windows Forms NotifyIcon 元件將應用程式圖示加入至 TaskBar](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon 元件](notifyicon-component-windows-forms.md)
- [NotifyIcon 元件概觀](notifyicon-component-overview-windows-forms.md)
