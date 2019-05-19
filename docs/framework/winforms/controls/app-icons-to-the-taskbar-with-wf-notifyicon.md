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
ms.openlocfilehash: 2d7fb1dfbdfb7cf9be33fc8c9711b4fbdc3efc2d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880543"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="7097f-102">作法：使用 Windows Forms NotifyIcon 元件將應用程式圖示新增至工作列</span><span class="sxs-lookup"><span data-stu-id="7097f-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>
<span data-ttu-id="7097f-103">Windows Form<xref:System.Windows.Forms.NotifyIcon>元件會顯示單一圖示在工作列的狀態通知區域中。</span><span class="sxs-lookup"><span data-stu-id="7097f-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="7097f-104">若要顯示多個圖示，狀態 區域中，您必須有多個<xref:System.Windows.Forms.NotifyIcon>您的表單上的元件。</span><span class="sxs-lookup"><span data-stu-id="7097f-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="7097f-105">若要設定控制項所顯示的圖示，使用<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7097f-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="7097f-106">您也可以撰寫程式碼<xref:System.Windows.Forms.NotifyIcon.DoubleClick>事件處理常式，因此當使用者按兩下的圖示時，會有發生的情況。</span><span class="sxs-lookup"><span data-stu-id="7097f-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="7097f-107">例如，您可以進行使用者設定圖示所代表的背景處理序出現的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7097f-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7097f-108"><xref:System.Windows.Forms.NotifyIcon>元件用以通知僅供，某個動作或事件已發生的警示使用者，或已有某種形式的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="7097f-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="7097f-109">您應該使用標準互動的應用程式的功能表、 工具列和其他使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="7097f-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>  
  
### <a name="to-set-the-icon"></a><span data-ttu-id="7097f-110">若要設定圖示</span><span class="sxs-lookup"><span data-stu-id="7097f-110">To set the icon</span></span>  
  
1.  <span data-ttu-id="7097f-111">指派值給<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="7097f-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="7097f-112">值必須是型別`System.Drawing.Icon`和從.ico 檔可以載入。</span><span class="sxs-lookup"><span data-stu-id="7097f-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="7097f-113">在程式碼，或按一下省略符號按鈕，您可以指定的圖示檔 (![的 Visual Studio 的 [屬性] 視窗中的省略符號按鈕 （...）](./media/visual-studio-ellipsis-button.png)) 旁邊<xref:System.Windows.Forms.NotifyIcon.Icon%2A>中的屬性**屬性**視窗中，，然後選取 檔案中的**開啟**出現的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7097f-113">You can specify the icon file in code or by clicking the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>  
  
2. <span data-ttu-id="7097f-114">將 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="7097f-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="7097f-115">設定<xref:System.Windows.Forms.NotifyIcon.Text%2A>屬性設為適當的工具提示字串。</span><span class="sxs-lookup"><span data-stu-id="7097f-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>  
  
     <span data-ttu-id="7097f-116">在下列程式碼範例中，將路徑設為圖示的位置**我的文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="7097f-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="7097f-117">因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此資料夾，會使用此位置。</span><span class="sxs-lookup"><span data-stu-id="7097f-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="7097f-118">選擇此位置也可讓具有最少的系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7097f-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="7097f-119">下列範例需要表單<xref:System.Windows.Forms.NotifyIcon>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="7097f-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="7097f-120">它也需要圖示檔名為`Icon.ico`。</span><span class="sxs-lookup"><span data-stu-id="7097f-120">It also requires an icon file named `Icon.ico`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7097f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7097f-121">See also</span></span>

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [<span data-ttu-id="7097f-122">如何：使用 Windows Forms NotifyIcon 元件關聯的捷徑功能表</span><span class="sxs-lookup"><span data-stu-id="7097f-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [<span data-ttu-id="7097f-123">NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="7097f-123">NotifyIcon Component</span></span>](notifyicon-component-windows-forms.md)
- [<span data-ttu-id="7097f-124">NotifyIcon 元件概觀</span><span class="sxs-lookup"><span data-stu-id="7097f-124">NotifyIcon Component Overview</span></span>](notifyicon-component-overview-windows-forms.md)
