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
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="4a379-102">如何：將捷徑功能表與 Windows Form NotifyIcon 元件關聯</span><span class="sxs-lookup"><span data-stu-id="4a379-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="4a379-103">以及<xref:System.Windows.Forms.MenuStrip>將<xref:System.Windows.Forms.ContextMenuStrip>功能替換和添加到早期版本的<xref:System.Windows.Forms.MainMenu><xref:System.Windows.Forms.ContextMenu>和 控制項，<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>保留用於向後相容性和將來使用（如果選擇）。</span><span class="sxs-lookup"><span data-stu-id="4a379-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="4a379-104">元件<xref:System.Windows.Forms.NotifyIcon>在工作列的狀態通知區域中顯示一個圖示。</span><span class="sxs-lookup"><span data-stu-id="4a379-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="4a379-105">通常，應用程式允許您按右鍵此圖示，將命令發送到它所代表的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a379-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="4a379-106">通過將<xref:System.Windows.Forms.ContextMenu>元件與<xref:System.Windows.Forms.NotifyIcon>元件關聯，可以將此功能添加到應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4a379-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a379-107">如果希望在啟動時最小化應用程式，<xref:System.Windows.Forms.NotifyIcon>同時在工作列中顯示元件的實例，請將主表單的屬性<xref:System.Windows.Forms.Form.WindowState%2A>設置為<xref:System.Windows.Forms.FormWindowState.Minimized>，並確保<xref:System.Windows.Forms.NotifyIcon>元件的屬性<xref:System.Windows.Forms.NotifyIcon.Visible%2A>設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="4a379-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="4a379-108">在設計時將快顯功能表與 NotifyIcon 元件關聯</span><span class="sxs-lookup"><span data-stu-id="4a379-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="4a379-109">向表單<xref:System.Windows.Forms.NotifyIcon>添加元件，並設置重要屬性，如 和<xref:System.Windows.Forms.NotifyIcon.Icon%2A><xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4a379-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="4a379-110">有關詳細資訊，請參閱[：使用 Windows 表單通知圖示元件將應用程式圖示添加到工作列](app-icons-to-the-taskbar-with-wf-notifyicon.md)。</span><span class="sxs-lookup"><span data-stu-id="4a379-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="4a379-111">向<xref:System.Windows.Forms.ContextMenu>Windows 表單添加元件。</span><span class="sxs-lookup"><span data-stu-id="4a379-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="4a379-112">將功能表項目添加到表示要在運行時提供的命令的快顯功能表中。</span><span class="sxs-lookup"><span data-stu-id="4a379-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="4a379-113">這也是向這些功能表項目（如便捷鍵）添加功能表增強功能的好時機。</span><span class="sxs-lookup"><span data-stu-id="4a379-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="4a379-114">將<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A><xref:System.Windows.Forms.NotifyIcon>元件的屬性設置為您添加的快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="4a379-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="4a379-115">設置此屬性後，按一下工作列上的圖示時將顯示快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="4a379-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="4a379-116">以程式設計方式將快顯功能表與 NotifyIcon 元件關聯</span><span class="sxs-lookup"><span data-stu-id="4a379-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="4a379-117">創建<xref:System.Windows.Forms.NotifyIcon>類和<xref:System.Windows.Forms.ContextMenu>類的實例，包含應用程式所需的任何屬性設置（<xref:System.Windows.Forms.NotifyIcon.Icon%2A>以及<xref:System.Windows.Forms.NotifyIcon.Visible%2A><xref:System.Windows.Forms.NotifyIcon>元件的屬性、元件的<xref:System.Windows.Forms.ContextMenu>功能表項目）。</span><span class="sxs-lookup"><span data-stu-id="4a379-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="4a379-118">將<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A><xref:System.Windows.Forms.NotifyIcon>元件的屬性設置為您添加的快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="4a379-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="4a379-119">設置此屬性後，按一下工作列上的圖示時將顯示快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="4a379-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4a379-120">以下代碼示例創建基本功能表結構。</span><span class="sxs-lookup"><span data-stu-id="4a379-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="4a379-121">您需要自訂功能表選項，以適應您正在開發的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a379-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="4a379-122">此外，您需要編寫代碼來處理這些功能表項目<xref:System.Windows.Forms.MenuItem.Click>的事件。</span><span class="sxs-lookup"><span data-stu-id="4a379-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="4a379-123">您必須初始化`notifyIcon1`，`contextMenu1,`並且可以通過在表單的建構函式中包括以下語句來實現：</span><span class="sxs-lookup"><span data-stu-id="4a379-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a379-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a379-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="4a379-125">如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar</span><span class="sxs-lookup"><span data-stu-id="4a379-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="4a379-126">NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="4a379-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="4a379-127">NotifyIcon 元件概觀</span><span class="sxs-lookup"><span data-stu-id="4a379-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
