---
title: 回應 Windows Forms 應用程式中的字型配置變更
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739222"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a><span data-ttu-id="b0271-102">如何：回應 Windows Forms 應用程式中的字型配置變更</span><span class="sxs-lookup"><span data-stu-id="b0271-102">How to: Respond to Font Scheme Changes in a Windows Forms Application</span></span>
<span data-ttu-id="b0271-103">在 Windows 作業系統中，使用者可以變更全系統的字型設定，讓預設字型顯示較大或較小。</span><span class="sxs-lookup"><span data-stu-id="b0271-103">In the Windows operating systems, a user can change the system-wide font settings to make the default font appear larger or smaller.</span></span> <span data-ttu-id="b0271-104">變更這些字型設定對於視力受損的使用者而言非常重要，而且需要較大的類型來讀取其螢幕上的文字。</span><span class="sxs-lookup"><span data-stu-id="b0271-104">Changing these font settings is critical for users who are visually impaired and require larger type to read the text on their screens.</span></span> <span data-ttu-id="b0271-105">您可以藉由增加或減少表單的大小，以及每次字型配置變更時包含的所有文字，來調整 Windows Forms 應用程式以回應這些變更。</span><span class="sxs-lookup"><span data-stu-id="b0271-105">You can adjust your Windows Forms application to react to these changes by increasing or decreasing the size of the form and all contained text whenever the font scheme changes.</span></span> <span data-ttu-id="b0271-106">如果您想要讓表單以動態方式容納字型大小的變更，您可以將程式碼加入至表單。</span><span class="sxs-lookup"><span data-stu-id="b0271-106">If you want your form to accommodate changes in font sizes dynamically, you can add code to your form.</span></span>  
  
 <span data-ttu-id="b0271-107">一般而言，Windows Forms 使用的預設字型是 `GetStockObject(DEFAULT_GUI_FONT)`的 <xref:Microsoft.Win32> 命名空間呼叫所傳回的字型。</span><span class="sxs-lookup"><span data-stu-id="b0271-107">Typically, the default font used by Windows Forms is the font returned by the <xref:Microsoft.Win32> namespace call to `GetStockObject(DEFAULT_GUI_FONT)`.</span></span> <span data-ttu-id="b0271-108">此呼叫傳回的字型只會在螢幕解析度變更時變更。</span><span class="sxs-lookup"><span data-stu-id="b0271-108">The font returned by this call only changes when the screen resolution changes.</span></span> <span data-ttu-id="b0271-109">如下列程式所示，您的程式碼必須將預設字型變更為 <xref:System.Drawing.SystemFonts.IconTitleFont%2A>，以回應字型大小的變更。</span><span class="sxs-lookup"><span data-stu-id="b0271-109">As shown in the following procedure, your code must change the default font to <xref:System.Drawing.SystemFonts.IconTitleFont%2A> to respond to changes in font size.</span></span>  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a><span data-ttu-id="b0271-110">若要使用桌面字型並回應字型配置變更</span><span class="sxs-lookup"><span data-stu-id="b0271-110">To use the desktop font and respond to font scheme changes</span></span>  
  
