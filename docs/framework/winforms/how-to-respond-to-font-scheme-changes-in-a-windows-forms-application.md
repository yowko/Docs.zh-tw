---
title: "如何：回應 Windows Forms 應用程式中的字型配置變更"
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
helpviewer_keywords: Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aac8d56c87ff03b313565a3d04cd3f3cc4e85f72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="707f1-102">如何：回應 Windows Forms 應用程式中的字型配置變更</span><span class="sxs-lookup"><span data-stu-id="707f1-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="707f1-103">在 Windows 作業系統中，使用者可以變更全系統字型設定，讓預設字型看起來更大或變小。</span><span class="sxs-lookup"><span data-stu-id="707f1-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="707f1-104">變更這些字型設定是重要的是視覺障礙者，並且需要讀取他們的螢幕上文字的較大類型的使用者。</span><span class="sxs-lookup"><span data-stu-id="707f1-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="707f1-105">您可以調整 Windows Form 應用程式由增加或減少大小的表單和內含之所有文字的字型配置變更時回應這些變更。</span><span class="sxs-lookup"><span data-stu-id="707f1-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="707f1-106">如果您想要以動態方式容納變更字型大小表單時，您可以將程式碼加入至表單。</span><span class="sxs-lookup"><span data-stu-id="707f1-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="707f1-107">一般而言，Windows Forms 所使用的預設字型是所傳回的字型<xref:Microsoft.Win32>命名空間呼叫`GetStockObject(DEFAULT_GUI_FONT)`。</span><span class="sxs-lookup"><span data-stu-id="707f1-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="707f1-108">這個呼叫所傳回的字型僅會變更螢幕解析度變更時。</span><span class="sxs-lookup"><span data-stu-id="707f1-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="707f1-109">下列程序所示，您的程式碼必須變更預設字型<xref:System.Drawing.SystemFonts.IconTitleFont%2A>來回應以字型大小的變更。</span><span class="sxs-lookup"><span data-stu-id="707f1-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="707f1-110">使用桌面的字型和回應的字型配置變更</span><span class="sxs-lookup"><span data-stu-id="707f1-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1.  <span data-ttu-id="707f1-111">建立您的表單，並加入您想要的控制項。</span><span class="sxs-lookup"><span data-stu-id="707f1-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="707f1-112">如需詳細資訊，請參閱[How to： 從命令列建立 Windows Forms 應用程式](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md)和[Windows Form 上使用的控制項](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="707f1-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="707f1-113">將參考加入<xref:Microsoft.Win32>您的程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="707f1-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="707f1-114">將下列程式碼加入至表單連結所需的事件處理常式，並變更表單的使用中的預設字型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="707f1-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="707f1-115">實作的處理常式<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>事件，讓自動縮放表單時<xref:Microsoft.Win32.UserPreferenceCategory.Window>類別目錄的變更。</span><span class="sxs-lookup"><span data-stu-id="707f1-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  <span data-ttu-id="707f1-116">最後，實作的處理常式<xref:System.Windows.Forms.Form.FormClosing>中斷連結的事件<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="707f1-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="707f1-117">包括此程式碼的失敗會導致您的應用程式會造成記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="707f1-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  <span data-ttu-id="707f1-118">編譯並執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="707f1-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="707f1-119">若要手動變更在 Windows XP 中的字型配置</span><span class="sxs-lookup"><span data-stu-id="707f1-119">To manually change the font scheme in Windows XP</span></span>  
  
1.  <span data-ttu-id="707f1-120">當 Windows Forms 應用程式正在執行時，以滑鼠右鍵按一下 Windows 桌面上，然後選擇 **屬性**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="707f1-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="707f1-121">在**顯示屬性**對話方塊中，按一下 [**外觀**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="707f1-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3.  <span data-ttu-id="707f1-122">從**字型大小**下拉式清單方塊中，選取新字型的大小。</span><span class="sxs-lookup"><span data-stu-id="707f1-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="707f1-123">您會發現表單回應執行階段變更桌面的字型配置中。</span><span class="sxs-lookup"><span data-stu-id="707f1-123">You will notice that the form now reacts to run time changes in the desktop font scheme.</span></span> <span data-ttu-id="707f1-124">當使用者變更之間**一般**，**大字型**，和**超大型字**，變更字型的表單，並正確地進行縮放。</span><span class="sxs-lookup"><span data-stu-id="707f1-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="707f1-125">範例</span><span class="sxs-lookup"><span data-stu-id="707f1-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="707f1-126">在此程式碼範例 constructer 包含呼叫`InitializeComponent`，也就是當您在 Visual Studio 中建立新的 Windows Form 專案時定義。</span><span class="sxs-lookup"><span data-stu-id="707f1-126">The constructer in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="707f1-127">如果您要建置命令列上的應用程式，請移除這行程式碼。</span><span class="sxs-lookup"><span data-stu-id="707f1-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707f1-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="707f1-128">See Also</span></span>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [<span data-ttu-id="707f1-129">Windows Forms 中的自動縮放比例</span><span class="sxs-lookup"><span data-stu-id="707f1-129">Automatic Scaling in Windows Forms</span></span>](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
