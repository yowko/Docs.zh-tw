---
title: "如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d795df8e8b514345632491fd6afdd618c2f18ec2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a><span data-ttu-id="2ff93-102">如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar</span><span class="sxs-lookup"><span data-stu-id="2ff93-102">How to: Add Application Icons to the TaskBar with the Windows Forms NotifyIcon Component</span></span>
<span data-ttu-id="2ff93-103">Windows Form<xref:System.Windows.Forms.NotifyIcon>元件會在工作列的狀態通知區域中顯示一個圖示。</span><span class="sxs-lookup"><span data-stu-id="2ff93-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status notification area of the taskbar.</span></span> <span data-ttu-id="2ff93-104">若要在 [狀態] 區域中顯示多個圖示，您必須有多個<xref:System.Windows.Forms.NotifyIcon>表單上的元件。</span><span class="sxs-lookup"><span data-stu-id="2ff93-104">To display multiple icons in the status area, you must have multiple <xref:System.Windows.Forms.NotifyIcon> components on your form.</span></span> <span data-ttu-id="2ff93-105">若要設定顯示控制項的圖示，請使用<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="2ff93-105">To set the icon displayed for a control, use the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="2ff93-106">您也可以撰寫程式碼<xref:System.Windows.Forms.NotifyIcon.DoubleClick>事件處理常式，因此當使用者按兩下圖示時，會發生的事情的情況。</span><span class="sxs-lookup"><span data-stu-id="2ff93-106">You can also write code in the <xref:System.Windows.Forms.NotifyIcon.DoubleClick> event handler so that something happens when the user double-clicks the icon.</span></span> <span data-ttu-id="2ff93-107">例如，您可以進行設定圖示所代表的背景處理序的使用者出現的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2ff93-107">For example, you could make a dialog box appear for the user to configure the background process represented by the icon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ff93-108"><xref:System.Windows.Forms.NotifyIcon>元件通知僅供使用，可用來警示使用者動作或事件已發生或發生某種類型的狀態變更。</span><span class="sxs-lookup"><span data-stu-id="2ff93-108">The <xref:System.Windows.Forms.NotifyIcon> component is used for notification purposes only, to alert users that an action or event has occurred or there has been a change in status of some sort.</span></span> <span data-ttu-id="2ff93-109">您應該使用與應用程式的標準互動的功能表、 工具列和其他使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="2ff93-109">You should use menus, toolbars, and other user-interface elements for standard interaction with applications.</span></span>  
  
### <a name="to-set-the-icon"></a><span data-ttu-id="2ff93-110">若要設定圖示</span><span class="sxs-lookup"><span data-stu-id="2ff93-110">To set the icon</span></span>  
  
1.  <span data-ttu-id="2ff93-111">指派值給<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="2ff93-111">Assign a value to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property.</span></span> <span data-ttu-id="2ff93-112">值必須是型別`System.Drawing.Icon`且能載入從.ico 檔案。</span><span class="sxs-lookup"><span data-stu-id="2ff93-112">The value must be of type `System.Drawing.Icon` and can be loaded from an .ico file.</span></span> <span data-ttu-id="2ff93-113">您可以指定的圖示檔，在程式碼，或按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性**屬性**視窗，然後選取 檔案中的**開啟**出現的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2ff93-113">You can specify the icon file in code or by clicking the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property in the **Properties** window, and then selecting the file in the **Open** dialog box that appears.</span></span>  
  
2.  <span data-ttu-id="2ff93-114">將 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="2ff93-114">Set the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property to `true`.</span></span>  
  
3.  <span data-ttu-id="2ff93-115">設定<xref:System.Windows.Forms.NotifyIcon.Text%2A>屬性設為適當的工具提示字串。</span><span class="sxs-lookup"><span data-stu-id="2ff93-115">Set the <xref:System.Windows.Forms.NotifyIcon.Text%2A> property to an appropriate ToolTip string.</span></span>  
  
     <span data-ttu-id="2ff93-116">在下列程式碼範例中，將路徑設定圖示的位置是**我的文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ff93-116">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="2ff93-117">使用這個位置是因為您可以假設執行 Windows 作業系統的大部分電腦都會包含此資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ff93-117">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="2ff93-118">選擇此位置也可讓使用者以最少的系統存取層級可安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ff93-118">Choosing this location also enables users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="2ff93-119">下列範例要求的表單具有<xref:System.Windows.Forms.NotifyIcon>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="2ff93-119">The following example requires a form with a <xref:System.Windows.Forms.NotifyIcon> control already added.</span></span> <span data-ttu-id="2ff93-120">它也需要一個名為圖示檔案`Icon.ico`。</span><span class="sxs-lookup"><span data-stu-id="2ff93-120">It also requires an icon file named `Icon.ico`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ff93-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ff93-121">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [<span data-ttu-id="2ff93-122">操作說明：將捷徑功能表與 Windows Forms NotifyIcon 元件關聯</span><span class="sxs-lookup"><span data-stu-id="2ff93-122">How to: Associate a Shortcut Menu with a Windows Forms NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [<span data-ttu-id="2ff93-123">NotifyIcon 元件</span><span class="sxs-lookup"><span data-stu-id="2ff93-123">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [<span data-ttu-id="2ff93-124">NotifyIcon 元件概觀</span><span class="sxs-lookup"><span data-stu-id="2ff93-124">NotifyIcon Component Overview</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
