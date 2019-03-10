---
title: 逐步解說：建立可存取的 Windows 架構應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: b27203f46c1d89577825e40541d9789d3b9e17de
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708271"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="93580-102">逐步解說：建立可存取的 Windows 架構應用程式</span><span class="sxs-lookup"><span data-stu-id="93580-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="93580-103">建立協助工具應用程式具有重要的商業含意，</span><span class="sxs-lookup"><span data-stu-id="93580-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="93580-104">許多政府對於市售軟體訂定有協助工具法規，</span><span class="sxs-lookup"><span data-stu-id="93580-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="93580-105">而擁有「Windows 憑證」標誌就表示符合有關協助工具的要求。</span><span class="sxs-lookup"><span data-stu-id="93580-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="93580-106">據估計光是美國便有約三千萬居民受到軟體協助工具的影響，而其中大部分是潛在客戶。</span><span class="sxs-lookup"><span data-stu-id="93580-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="93580-107">本逐步解說將提出「Windows 憑證」標誌的五項協助工具需求。</span><span class="sxs-lookup"><span data-stu-id="93580-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="93580-108">根據這些需求，協助工具應用程式將會：</span><span class="sxs-lookup"><span data-stu-id="93580-108">According to these requirements, an accessible application will:</span></span>  
  
-   <span data-ttu-id="93580-109">支援 [控制台] 的大小、色彩、字型和輸入設定。</span><span class="sxs-lookup"><span data-stu-id="93580-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="93580-110">當使用者變更 [控制台] 的設定時，功能表列、標題列、框線和狀態列的大小也會隨著調整。</span><span class="sxs-lookup"><span data-stu-id="93580-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="93580-111">不需要在這個應用程式中對控制項或程式碼進行其他變更。</span><span class="sxs-lookup"><span data-stu-id="93580-111">No additional changes to the controls or code are required in this application.</span></span>  
  
-   <span data-ttu-id="93580-112">支援高對比模式。</span><span class="sxs-lookup"><span data-stu-id="93580-112">Support High Contrast mode.</span></span>  
  
-   <span data-ttu-id="93580-113">提供具備輔助說明的所有功能鍵盤存取。</span><span class="sxs-lookup"><span data-stu-id="93580-113">Provide documented keyboard access to all features.</span></span>  
  
