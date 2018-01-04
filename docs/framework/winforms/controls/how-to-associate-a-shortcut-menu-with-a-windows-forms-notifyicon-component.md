---
title: "如何：將捷徑功能表與 Windows Form NotifyIcon 元件關聯"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a594888351710639f7ebc07eb99a425df2ea80d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>如何：將捷徑功能表與 Windows Form NotifyIcon 元件關聯
> [!NOTE]
>  雖然<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>取代，並將功能加入至<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>的舊版中，控制項<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>您選擇保留的回溯相容性及供未來使用。  
  
 <xref:System.Windows.Forms.NotifyIcon>元件工作列的狀態通知區域中顯示圖示。 一般而言，應用程式可讓您以滑鼠右鍵按一下此圖示將命令傳送至它所代表的應用程式。 透過建立關聯<xref:System.Windows.Forms.ContextMenu>元件<xref:System.Windows.Forms.NotifyIcon>元件，您可以將這項功能加入至您的應用程式。  
  
> [!NOTE]
>  如果您希望應用程式最小化在啟動時顯示的執行個體<xref:System.Windows.Forms.NotifyIcon>元件在工作列中，將主要表單的<xref:System.Windows.Forms.Form.WindowState%2A>屬性<xref:System.Windows.Forms.FormWindowState.Minimized>，並確定<xref:System.Windows.Forms.NotifyIcon>元件的<xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性設定為`true`。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>在設計階段與 NotifyIcon 元件的捷徑功能表  
  
1.  新增<xref:System.Windows.Forms.NotifyIcon>元件加入至表單，並設定重要的屬性，例如<xref:System.Windows.Forms.NotifyIcon.Icon%2A>和<xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性。  
  
     如需詳細資訊，請參閱[如何： 新增應用程式圖示加入工作列使用 Windows Form NotifyIcon 元件](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)。  
  
2.  新增<xref:System.Windows.Forms.ContextMenu>元件加入至 Windows 表單。  
  
     加入功能表項目代表您想要提供在執行階段之命令的捷徑功能表。 這也是將功能表增強功能加入至這些功能表項目，例如存取金鑰的好時機。  
  
3.  設定<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>屬性<xref:System.Windows.Forms.NotifyIcon>元件至您新增的捷徑功能表。  
  
     設定這個屬性，按一下工作列上的圖示時將顯示的捷徑功能表。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>若要以程式設計方式，與 NotifyIcon 元件產生關聯的捷徑功能表  
  
1.  建立的執行個體<xref:System.Windows.Forms.NotifyIcon>類別和<xref:System.Windows.Forms.ContextMenu>類別，具有任何屬性設定所需的應用程式 (<xref:System.Windows.Forms.NotifyIcon.Icon%2A>和<xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性<xref:System.Windows.Forms.NotifyIcon>元件，用於功能表項目<xref:System.Windows.Forms.ContextMenu>元件）。  
  
2.  設定<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>屬性<xref:System.Windows.Forms.NotifyIcon>元件至您新增的捷徑功能表。  
  
     設定這個屬性，按一下工作列上的圖示時將顯示的捷徑功能表。  
  
    > [!NOTE]
    >  下列程式碼範例會建立基本的功能表結構。 您必須自訂功能表選項，以符合您所開發的應用程式。 此外，您會想要撰寫程式碼以處理<xref:System.Windows.Forms.MenuItem.Click>事件的這些功能表項目。  
  
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
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [操作說明：使用 Windows Forms NotifyIcon 元件將應用程式圖示加入至 TaskBar](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)  
 [NotifyIcon 元件](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [NotifyIcon 元件概觀](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
