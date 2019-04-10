---
title: HOW TO：使用 Windows Forms NotifyIcon 元件將應用程式圖示新增至工作列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: 52c18b959361079aac6b95dc5d4584bf464a306a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304515"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="e1f19-102">HOW TO：使用 Windows Forms NotifyIcon 元件將應用程式圖示新增至工作列</span><span class="sxs-lookup"><span data-stu-id="e1f19-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>
<span data-ttu-id="e1f19-103">Windows Form<xref:System.Windows.Forms.NotifyIcon>元件會顯示單一圖示在工作列的狀態通知區域中。</span><span class="sxs-lookup"><span data-stu-id="e1f19-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="e1f19-104">若要顯示多個圖示，狀態 區域中，您必須有多個<xref:System.Windows.Forms.NotifyIcon>您的表單上的元件。</span><span class="sxs-lookup"><span data-stu-id="e1f19-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="e1f19-105">若要設定控制項所顯示的圖示，使用<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f19-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="e1f19-106">您也可以撰寫程式碼<xref:System.Windows.Forms.NotifyIcon.DoubleClick>事件處理常式，因此當使用者按兩下的圖示時，會有發生的情況。</span><span class="sxs-lookup"><span data-stu-id="e1f19-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="e1f19-107">例如，您可以進行使用者設定圖示所代表的背景處理序出現的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e1f19-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1f19-108"><xref:System.Windows.Forms.NotifyIcon>元件用以通知僅供，某個動作或事件已發生的警示使用者，或已有某種形式的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="e1f19-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="e1f19-109">您應該使用標準互動的應用程式的功能表、 工具列和其他使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="e1f19-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>  
  
### <a name="to-set-the-icon"></a><span data-ttu-id="e1f19-110">若要設定圖示</span><span class="sxs-lookup"><span data-stu-id="e1f19-110">To set the icon</span></span>  
  
1. <span data-ttu-id="e1f19-111">指派值給<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e1f19-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="e1f19-112">值必須是型別`System.Drawing.Icon`和從.ico 檔可以載入。</span><span class="sxs-lookup"><span data-stu-id="e1f19-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="e1f19-113">在程式碼，或按一下省略符號按鈕，您可以指定的圖示檔 (![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁<xref:System.Windows.Forms.NotifyIcon.Icon%2A>中的屬性**屬性**視窗中，，然後選取 檔案中的**開啟**出現的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e1f19-113">You can specify the icon file in code or by clicking the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>  
  
2. <span data-ttu-id="e1f19-114">將 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="e1f19-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="e1f19-115">設定<xref:System.Windows.Forms.NotifyIcon.Text%2A>屬性設為適當的工具提示字串。</span><span class="sxs-lookup"><span data-stu-id="e1f19-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>  
  
     <span data-ttu-id="e1f19-116">在下列程式碼範例中，將路徑設為圖示的位置**我的文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="e1f19-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="e1f19-117">因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此資料夾，會使用此位置。</span><span class="sxs-lookup"><span data-stu-id="e1f19-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="e1f19-118">選擇此位置也可讓具有最少的系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1f19-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="e1f19-119">下列範例需要表單<xref:System.Windows.Forms.NotifyIcon>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="e1f19-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="e1f19-120">它也需要圖示檔名為`Icon.ico`。</span><span class="sxs-lookup"><span data-stu-id="e1f19-120">It also requires an icon file named `Icon.ico`.</span></span>  
  
    ```vb  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
    ```  
  
    ```csharp  
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
  
    ```cpp  
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
  
## <a name="see-also"></a><span data-ttu-id="e1f19-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1f19-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="e1f19-122">HOW TO：建立捷徑功能表與 Windows Forms NotifyIcon 元件的關聯</span><span class="sxs-lookup"><span data-stu-id="e1f19-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="e1f19-123">NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="e1f19-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="e1f19-124">NotifyIcon 元件概觀</span><span class="sxs-lookup"><span data-stu-id="e1f19-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
