---
title: 逐步解說：使用 MaskedTextBox 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182065"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="aa1e8-102">逐步解說：使用 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="aa1e8-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="aa1e8-103">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="aa1e8-103">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="aa1e8-104">初始化控制項<xref:System.Windows.Forms.MaskedTextBox></span><span class="sxs-lookup"><span data-stu-id="aa1e8-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
- <span data-ttu-id="aa1e8-105">當字元<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>不符合遮罩時，使用事件處理常式提醒使用者</span><span class="sxs-lookup"><span data-stu-id="aa1e8-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
- <span data-ttu-id="aa1e8-106">將類型分配給<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>屬性，<xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>並使用事件處理常式在使用者嘗試提交的值對類型無效時提醒使用者</span><span class="sxs-lookup"><span data-stu-id="aa1e8-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="aa1e8-107">創建專案和添加控制項</span><span class="sxs-lookup"><span data-stu-id="aa1e8-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="aa1e8-108">向表單添加蒙版文字方塊控制項</span><span class="sxs-lookup"><span data-stu-id="aa1e8-108">To add a MaskedTextBox control to your form</span></span>  
  
1. <span data-ttu-id="aa1e8-109">打開要在其上放置控制項的<xref:System.Windows.Forms.MaskedTextBox>表單。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2. <span data-ttu-id="aa1e8-110">將<xref:System.Windows.Forms.MaskedTextBox>控制項從**工具箱**拖動到表單。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3. <span data-ttu-id="aa1e8-111">按右鍵控制項並選擇 **"屬性**"。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="aa1e8-112">在 **"屬性"** 視窗中，選擇 **"蒙版"** 屬性，然後按一下屬性名稱旁邊的 **..."（** 省略號）按鈕。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4. <span data-ttu-id="aa1e8-113">在 **"輸入遮罩"** 對話方塊中，選擇 **"短日期**"蒙版，然後按一下 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5. <span data-ttu-id="aa1e8-114">在 **"屬性"** 視窗中將<xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A>屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="aa1e8-115">每次使用者嘗試輸入違反遮罩定義的字元時，此屬性都會發出短促的蜂鳴音。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="aa1e8-116">有關蒙版屬性支援的字元的摘要，請參閱<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>該屬性的備註部分。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="aa1e8-117">提醒使用者輸入錯誤</span><span class="sxs-lookup"><span data-stu-id="aa1e8-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="aa1e8-118">為被拒絕的蒙版輸入添加氣球提示</span><span class="sxs-lookup"><span data-stu-id="aa1e8-118">Add a balloon tip for rejected mask input</span></span>  
  
1. <span data-ttu-id="aa1e8-119">返回到**工具箱**並將 添加到<xref:System.Windows.Forms.ToolTip>表單中。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2. <span data-ttu-id="aa1e8-120">為<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>發生輸入錯誤時引發 的事件<xref:System.Windows.Forms.ToolTip>創建事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="aa1e8-121">氣球提示保持可見五秒，或直到使用者按一下它。</span><span class="sxs-lookup"><span data-stu-id="aa1e8-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="aa1e8-122">提醒使用者輸入無效類型</span><span class="sxs-lookup"><span data-stu-id="aa1e8-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="aa1e8-123">為無效資料類型添加氣球提示</span><span class="sxs-lookup"><span data-stu-id="aa1e8-123">Add a balloon tip for invalid data types</span></span>  
  
1. <span data-ttu-id="aa1e8-124">在<xref:System.Windows.Forms.Form.Load>表單的事件處理常式中，將表示<xref:System.Type><xref:System.DateTime>該類型的物件分配給<xref:System.Windows.Forms.MaskedTextBox>控制項的屬性： <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A></span><span class="sxs-lookup"><span data-stu-id="aa1e8-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2. <span data-ttu-id="aa1e8-125">新增 <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> 事件的事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="aa1e8-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="aa1e8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa1e8-126">See also</span></span>

- <xref:System.Windows.Forms.MaskedTextBox>
- [<span data-ttu-id="aa1e8-127">MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="aa1e8-127">MaskedTextBox Control</span></span>](maskedtextbox-control-windows-forms.md)
