---
title: 使用 NotifyIcon 元件將應用程式圖示新增至工作列
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
ms.openlocfilehash: 46b50ecaabe75dba08fea922d7b5639031692269
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746242"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="228e6-102">如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar</span><span class="sxs-lookup"><span data-stu-id="228e6-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>

<span data-ttu-id="228e6-103">Windows Forms <xref:System.Windows.Forms.NotifyIcon> 元件會在工作列的狀態通知區域中顯示單一圖示。</span><span class="sxs-lookup"><span data-stu-id="228e6-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="228e6-104">若要在 [狀態] 區域中顯示多個圖示，您的表單上必須有多個 <xref:System.Windows.Forms.NotifyIcon> 元件。</span><span class="sxs-lookup"><span data-stu-id="228e6-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="228e6-105">若要設定控制項的顯示圖示，請使用 [<xref:System.Windows.Forms.NotifyIcon.Icon%2A>] 屬性。</span><span class="sxs-lookup"><span data-stu-id="228e6-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="228e6-106">您也可以在 <xref:System.Windows.Forms.NotifyIcon.DoubleClick> 事件處理常式中撰寫程式碼，如此一來，當使用者按兩下圖示時，就會發生問題。</span><span class="sxs-lookup"><span data-stu-id="228e6-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="228e6-107">例如，您可以讓使用者看到對話方塊，以設定圖示所代表的背景進程。</span><span class="sxs-lookup"><span data-stu-id="228e6-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>

> [!NOTE]
> <span data-ttu-id="228e6-108"><xref:System.Windows.Forms.NotifyIcon> 元件僅供通知之用，用來警示使用者發生動作或事件，或某個排序狀態有變更。</span><span class="sxs-lookup"><span data-stu-id="228e6-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="228e6-109">您應該使用功能表、工具列和其他使用者介面元素，來與應用程式進行標準互動。</span><span class="sxs-lookup"><span data-stu-id="228e6-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>

### <a name="to-set-the-icon"></a><span data-ttu-id="228e6-110">若要設定圖示</span><span class="sxs-lookup"><span data-stu-id="228e6-110">To set the icon</span></span>

1. <span data-ttu-id="228e6-111">將值指派給 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="228e6-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="228e6-112">此值必須是 `System.Drawing.Icon` 類型，而且可以從 .ico 檔案載入。</span><span class="sxs-lookup"><span data-stu-id="228e6-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="228e6-113">您可以在程式碼中指定圖示檔，或按一下省略號按鈕（![**屬性**] 視窗中 [<xref:System.Windows.Forms.NotifyIcon.Icon%2A>] 屬性旁邊的 [](./media/visual-studio-ellipsis-button.png)Visual Studio 屬性視窗中的省略號按鈕（...），然後在出現的 [**開啟**] 對話方塊中選取檔案。</span><span class="sxs-lookup"><span data-stu-id="228e6-113">You can specify the icon file in code or by clicking the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>

2. <span data-ttu-id="228e6-114">將 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="228e6-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>

3. <span data-ttu-id="228e6-115">將 [<xref:System.Windows.Forms.NotifyIcon.Text%2A>] 屬性設定為適當的工具提示字串。</span><span class="sxs-lookup"><span data-stu-id="228e6-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>

     <span data-ttu-id="228e6-116">在下列程式碼範例中，為圖示的位置設定的路徑是 [**我的文件**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="228e6-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="228e6-117">因為您可以假設大部分執行 Windows 作業系統的電腦都包含此資料夾，所以會使用這個位置。</span><span class="sxs-lookup"><span data-stu-id="228e6-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="228e6-118">選擇此位置也可讓具有最低系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="228e6-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="228e6-119">下列範例需要已經加入 <xref:System.Windows.Forms.NotifyIcon> 控制項的表單。</span><span class="sxs-lookup"><span data-stu-id="228e6-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="228e6-120">它也需要名為 `Icon.ico`的圖示檔。</span><span class="sxs-lookup"><span data-stu-id="228e6-120">It also requires an icon file named `Icon.ico`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="228e6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="228e6-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="228e6-122">操作說明：將捷徑功能表與 Windows Forms NotifyIcon 元件關聯</span><span class="sxs-lookup"><span data-stu-id="228e6-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="228e6-123">NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="228e6-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="228e6-124">NotifyIcon 元件概觀</span><span class="sxs-lookup"><span data-stu-id="228e6-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