-   <span data-ttu-id="93580-114">以視覺呈現和程式設計方式顯示鍵盤焦點的位置。</span><span class="sxs-lookup"><span data-stu-id="93580-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
-   <span data-ttu-id="93580-115">避免只以音效傳達重要資訊。</span><span class="sxs-lookup"><span data-stu-id="93580-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="93580-116">如需詳細資訊，請參閱[設計可及性應用程式的資源](/visualstudio/ide/reference/resources-for-designing-accessible-applications)。</span><span class="sxs-lookup"><span data-stu-id="93580-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="93580-117">如需支援各種鍵盤配置的資訊，請參閱[開發世界性的應用程式的最佳做法](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="93580-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="93580-118">建立專案</span><span class="sxs-lookup"><span data-stu-id="93580-118">Creating the Project</span></span>  
 <span data-ttu-id="93580-119">本逐步解說會建立一個接受披薩訂單的應用程式使用者介面，</span><span class="sxs-lookup"><span data-stu-id="93580-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="93580-120">其中包含輸入顧客名稱的 <xref:System.Windows.Forms.TextBox>、選取披薩尺寸的 <xref:System.Windows.Forms.RadioButton> 群組、選取配料的 <xref:System.Windows.Forms.CheckedListBox>、兩個標示為 [訂購] 和 [取消] 的 Button 控制項，以及一個含有結束命令的功能表。</span><span class="sxs-lookup"><span data-stu-id="93580-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="93580-121">使用者會輸入顧客名稱、披薩尺寸和想要的配料。</span><span class="sxs-lookup"><span data-stu-id="93580-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="93580-122">當使用者按一下 [訂購] 按鈕時，訊息方塊中會顯示訂單摘要及其費用，然後會清除控制項並準備接受下一筆訂單。</span><span class="sxs-lookup"><span data-stu-id="93580-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="93580-123">當使用者按一下 [取消] 按鈕時，會清除控制項並準備接受下一筆訂單。</span><span class="sxs-lookup"><span data-stu-id="93580-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="93580-124">當使用者按一下 [結束] 功能表項目時，程式會關閉。</span><span class="sxs-lookup"><span data-stu-id="93580-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="93580-125">本逐步解說的重點不在於零售訂單系統的程式碼，而是在於使用者介面的協助工具。</span><span class="sxs-lookup"><span data-stu-id="93580-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="93580-126">本逐步解說示範數個常用控制項的協助工具功能，這些控制項包括按鈕、選項按鈕、文字方塊和標籤。</span><span class="sxs-lookup"><span data-stu-id="93580-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="93580-127">開始建立應用程式</span><span class="sxs-lookup"><span data-stu-id="93580-127">To begin making the application</span></span>  
  
-   <span data-ttu-id="93580-128">建立新的 Windows 應用程式在 Visual Basic 或 Visual C#。</span><span class="sxs-lookup"><span data-stu-id="93580-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="93580-129">將專案命名為 **PizzaOrder**</span><span class="sxs-lookup"><span data-stu-id="93580-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="93580-130">(如需詳細資訊，請參閱[建立新的方案和專案](/visualstudio/ide/creating-solutions-and-projects))。</span><span class="sxs-lookup"><span data-stu-id="93580-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="93580-131">將控制項加入表單</span><span class="sxs-lookup"><span data-stu-id="93580-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="93580-132">將控制項加入表單時，請注意下列建立協助工具應用程式的方針：</span><span class="sxs-lookup"><span data-stu-id="93580-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
-   <span data-ttu-id="93580-133">設定 <xref:System.Windows.Forms.Control.AccessibleDescription%2A> 和 <xref:System.Windows.Forms.Control.AccessibleName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="93580-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="93580-134">在這個範例中，<xref:System.Windows.Forms.Control.AccessibleRole%2A> 的預設值便已足夠。</span><span class="sxs-lookup"><span data-stu-id="93580-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="93580-135">如需協助工具屬性的詳細資訊，請參閱[提供 Windows Forms 上控制項的協助工具資訊](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md)。</span><span class="sxs-lookup"><span data-stu-id="93580-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
-   <span data-ttu-id="93580-136">將字型大小設定為 10 或更大的點數。</span><span class="sxs-lookup"><span data-stu-id="93580-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93580-137">如果您一開始將表單的字型大小設定為 10，之後加入表單之所有控制項的字型大小都將是 10。</span><span class="sxs-lookup"><span data-stu-id="93580-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
-   <span data-ttu-id="93580-138">確定任何描述 TextBox 控制項的 Label 控制項都是依定位順序，緊接著位於 TextBox 控制項之前。</span><span class="sxs-lookup"><span data-stu-id="93580-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
-   <span data-ttu-id="93580-139">使用 "&" 字元，將便捷鍵加入使用者可能想要巡覽之任何控制項的 <xref:System.Windows.Forms.Control.Text%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="93580-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
-   <span data-ttu-id="93580-140">使用 "&" 字元，將便捷鍵加入使用者可能想要巡覽的控制項前面之標籤的 <xref:System.Windows.Forms.Control.Text%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="93580-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="93580-141">將標籤的 <xref:System.Windows.Forms.Label.UseMnemonic%2A> 屬性設定為 `true`如此一來，當使用者按下便捷鍵時，焦點便會設定為定位順序的下一個控制項。</span><span class="sxs-lookup"><span data-stu-id="93580-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
-   <span data-ttu-id="93580-142">將便捷鍵加入所有功能表項目。</span><span class="sxs-lookup"><span data-stu-id="93580-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="93580-143">讓 Windows 應用程式具備協助功能</span><span class="sxs-lookup"><span data-stu-id="93580-143">To make your Windows Application accessible</span></span>  
  
-   <span data-ttu-id="93580-144">如下所述將控制項加入表單並設定屬性。</span><span class="sxs-lookup"><span data-stu-id="93580-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="93580-145">如需如何在表單上排列控制項的模型，請參閱表格下方的圖片。</span><span class="sxs-lookup"><span data-stu-id="93580-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="93580-146">物件</span><span class="sxs-lookup"><span data-stu-id="93580-146">Object</span></span>|<span data-ttu-id="93580-147">屬性</span><span class="sxs-lookup"><span data-stu-id="93580-147">Property</span></span>|<span data-ttu-id="93580-148">值</span><span class="sxs-lookup"><span data-stu-id="93580-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="93580-149">Form1</span><span class="sxs-lookup"><span data-stu-id="93580-149">Form1</span></span>|<span data-ttu-id="93580-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-150">AccessibleDescription</span></span>|<span data-ttu-id="93580-151">訂購表單</span><span class="sxs-lookup"><span data-stu-id="93580-151">Order form</span></span>|  
    ||<span data-ttu-id="93580-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-152">AccessibleName</span></span>|<span data-ttu-id="93580-153">訂購表單</span><span class="sxs-lookup"><span data-stu-id="93580-153">Order form</span></span>|  
    ||<span data-ttu-id="93580-154">字型大小</span><span class="sxs-lookup"><span data-stu-id="93580-154">Font Size</span></span>|<span data-ttu-id="93580-155">10</span><span class="sxs-lookup"><span data-stu-id="93580-155">10</span></span>|  
    ||<span data-ttu-id="93580-156">Text</span><span class="sxs-lookup"><span data-stu-id="93580-156">Text</span></span>|<span data-ttu-id="93580-157">比薩訂購表單</span><span class="sxs-lookup"><span data-stu-id="93580-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="93580-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="93580-158">PictureBox</span></span>|<span data-ttu-id="93580-159">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-159">Name</span></span>|<span data-ttu-id="93580-160">標誌</span><span class="sxs-lookup"><span data-stu-id="93580-160">logo</span></span>|  
    ||<span data-ttu-id="93580-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-161">AccessibleDescription</span></span>|<span data-ttu-id="93580-162">一片披薩</span><span class="sxs-lookup"><span data-stu-id="93580-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="93580-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-163">AccessibleName</span></span>|<span data-ttu-id="93580-164">公司標誌</span><span class="sxs-lookup"><span data-stu-id="93580-164">Company logo</span></span>|  
    ||<span data-ttu-id="93580-165">Image</span><span class="sxs-lookup"><span data-stu-id="93580-165">Image</span></span>|<span data-ttu-id="93580-166">任何圖示或點陣圖</span><span class="sxs-lookup"><span data-stu-id="93580-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="93580-167">標籤</span><span class="sxs-lookup"><span data-stu-id="93580-167">Label</span></span>|<span data-ttu-id="93580-168">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-168">Name</span></span>|<span data-ttu-id="93580-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="93580-169">companyLabel</span></span>|  
    ||<span data-ttu-id="93580-170">Text</span><span class="sxs-lookup"><span data-stu-id="93580-170">Text</span></span>|<span data-ttu-id="93580-171">好吃披薩</span><span class="sxs-lookup"><span data-stu-id="93580-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="93580-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-172">TabIndex</span></span>|<span data-ttu-id="93580-173">1</span><span class="sxs-lookup"><span data-stu-id="93580-173">1</span></span>|  
    ||<span data-ttu-id="93580-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-174">AccessibleDescription</span></span>|<span data-ttu-id="93580-175">公司名稱</span><span class="sxs-lookup"><span data-stu-id="93580-175">Company name</span></span>|  
    ||<span data-ttu-id="93580-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-176">AccessibleName</span></span>|<span data-ttu-id="93580-177">公司名稱</span><span class="sxs-lookup"><span data-stu-id="93580-177">Company name</span></span>|  
    ||<span data-ttu-id="93580-178">Backcolor</span><span class="sxs-lookup"><span data-stu-id="93580-178">Backcolor</span></span>|<span data-ttu-id="93580-179">藍色</span><span class="sxs-lookup"><span data-stu-id="93580-179">Blue</span></span>|  
    ||<span data-ttu-id="93580-180">Forecolor</span><span class="sxs-lookup"><span data-stu-id="93580-180">Forecolor</span></span>|<span data-ttu-id="93580-181">黃色</span><span class="sxs-lookup"><span data-stu-id="93580-181">Yellow</span></span>|  
    ||<span data-ttu-id="93580-182">Font size</span><span class="sxs-lookup"><span data-stu-id="93580-182">Font size</span></span>|<span data-ttu-id="93580-183">18</span><span class="sxs-lookup"><span data-stu-id="93580-183">18</span></span>|  
    |<span data-ttu-id="93580-184">標籤</span><span class="sxs-lookup"><span data-stu-id="93580-184">Label</span></span>|<span data-ttu-id="93580-185">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-185">Name</span></span>|<span data-ttu-id="93580-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="93580-186">customerLabel</span></span>|  
    ||<span data-ttu-id="93580-187">Text</span><span class="sxs-lookup"><span data-stu-id="93580-187">Text</span></span>|<span data-ttu-id="93580-188">名稱(&N)</span><span class="sxs-lookup"><span data-stu-id="93580-188">&Name</span></span>|  
    ||<span data-ttu-id="93580-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-189">TabIndex</span></span>|<span data-ttu-id="93580-190">2</span><span class="sxs-lookup"><span data-stu-id="93580-190">2</span></span>|  
    ||<span data-ttu-id="93580-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-191">AccessibleDescription</span></span>|<span data-ttu-id="93580-192">顧客名稱標籤</span><span class="sxs-lookup"><span data-stu-id="93580-192">Customer name label</span></span>|  
    ||<span data-ttu-id="93580-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-193">AccessibleName</span></span>|<span data-ttu-id="93580-194">顧客名稱標籤</span><span class="sxs-lookup"><span data-stu-id="93580-194">Customer name label</span></span>|  
    ||<span data-ttu-id="93580-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="93580-195">UseMnemonic</span></span>|<span data-ttu-id="93580-196">True</span><span class="sxs-lookup"><span data-stu-id="93580-196">True</span></span>|  
    |<span data-ttu-id="93580-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="93580-197">TextBox</span></span>|<span data-ttu-id="93580-198">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-198">Name</span></span>|<span data-ttu-id="93580-199">customerName</span><span class="sxs-lookup"><span data-stu-id="93580-199">customerName</span></span>|  
    ||<span data-ttu-id="93580-200">Text</span><span class="sxs-lookup"><span data-stu-id="93580-200">Text</span></span>|<span data-ttu-id="93580-201">(無)</span><span class="sxs-lookup"><span data-stu-id="93580-201">(none)</span></span>|  
    ||<span data-ttu-id="93580-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-202">TabIndex</span></span>|<span data-ttu-id="93580-203">3</span><span class="sxs-lookup"><span data-stu-id="93580-203">3</span></span>|  
    ||<span data-ttu-id="93580-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-204">AccessibleDescription</span></span>|<span data-ttu-id="93580-205">顧客名稱</span><span class="sxs-lookup"><span data-stu-id="93580-205">Customer name</span></span>|  
    ||<span data-ttu-id="93580-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-206">AccessibleName</span></span>|<span data-ttu-id="93580-207">顧客名稱</span><span class="sxs-lookup"><span data-stu-id="93580-207">Customer name</span></span>|  
    |<span data-ttu-id="93580-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="93580-208">GroupBox</span></span>|<span data-ttu-id="93580-209">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-209">Name</span></span>|<span data-ttu-id="93580-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="93580-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="93580-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-211">AccessibleDescription</span></span>|<span data-ttu-id="93580-212">披薩尺寸選擇</span><span class="sxs-lookup"><span data-stu-id="93580-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="93580-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-213">AccessibleName</span></span>|<span data-ttu-id="93580-214">披薩尺寸選擇</span><span class="sxs-lookup"><span data-stu-id="93580-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="93580-215">Text</span><span class="sxs-lookup"><span data-stu-id="93580-215">Text</span></span>|<span data-ttu-id="93580-216">披薩尺寸</span><span class="sxs-lookup"><span data-stu-id="93580-216">Pizza size</span></span>|  
    ||<span data-ttu-id="93580-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-217">TabIndex</span></span>|<span data-ttu-id="93580-218">4</span><span class="sxs-lookup"><span data-stu-id="93580-218">4</span></span>|  
    |<span data-ttu-id="93580-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="93580-219">RadioButton</span></span>|<span data-ttu-id="93580-220">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-220">Name</span></span>|<span data-ttu-id="93580-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="93580-221">smallPizza</span></span>|  
    ||<span data-ttu-id="93580-222">Text</span><span class="sxs-lookup"><span data-stu-id="93580-222">Text</span></span>|<span data-ttu-id="93580-223">小披薩美金 $6.00 元(&S)</span><span class="sxs-lookup"><span data-stu-id="93580-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="93580-224">已核取</span><span class="sxs-lookup"><span data-stu-id="93580-224">Checked</span></span>|<span data-ttu-id="93580-225">True</span><span class="sxs-lookup"><span data-stu-id="93580-225">True</span></span>|  
    ||<span data-ttu-id="93580-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-226">TabIndex</span></span>|<span data-ttu-id="93580-227">0</span><span class="sxs-lookup"><span data-stu-id="93580-227">0</span></span>|  
    ||<span data-ttu-id="93580-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-228">AccessibleDescription</span></span>|<span data-ttu-id="93580-229">小披薩</span><span class="sxs-lookup"><span data-stu-id="93580-229">Small pizza</span></span>|  
    ||<span data-ttu-id="93580-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-230">AccessibleName</span></span>|<span data-ttu-id="93580-231">小披薩</span><span class="sxs-lookup"><span data-stu-id="93580-231">Small pizza</span></span>|  
    |<span data-ttu-id="93580-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="93580-232">RadioButton</span></span>|<span data-ttu-id="93580-233">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-233">Name</span></span>|<span data-ttu-id="93580-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="93580-234">largePizza</span></span>|  
    ||<span data-ttu-id="93580-235">Text</span><span class="sxs-lookup"><span data-stu-id="93580-235">Text</span></span>|<span data-ttu-id="93580-236">大批薩美金 $10.00 元(&L)</span><span class="sxs-lookup"><span data-stu-id="93580-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="93580-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-237">TabIndex</span></span>|<span data-ttu-id="93580-238">1</span><span class="sxs-lookup"><span data-stu-id="93580-238">1</span></span>|  
    ||<span data-ttu-id="93580-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-239">AccessibleDescription</span></span>|<span data-ttu-id="93580-240">大批薩</span><span class="sxs-lookup"><span data-stu-id="93580-240">Large pizza</span></span>|  
    ||<span data-ttu-id="93580-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-241">AccessibleName</span></span>|<span data-ttu-id="93580-242">大批薩</span><span class="sxs-lookup"><span data-stu-id="93580-242">Large pizza</span></span>|  
    |<span data-ttu-id="93580-243">標籤</span><span class="sxs-lookup"><span data-stu-id="93580-243">Label</span></span>|<span data-ttu-id="93580-244">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-244">Name</span></span>|<span data-ttu-id="93580-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="93580-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="93580-246">Text</span><span class="sxs-lookup"><span data-stu-id="93580-246">Text</span></span>|<span data-ttu-id="93580-247">配料 (每份美金 $0.75 元)(&T)</span><span class="sxs-lookup"><span data-stu-id="93580-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="93580-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-248">TabIndex</span></span>|<span data-ttu-id="93580-249">5</span><span class="sxs-lookup"><span data-stu-id="93580-249">5</span></span>|  
    ||<span data-ttu-id="93580-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-250">AccessibleDescription</span></span>|<span data-ttu-id="93580-251">配料標籤</span><span class="sxs-lookup"><span data-stu-id="93580-251">Toppings label</span></span>|  
    ||<span data-ttu-id="93580-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-252">AccessibleName</span></span>|<span data-ttu-id="93580-253">配料標籤</span><span class="sxs-lookup"><span data-stu-id="93580-253">Toppings label</span></span>|  
    ||<span data-ttu-id="93580-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="93580-254">UseMnemonic</span></span>|<span data-ttu-id="93580-255">True</span><span class="sxs-lookup"><span data-stu-id="93580-255">True</span></span>|  
    |<span data-ttu-id="93580-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="93580-256">CheckedListBox</span></span>|<span data-ttu-id="93580-257">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-257">Name</span></span>|<span data-ttu-id="93580-258">配料</span><span class="sxs-lookup"><span data-stu-id="93580-258">toppings</span></span>|  
    ||<span data-ttu-id="93580-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-259">TabIndex</span></span>|<span data-ttu-id="93580-260">6</span><span class="sxs-lookup"><span data-stu-id="93580-260">6</span></span>|  
    ||<span data-ttu-id="93580-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-261">AccessibleDescription</span></span>|<span data-ttu-id="93580-262">可供選擇的配料</span><span class="sxs-lookup"><span data-stu-id="93580-262">Available toppings</span></span>|  
    ||<span data-ttu-id="93580-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-263">AccessibleName</span></span>|<span data-ttu-id="93580-264">可供選擇的配料</span><span class="sxs-lookup"><span data-stu-id="93580-264">Available toppings</span></span>|  
    ||<span data-ttu-id="93580-265">項目</span><span class="sxs-lookup"><span data-stu-id="93580-265">Items</span></span>|<span data-ttu-id="93580-266">辣肉腸、臘腸、蘑菇</span><span class="sxs-lookup"><span data-stu-id="93580-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="93580-267">按鈕</span><span class="sxs-lookup"><span data-stu-id="93580-267">Button</span></span>|<span data-ttu-id="93580-268">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-268">Name</span></span>|<span data-ttu-id="93580-269">順序</span><span class="sxs-lookup"><span data-stu-id="93580-269">order</span></span>|  
    ||<span data-ttu-id="93580-270">Text</span><span class="sxs-lookup"><span data-stu-id="93580-270">Text</span></span>|<span data-ttu-id="93580-271">順序(&O)</span><span class="sxs-lookup"><span data-stu-id="93580-271">&Order</span></span>|  
    ||<span data-ttu-id="93580-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-272">TabIndex</span></span>|<span data-ttu-id="93580-273">7</span><span class="sxs-lookup"><span data-stu-id="93580-273">7</span></span>|  
    ||<span data-ttu-id="93580-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-274">AccessibleDescription</span></span>|<span data-ttu-id="93580-275">合計訂單</span><span class="sxs-lookup"><span data-stu-id="93580-275">Total the order</span></span>|  
    ||<span data-ttu-id="93580-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-276">AccessibleName</span></span>|<span data-ttu-id="93580-277">訂單總計</span><span class="sxs-lookup"><span data-stu-id="93580-277">Total order</span></span>|  
    |<span data-ttu-id="93580-278">按鈕</span><span class="sxs-lookup"><span data-stu-id="93580-278">Button</span></span>|<span data-ttu-id="93580-279">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-279">Name</span></span>|<span data-ttu-id="93580-280">cancel</span><span class="sxs-lookup"><span data-stu-id="93580-280">cancel</span></span>|  
    ||<span data-ttu-id="93580-281">Text</span><span class="sxs-lookup"><span data-stu-id="93580-281">Text</span></span>|<span data-ttu-id="93580-282">取消(&C)</span><span class="sxs-lookup"><span data-stu-id="93580-282">&Cancel</span></span>|  
    ||<span data-ttu-id="93580-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="93580-283">TabIndex</span></span>|<span data-ttu-id="93580-284">8</span><span class="sxs-lookup"><span data-stu-id="93580-284">8</span></span>|  
    ||<span data-ttu-id="93580-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="93580-285">AccessibleDescription</span></span>|<span data-ttu-id="93580-286">取消訂單</span><span class="sxs-lookup"><span data-stu-id="93580-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="93580-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="93580-287">AccessibleName</span></span>|<span data-ttu-id="93580-288">取消訂單</span><span class="sxs-lookup"><span data-stu-id="93580-288">Cancel order</span></span>|  
    |<span data-ttu-id="93580-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="93580-289">MainMenu</span></span>|<span data-ttu-id="93580-290">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-290">Name</span></span>|<span data-ttu-id="93580-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="93580-291">theMainMenu</span></span>|  
    |<span data-ttu-id="93580-292">MenuItem</span><span class="sxs-lookup"><span data-stu-id="93580-292">MenuItem</span></span>|<span data-ttu-id="93580-293">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-293">Name</span></span>|<span data-ttu-id="93580-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="93580-294">fileCommands</span></span>|  
    ||<span data-ttu-id="93580-295">Text</span><span class="sxs-lookup"><span data-stu-id="93580-295">Text</span></span>|<span data-ttu-id="93580-296">檔案(&F)</span><span class="sxs-lookup"><span data-stu-id="93580-296">&File</span></span>|  
    |<span data-ttu-id="93580-297">MenuItem</span><span class="sxs-lookup"><span data-stu-id="93580-297">MenuItem</span></span>|<span data-ttu-id="93580-298">名稱</span><span class="sxs-lookup"><span data-stu-id="93580-298">Name</span></span>|<span data-ttu-id="93580-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="93580-299">exitApp</span></span>|  
    ||<span data-ttu-id="93580-300">Text</span><span class="sxs-lookup"><span data-stu-id="93580-300">Text</span></span>|<span data-ttu-id="93580-301">結束(&X)</span><span class="sxs-lookup"><span data-stu-id="93580-301">E&xit</span></span>|  
  
     <span data-ttu-id="93580-302">![比薩訂購表單](./media/vbpizzaorderform.gif "vbPizzaOrderForm")</span><span class="sxs-lookup"><span data-stu-id="93580-302">![Pizza Order Form](./media/vbpizzaorderform.gif "vbPizzaOrderForm")</span></span>  
<span data-ttu-id="93580-303">您的表單看起來會如下所示：</span><span class="sxs-lookup"><span data-stu-id="93580-303">Your form will look something like the following:</span></span>  
  
## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="93580-304">支援高對比模式</span><span class="sxs-lookup"><span data-stu-id="93580-304">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="93580-305">高對比模式是 Windows 系統的一項設定，使用對比色彩和字型大小以提升可讀性，對於視覺受損的使用者很有幫助。</span><span class="sxs-lookup"><span data-stu-id="93580-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="93580-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A>屬性可用來判斷是否已設定高對比模式。</span><span class="sxs-lookup"><span data-stu-id="93580-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="93580-307">如果 SystemInformation.HighContrast 為 `true`，應用程式應該：</span><span class="sxs-lookup"><span data-stu-id="93580-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
-   <span data-ttu-id="93580-308">使用系統色彩配置來顯示所有使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="93580-308">Display all user interface elements using the system color scheme</span></span>  
  
-   <span data-ttu-id="93580-309">藉由視覺提示或音效來傳達原本由色彩傳達的任何資訊。</span><span class="sxs-lookup"><span data-stu-id="93580-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="93580-310">例如，如果使用紅色字型醒目提示特定清單項目，您也可以將粗體套用至字型，讓使用者透過非色彩提示得知該項目已醒目提示。</span><span class="sxs-lookup"><span data-stu-id="93580-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
-   <span data-ttu-id="93580-311">省略文字後的任何影像或圖樣。</span><span class="sxs-lookup"><span data-stu-id="93580-311">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="93580-312">當應用程式啟動並回應 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 系統事件時，應該會檢查 <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> 的設定。</span><span class="sxs-lookup"><span data-stu-id="93580-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="93580-313">只要 <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> 的值變更，便會引發 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="93580-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="93580-314">在應用程式中，唯一不使用色彩系統設定的項目是 `lblCompanyName`。</span><span class="sxs-lookup"><span data-stu-id="93580-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="93580-315"><xref:System.Drawing.SystemColors>類別用來將標籤的色彩設定變更為使用者選取的系統色彩。</span><span class="sxs-lookup"><span data-stu-id="93580-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="93580-316">有效啟用高對比模式</span><span class="sxs-lookup"><span data-stu-id="93580-316">To enable High Contrast mode in an effective way</span></span>  
  
1.  <span data-ttu-id="93580-317">建立一個方法，將標籤的色彩設定為系統色彩。</span><span class="sxs-lookup"><span data-stu-id="93580-317">Create a method to set the colors of the label to the system colors.</span></span>  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
    private void SetColorScheme()  
    {  
       if (SystemInformation.HighContrast)  
       {  
          companyLabel.BackColor = SystemColors.Window;  
          companyLabel.ForeColor = SystemColors.WindowText;  
       }  
       else  
       {  
          companyLabel.BackColor = Color.Blue;  
          companyLabel.ForeColor = Color.Yellow;  
       }  
    }  
    ```  
  
2.  <span data-ttu-id="93580-318">在表單建構函式 (Visual Basic 中為 `Public Sub New()`，Visual C# 中為 `public class Form1`) 中呼叫 `SetColorScheme` 程序。</span><span class="sxs-lookup"><span data-stu-id="93580-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="93580-319">若要存取 Visual Basic 中的建構函式，您必須展開標示為 [Windows Forms 設計工具產生的程式碼] 的區域。</span><span class="sxs-lookup"><span data-stu-id="93580-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3.  <span data-ttu-id="93580-320">使用適當的簽章建立事件程序，以回應 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="93580-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4.  <span data-ttu-id="93580-321">呼叫 `InitializeComponents` 之後，在表單建構函式中新增程式碼，將事件程序與系統事件連結。</span><span class="sxs-lookup"><span data-stu-id="93580-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="93580-322">這個方法會呼叫 `SetColorScheme` 程序。</span><span class="sxs-lookup"><span data-stu-id="93580-322">This method calls the `SetColorScheme` procedure.</span></span>  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5.  <span data-ttu-id="93580-323">先將程式碼加入表單的 <xref:System.Windows.Forms.Control.Dispose%2A> 方法，再呼叫基底類別的 <xref:System.Windows.Forms.Control.Dispose%2A> 方法，以便在應用程式關閉時釋放事件。</span><span class="sxs-lookup"><span data-stu-id="93580-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="93580-324">若要存取 Visual Basic 中的 <xref:System.Windows.Forms.Control.Dispose%2A> 方法，您必須展開標示為 [Windows Form 設計工具產生的程式碼] 的區域。</span><span class="sxs-lookup"><span data-stu-id="93580-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93580-325">系統事件程式碼會執行獨立於主應用程式的執行緒。</span><span class="sxs-lookup"><span data-stu-id="93580-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="93580-326">如果您沒有釋放該事件，即使關閉程式之後，連結至該事件的程式碼仍會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="93580-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6.  <span data-ttu-id="93580-327">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="93580-327">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="93580-328">透過音效以外的其他方式傳達重要資訊</span><span class="sxs-lookup"><span data-stu-id="93580-328">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="93580-329">在這個應用程式中，資訊不只以音效傳達。</span><span class="sxs-lookup"><span data-stu-id="93580-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="93580-330">如果您在應用程式中使用音效，應該也可以使用其他方式來提供資訊。</span><span class="sxs-lookup"><span data-stu-id="93580-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="93580-331">透過音效以外的其他方式提供資訊</span><span class="sxs-lookup"><span data-stu-id="93580-331">To supply information by some other means than sound</span></span>  
  
1.  <span data-ttu-id="93580-332">使用 Windows 應用程式開發介面函式 FlashWindow 讓標題列閃爍。</span><span class="sxs-lookup"><span data-stu-id="93580-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="93580-333">如需如何呼叫 Windows API 函式的範例，請參閱[逐步解說：呼叫 Windows Api](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)。</span><span class="sxs-lookup"><span data-stu-id="93580-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93580-334">使用者可以啟動 Windows 聲音感測服務，當系統音效透過電腦內建喇叭播放時，同時能使視窗閃爍。</span><span class="sxs-lookup"><span data-stu-id="93580-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2.  <span data-ttu-id="93580-335">在非強制回應視窗中顯示重要資訊，讓使用者可以有所回應。</span><span class="sxs-lookup"><span data-stu-id="93580-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3.  <span data-ttu-id="93580-336">顯示取得鍵盤焦點的訊息方塊，</span><span class="sxs-lookup"><span data-stu-id="93580-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="93580-337">但是如果使用者可能會輸入資料，則應避免使用這個方法。</span><span class="sxs-lookup"><span data-stu-id="93580-337">Avoid this method when the user may be typing.</span></span>  
  
4.  <span data-ttu-id="93580-338">在工作列的狀態通知區域中顯示狀態標記。</span><span class="sxs-lookup"><span data-stu-id="93580-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="93580-339">如需詳細資訊，請參閱[如何：使用 Windows Forms NotifyIcon 元件將應用程式圖示新增至工作列](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md)。</span><span class="sxs-lookup"><span data-stu-id="93580-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="93580-340">測試應用程式</span><span class="sxs-lookup"><span data-stu-id="93580-340">Testing the Application</span></span>  
 <span data-ttu-id="93580-341">在部署應用程式之前，您應該測試已實作的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="93580-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="93580-342">測試協助工具功能</span><span class="sxs-lookup"><span data-stu-id="93580-342">To test accessibility features</span></span>  
  
1.  <span data-ttu-id="93580-343">若要測試鍵盤存取，請拔除滑鼠，然後只利用鍵盤逐一測試使用者介面中的每一項功能。</span><span class="sxs-lookup"><span data-stu-id="93580-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="93580-344">請確定所有工作都可以只使用鍵盤執行。</span><span class="sxs-lookup"><span data-stu-id="93580-344">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2.  <span data-ttu-id="93580-345">若要測試是否支援高對比，請在 [控制台] 中選擇協助工具選項圖示。</span><span class="sxs-lookup"><span data-stu-id="93580-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="93580-346">按一下 [顯示] 索引標籤，然後選取 [使用高對比] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="93580-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="93580-347">巡覽所有使用者介面項目，確保色彩和字型變更均已正確反映。</span><span class="sxs-lookup"><span data-stu-id="93580-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="93580-348">同時確保已省略文字後的影像或圖樣。</span><span class="sxs-lookup"><span data-stu-id="93580-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="93580-349">Windows NT 4 的 [控制台] 中並沒有協助工具選項圖示。</span><span class="sxs-lookup"><span data-stu-id="93580-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="93580-350">因此，這個變更 SystemInformation.HighContrast 設定的程序不適用於 Windows NT 4。</span><span class="sxs-lookup"><span data-stu-id="93580-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3.  <span data-ttu-id="93580-351">另外還有其他工具可以測試應用程式的協助工具。</span><span class="sxs-lookup"><span data-stu-id="93580-351">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4.  <span data-ttu-id="93580-352">若要測試鍵盤焦點的顯示，請執行放大鏡</span><span class="sxs-lookup"><span data-stu-id="93580-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="93580-353">(若要開啟 [放大鏡]，請按一下 [開始] 功能表，然後依序指向 [程式集]、[附屬應用程式] 和 [協助工具]，然後按一下 [放大鏡])。</span><span class="sxs-lookup"><span data-stu-id="93580-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="93580-354">同時使用鍵盤 Tab 鍵和滑鼠來巡覽使用者介面。</span><span class="sxs-lookup"><span data-stu-id="93580-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="93580-355">確保 [放大鏡] 正確追蹤所有巡覽。</span><span class="sxs-lookup"><span data-stu-id="93580-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5.  <span data-ttu-id="93580-356">若要測試螢幕項目的顯示，請執行 [檢查]，然後同時使用滑鼠和 TAB 鍵跳到每個項目。</span><span class="sxs-lookup"><span data-stu-id="93580-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="93580-357">針對 UI 中的每個物件，確保 [檢查] 視窗的 [名稱]、[狀態]、[角色]、[位置] 和 [值] 欄位所顯示的資訊，對使用者都是有意義的。</span><span class="sxs-lookup"><span data-stu-id="93580-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>
