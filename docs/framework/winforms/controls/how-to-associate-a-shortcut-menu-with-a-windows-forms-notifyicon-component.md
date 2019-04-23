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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337054"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="c3cb0-102">HOW TO：建立捷徑功能表與 Windows Forms NotifyIcon 元件的關聯</span><span class="sxs-lookup"><span data-stu-id="c3cb0-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
>  <span data-ttu-id="c3cb0-103">雖然<xref:System.Windows.Forms.MenuStrip>並<xref:System.Windows.Forms.ContextMenuStrip>取代及新增功能<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>控制項的舊版本中，<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>會保留回溯相容性以及供未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="c3cb0-104"><xref:System.Windows.Forms.NotifyIcon>元件會顯示在工作列的狀態通知區域中的圖示。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="c3cb0-105">通常，應用程式可讓您以滑鼠右鍵按一下此圖示可將命令傳送至它所代表的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="c3cb0-106">產生關聯<xref:System.Windows.Forms.ContextMenu>元件與<xref:System.Windows.Forms.NotifyIcon>元件，您可以將這項功能新增至您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3cb0-107">如果您想要在啟動時顯示的執行個體最小化您的應用程式<xref:System.Windows.Forms.NotifyIcon>元件，在工作列上，設定主要表單<xref:System.Windows.Forms.Form.WindowState%2A>屬性設<xref:System.Windows.Forms.FormWindowState.Minimized>，並確定<xref:System.Windows.Forms.NotifyIcon>元件的<xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="c3cb0-108">若要使用 NotifyIcon 元件關聯的捷徑功能表，在設計階段</span><span class="sxs-lookup"><span data-stu-id="c3cb0-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="c3cb0-109">新增<xref:System.Windows.Forms.NotifyIcon>元件至表單，以及設定重要的屬性，例如<xref:System.Windows.Forms.NotifyIcon.Icon%2A>和<xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="c3cb0-110">如需詳細資訊，請參閱[如何：新增應用程式圖示加入工作列使用 Windows Form NotifyIcon 元件](app-icons-to-the-taskbar-with-wf-notifyicon.md)。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="c3cb0-111">新增<xref:System.Windows.Forms.ContextMenu>元件至您的 Windows 表單。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="c3cb0-112">加入功能表項目代表您想要在執行階段提供之命令的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="c3cb0-113">這也是功能表增強功能加入這些功能表項目，例如存取金鑰的好時機。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="c3cb0-114">設定<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>屬性<xref:System.Windows.Forms.NotifyIcon>元件至您新增的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="c3cb0-115">設定這個屬性，按一下工作列上的圖示時，將會顯示快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="c3cb0-116">若要以程式設計方式使用 NotifyIcon 元件關聯的捷徑功能表</span><span class="sxs-lookup"><span data-stu-id="c3cb0-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="c3cb0-117">建立的執行個體<xref:System.Windows.Forms.NotifyIcon>類別和<xref:System.Windows.Forms.ContextMenu>類別，且任何屬性設定所需的應用程式 (<xref:System.Windows.Forms.NotifyIcon.Icon%2A>並<xref:System.Windows.Forms.NotifyIcon.Visible%2A>屬性<xref:System.Windows.Forms.NotifyIcon>元件，功能表項目<xref:System.Windows.Forms.ContextMenu>元件）。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="c3cb0-118">設定<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>屬性<xref:System.Windows.Forms.NotifyIcon>元件至您新增的捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="c3cb0-119">設定這個屬性，按一下工作列上的圖示時，將會顯示快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3cb0-120">下列程式碼範例會建立基本的功能表結構。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="c3cb0-121">您必須自訂以符合您正在開發的應用程式的功能表選項。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="c3cb0-122">此外，您會想要撰寫程式碼來處理<xref:System.Windows.Forms.MenuItem.Click>事件的這些功能表項目。</span><span class="sxs-lookup"><span data-stu-id="c3cb0-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
>  <span data-ttu-id="c3cb0-123">您必須先初始化`notifyIcon1`和`contextMenu1,`可執行下列陳述式併入您的表單的建構函式：</span><span class="sxs-lookup"><span data-stu-id="c3cb0-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3cb0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3cb0-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="c3cb0-125">如何：應用程式圖示加入工作列使用 Windows Forms NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="c3cb0-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="c3cb0-126">NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="c3cb0-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="c3cb0-127">NotifyIcon 元件概觀</span><span class="sxs-lookup"><span data-stu-id="c3cb0-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
