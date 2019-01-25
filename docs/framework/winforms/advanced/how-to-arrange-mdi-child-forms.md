---
title: HOW TO：排列 MDI 子表單
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
ms.openlocfilehash: 6e1e4f22aa70d8ee4d4122f9e77427c101b6713f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540737"
---
# <a name="how-to-arrange-mdi-child-forms"></a><span data-ttu-id="259ce-102">HOW TO：排列 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="259ce-102">How to: Arrange MDI Child Forms</span></span>
<span data-ttu-id="259ce-103">應用程式通常會包含 [並排]、[重疊顯示] 和 [排列] 等動作的功能表命令，以便控制所開啟之 MDI 子表單的配置。</span><span class="sxs-lookup"><span data-stu-id="259ce-103">Often, applications will have menu commands for actions such as Tile, Cascade, and Arrange, which control the layout of the open MDI child forms.</span></span> <span data-ttu-id="259ce-104">您可以搭配使用 <xref:System.Windows.Forms.Form.LayoutMdi%2A> 方法和其中一個 <xref:System.Windows.Forms.MdiLayout> 列舉值，來重新排列 MDI 父表單中的子表單。</span><span class="sxs-lookup"><span data-stu-id="259ce-104">You can use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method with one of the <xref:System.Windows.Forms.MdiLayout> enumeration values to rearrange the child forms in an MDI parent form.</span></span>  
  
 <span data-ttu-id="259ce-105"><xref:System.Windows.Forms.MdiLayout> 列舉值會以重疊顯示、水平或垂直並排方式來顯示子表單，或將子表單當做排列在 MDI 表單下方的子表單圖示來顯示。</span><span class="sxs-lookup"><span data-stu-id="259ce-105">The <xref:System.Windows.Forms.MdiLayout> enumeration values display child forms as cascading, as horizontally or vertically tiled, or as child form icons arranged along the lower portion of the MDI form.</span></span> <span data-ttu-id="259ce-106">這些值有相同的效果，為 Windows 命令**重疊顯示視窗**，**並排顯示視窗**，**堆疊顯示視窗**，和**顯示桌面**分別。</span><span class="sxs-lookup"><span data-stu-id="259ce-106">These values have the same effect as the Windows commands **Cascade windows**, **Show windows side by side**, **Show windows stacked**, and **Show the desktop**, respectively.</span></span>  
  
 <span data-ttu-id="259ce-107">這些方法通常會當做由功能表項目的 <xref:System.Windows.Forms.Control.Click> 事件所呼叫的事件處理常式來使用。</span><span class="sxs-lookup"><span data-stu-id="259ce-107">Often, these methods are used as the event handlers called by a menu item's <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="259ce-108">如此一來，具有「重疊顯示視窗」文字的功能表項目就可在 MDI 子視窗上呈現出指定的效果。</span><span class="sxs-lookup"><span data-stu-id="259ce-108">In this way, a menu item with the text "Cascade Windows" can have the desired effect on the MDI child windows.</span></span>  
  
### <a name="to-arrange-child-forms"></a><span data-ttu-id="259ce-109">排列子表單</span><span class="sxs-lookup"><span data-stu-id="259ce-109">To arrange child forms</span></span>  
  
1.  <span data-ttu-id="259ce-110">在方法中，使用 <xref:System.Windows.Forms.Form.LayoutMdi%2A> 方法設定 MDI 父表單的 <xref:System.Windows.Forms.MdiLayout> 列舉。</span><span class="sxs-lookup"><span data-stu-id="259ce-110">In a method, use the <xref:System.Windows.Forms.Form.LayoutMdi%2A> method to set the <xref:System.Windows.Forms.MdiLayout> enumeration for the MDI parent form.</span></span> <span data-ttu-id="259ce-111">下列範例針對 MDI 父表單 (<xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType>) 的子視窗，使用 `Form1` 列舉值。</span><span class="sxs-lookup"><span data-stu-id="259ce-111">The following example uses the <xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType> enumeration value for the child windows of the MDI parent form (`Form1`).</span></span> <span data-ttu-id="259ce-112">列舉型別會使用於程式碼中的事件處理常式<xref:System.Windows.Forms.Control.Click>事件的**串聯 Windows**功能表項目。</span><span class="sxs-lookup"><span data-stu-id="259ce-112">The enumeration is used in code during the event handler for the <xref:System.Windows.Forms.Control.Click> event of the **Cascade Windows** menu item.</span></span>  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="259ce-113">您也可以藉由變更所使用的 <xref:System.Windows.Forms.MdiLayout> 列舉值，來並排顯示視窗，以及將視窗排列為圖示。</span><span class="sxs-lookup"><span data-stu-id="259ce-113">You can also tile windows and arranging windows as icons by changing the <xref:System.Windows.Forms.MdiLayout> enumeration value used.</span></span>  
  
2.  <span data-ttu-id="259ce-114">如果使用 Visual C#，請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="259ce-114">If you’re using Visual C#, place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="259ce-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="259ce-115">See also</span></span>
- [<span data-ttu-id="259ce-116">多重文件介面 (MDI) 應用程式</span><span class="sxs-lookup"><span data-stu-id="259ce-116">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="259ce-117">如何：建立 MDI 父表單</span><span class="sxs-lookup"><span data-stu-id="259ce-117">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="259ce-118">如何：建立 MDI 子表單</span><span class="sxs-lookup"><span data-stu-id="259ce-118">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="259ce-119">如何：決定作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="259ce-119">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="259ce-120">如何：將資料傳送至作用中的 MDI 子系</span><span class="sxs-lookup"><span data-stu-id="259ce-120">How to: Send Data to the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