1. <span data-ttu-id="b0271-111">建立您的表單，並新增您想要的控制項。</span><span class="sxs-lookup"><span data-stu-id="b0271-111">Create your form, and add the controls you want to it.</span></span> <span data-ttu-id="b0271-112">如需詳細資訊，請參閱[如何：從命令列建立 Windows Forms 應用程式](how-to-create-a-windows-forms-application-from-the-command-line.md)和[要在 Windows Forms 上使用的控制項](./controls/controls-to-use-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="b0271-112">For more information, see [How to: Create a Windows Forms Application from the Command Line](how-to-create-a-windows-forms-application-from-the-command-line.md) and [Controls to Use on Windows Forms](./controls/controls-to-use-on-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="b0271-113">將 <xref:Microsoft.Win32> 命名空間的參考新增至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0271-113">Add a reference to the <xref:Microsoft.Win32> namespace to your code.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="b0271-114">將下列程式碼加入至表單的函式，以連結所需的事件處理常式，以及變更用於表單的預設字型。</span><span class="sxs-lookup"><span data-stu-id="b0271-114">Add the following code to the constructor of your form to hook up required event handlers, and to change the default font in use for the form.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="b0271-115">執行 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件的處理常式，讓表單在 <xref:Microsoft.Win32.UserPreferenceCategory.Window> 分類變更時自動調整。</span><span class="sxs-lookup"><span data-stu-id="b0271-115">Implement a handler for the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event that causes the form to scale automatically when the <xref:Microsoft.Win32.UserPreferenceCategory.Window> category changes.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. <span data-ttu-id="b0271-116">最後，針對卸離 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件處理常式的 <xref:System.Windows.Forms.Form.FormClosing> 事件，執行處理常式。</span><span class="sxs-lookup"><span data-stu-id="b0271-116">Finally, implement a handler for the <xref:System.Windows.Forms.Form.FormClosing> event that detaches the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event handler.</span></span>  
  
     > [!IMPORTANT]
     > <span data-ttu-id="b0271-117">若無法包含此程式碼，將會導致您的應用程式流失記憶體。</span><span class="sxs-lookup"><span data-stu-id="b0271-117">Failure to include this code will cause your application to leak memory.</span></span>  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. <span data-ttu-id="b0271-118">編譯並執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0271-118">Compile and run the code.</span></span>  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a><span data-ttu-id="b0271-119">手動變更 Windows XP 中的字型配置</span><span class="sxs-lookup"><span data-stu-id="b0271-119">To manually change the font scheme in Windows XP</span></span>  
  
1. <span data-ttu-id="b0271-120">當您的 Windows Forms 應用程式正在執行時，請以滑鼠右鍵按一下 Windows 桌面，然後從快捷方式功能表中選擇 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="b0271-120">While your Windows Forms application is running, right-click the Windows desktop and choose **Properties** from the shortcut menu.</span></span>  
  
2. <span data-ttu-id="b0271-121">在 [**顯示內容**] 對話方塊中，按一下 [**外觀**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b0271-121">In the **Display Properties** dialog box, click the **Appearance** tab.</span></span>  
  
3. <span data-ttu-id="b0271-122">從 [**字型大小**] 下拉式清單方塊中，選取新的字型大小。</span><span class="sxs-lookup"><span data-stu-id="b0271-122">From the **Font Size** drop-down list box, select a new font size.</span></span>  
  
     <span data-ttu-id="b0271-123">您會發現表單現在會回應桌面字型配置中的執行時間變更。</span><span class="sxs-lookup"><span data-stu-id="b0271-123">You'll notice that the form now reacts to run-time changes in the desktop font scheme.</span></span> <span data-ttu-id="b0271-124">當使用者在**標準**、**大**字型和**超大**字型之間變更時，表單會變更字型並正確縮放。</span><span class="sxs-lookup"><span data-stu-id="b0271-124">When the user changes between **Normal**, **Large Fonts**, and **Extra Large Fonts**, the form changes font and scales correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0271-125">範例</span><span class="sxs-lookup"><span data-stu-id="b0271-125">Example</span></span>  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 <span data-ttu-id="b0271-126">這個程式碼範例中的函式包含 `InitializeComponent`的呼叫，這是在 Visual Studio 中建立新的 Windows Forms 專案時所定義。</span><span class="sxs-lookup"><span data-stu-id="b0271-126">The constructor in this code example contains a call to `InitializeComponent`, which is defined when you create a new Windows Forms project in Visual Studio.</span></span> <span data-ttu-id="b0271-127">如果您要在命令列上建立應用程式，請移除這行程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0271-127">Remove this line of code if you are building your application on the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0271-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0271-128">See also</span></span>

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [<span data-ttu-id="b0271-129">Windows Forms 中的自動縮放比例</span><span class="sxs-lookup"><span data-stu-id="b0271-129">Automatic Scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
