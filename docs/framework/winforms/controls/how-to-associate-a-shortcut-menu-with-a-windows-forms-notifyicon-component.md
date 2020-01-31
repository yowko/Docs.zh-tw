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
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a><span data-ttu-id="23a52-102">如何：將捷徑功能表與 Windows Form NotifyIcon 元件關聯</span><span class="sxs-lookup"><span data-stu-id="23a52-102">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>
> [!NOTE]
> <span data-ttu-id="23a52-103">雖然 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 將功能取代並加入舊版的 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 控制項，但如果您選擇，<xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 會保留供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="23a52-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="23a52-104"><xref:System.Windows.Forms.NotifyIcon> 元件會在工作列的狀態通知區域中顯示圖示。</span><span class="sxs-lookup"><span data-stu-id="23a52-104">The <xref:System.Windows.Forms.NotifyIcon> component displays an icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="23a52-105">通常，應用程式可讓您以滑鼠右鍵按一下此圖示，將命令傳送至它所代表的應用程式。</span><span class="sxs-lookup"><span data-stu-id="23a52-105">Commonly, applications enable you to right-click this icon to send commands to the application it represents.</span></span> <span data-ttu-id="23a52-106">藉由將 <xref:System.Windows.Forms.ContextMenu> 元件與 <xref:System.Windows.Forms.NotifyIcon> 元件建立關聯，您就可以將此功能新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="23a52-106">By associating a <xref:System.Windows.Forms.ContextMenu> component with the <xref:System.Windows.Forms.NotifyIcon> component, you can add this functionality to your applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23a52-107">如果您想要在啟動時將應用程式最小化，同時在工作列中顯示 <xref:System.Windows.Forms.NotifyIcon> 元件的實例，請將主要表單的 [<xref:System.Windows.Forms.Form.WindowState%2A>] 屬性設定為 [<xref:System.Windows.Forms.FormWindowState.Minimized>]，並確定 <xref:System.Windows.Forms.NotifyIcon> 元件的 [<xref:System.Windows.Forms.NotifyIcon.Visible%2A>] 屬性已設定為 [`true`]。</span><span class="sxs-lookup"><span data-stu-id="23a52-107">If you want your application to be minimized at startup while displaying an instance of the <xref:System.Windows.Forms.NotifyIcon> component in the taskbar, set the main form's <xref:System.Windows.Forms.Form.WindowState%2A> property to <xref:System.Windows.Forms.FormWindowState.Minimized> and be sure the <xref:System.Windows.Forms.NotifyIcon> component's <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property is set to `true`.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a><span data-ttu-id="23a52-108">在設計階段將快捷方式功能表與 NotifyIcon 元件產生關聯</span><span class="sxs-lookup"><span data-stu-id="23a52-108">To associate a shortcut menu with the NotifyIcon component at design time</span></span>  
  
1. <span data-ttu-id="23a52-109">將 <xref:System.Windows.Forms.NotifyIcon> 元件新增至您的表單，並設定重要屬性，例如 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 和 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="23a52-109">Add a <xref:System.Windows.Forms.NotifyIcon> component to your form, and set the important properties, such as the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties.</span></span>  
  
     <span data-ttu-id="23a52-110">如需詳細資訊，請參閱[如何：使用 Windows Forms NotifyIcon 元件將應用程式圖示新增至工作列](app-icons-to-the-taskbar-with-wf-notifyicon.md)。</span><span class="sxs-lookup"><span data-stu-id="23a52-110">For more information, see [How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
2. <span data-ttu-id="23a52-111">將 <xref:System.Windows.Forms.ContextMenu> 元件新增至您的 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="23a52-111">Add a <xref:System.Windows.Forms.ContextMenu> component to your Windows Form.</span></span>  
  
     <span data-ttu-id="23a52-112">將功能表項目新增至快捷方式功能表，代表您想要在執行時間提供的命令。</span><span class="sxs-lookup"><span data-stu-id="23a52-112">Add menu items to the shortcut menu representing the commands you want to make available at run time.</span></span> <span data-ttu-id="23a52-113">這也是將功能表增強功能新增至這些功能表項目的好時機，例如存取金鑰。</span><span class="sxs-lookup"><span data-stu-id="23a52-113">This is also a good time to add menu enhancements to these menu items, such as access keys.</span></span>  
  
3. <span data-ttu-id="23a52-114">將 <xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> 屬性設定為您新增的快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="23a52-114">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="23a52-115">設定此屬性後，按一下工作列上的圖示時，就會顯示快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="23a52-115">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a><span data-ttu-id="23a52-116">以程式設計方式將快捷方式功能表與 NotifyIcon 元件產生關聯</span><span class="sxs-lookup"><span data-stu-id="23a52-116">To associate a shortcut menu with the NotifyIcon component programmatically</span></span>  
  
1. <span data-ttu-id="23a52-117">建立 <xref:System.Windows.Forms.NotifyIcon> 類別和 <xref:System.Windows.Forms.ContextMenu> 類別的實例，其中包含應用程式所需的任何屬性設定（<xref:System.Windows.Forms.NotifyIcon.Icon%2A>，以及 <xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性（<xref:System.Windows.Forms.ContextMenu> 元件的功能表項目）。</span><span class="sxs-lookup"><span data-stu-id="23a52-117">Create an instance of the <xref:System.Windows.Forms.NotifyIcon> class and a <xref:System.Windows.Forms.ContextMenu> class, with whatever property settings are necessary for the application (<xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A> properties for the <xref:System.Windows.Forms.NotifyIcon> component, menu items for the <xref:System.Windows.Forms.ContextMenu> component).</span></span>  
  
2. <span data-ttu-id="23a52-118">將 <xref:System.Windows.Forms.NotifyIcon> 元件的 <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> 屬性設定為您新增的快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="23a52-118">Set the <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> property of the <xref:System.Windows.Forms.NotifyIcon> component to the shortcut menu that you added.</span></span>  
  
     <span data-ttu-id="23a52-119">設定此屬性後，按一下工作列上的圖示時，就會顯示快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="23a52-119">With this property set, the shortcut menu will be displayed when the icon on the taskbar is clicked.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="23a52-120">下列程式碼範例會建立基本功能表結構。</span><span class="sxs-lookup"><span data-stu-id="23a52-120">The following code example creates a basic menu structure.</span></span> <span data-ttu-id="23a52-121">您必須自訂功能表選項，使其符合您正在開發的應用程式。</span><span class="sxs-lookup"><span data-stu-id="23a52-121">You will need to customize the menu choices to those that fit the application you are developing.</span></span> <span data-ttu-id="23a52-122">此外，您也會想要撰寫程式碼來處理這些功能表項目的 <xref:System.Windows.Forms.MenuItem.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="23a52-122">Additionally, you will want to write code to handle the <xref:System.Windows.Forms.MenuItem.Click> events for these menu items.</span></span>  
  
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
> <span data-ttu-id="23a52-123">您必須將下列語句包含在表單的函式中，以初始化 `notifyIcon1` 和 `contextMenu1,` 可以執行的動作：</span><span class="sxs-lookup"><span data-stu-id="23a52-123">You must initialize `notifyIcon1` and `contextMenu1,` which you can do by including the following statements in the constructor of your form:</span></span>  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a><span data-ttu-id="23a52-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="23a52-124">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="23a52-125">操作說明：使用 Windows Forms NotifyIcon 元件將應用程式圖示加入至 TaskBar</span><span class="sxs-lookup"><span data-stu-id="23a52-125">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [<span data-ttu-id="23a52-126">NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="23a52-126">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="23a52-127">NotifyIcon 元件概觀</span><span class="sxs-lookup"><span data-stu-id="23a52-127">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
