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
ms.openlocfilehash: bcca6c5f5481d351a39a4e71532cc0f006075128
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538437"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a><span data-ttu-id="50a02-102">逐步解說：使用 MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="50a02-102">Walkthrough: Working with the MaskedTextBox Control</span></span>
<span data-ttu-id="50a02-103">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="50a02-103">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="50a02-104">初始化<xref:System.Windows.Forms.MaskedTextBox>控制項</span><span class="sxs-lookup"><span data-stu-id="50a02-104">Initializing the <xref:System.Windows.Forms.MaskedTextBox> control</span></span>  
  
-   <span data-ttu-id="50a02-105">使用<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>遮罩不符合一個字元時，通知使用者的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="50a02-105">Using the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event handler to alert the user when a character does not conform to the mask</span></span>  
  
-   <span data-ttu-id="50a02-106">指派的型別<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>屬性，並使用<xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>來提醒使用者當他們嘗試認可的值不是有效類型的事件處理常式</span><span class="sxs-lookup"><span data-stu-id="50a02-106">Assigning a type to the <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property and using the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event handler to alert the user when the value they're attempting to commit is not valid for the type</span></span>  
  
## <a name="creating-the-project-and-adding-a-control"></a><span data-ttu-id="50a02-107">建立專案並加入控制項</span><span class="sxs-lookup"><span data-stu-id="50a02-107">Creating the Project and Adding a Control</span></span>  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a><span data-ttu-id="50a02-108">若要將 MaskedTextBox 控制項加入至表單</span><span class="sxs-lookup"><span data-stu-id="50a02-108">To add a MaskedTextBox control to your form</span></span>  
  
1.  <span data-ttu-id="50a02-109">開啟您想要放置的表單<xref:System.Windows.Forms.MaskedTextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="50a02-109">Open the form on which you want to place the <xref:System.Windows.Forms.MaskedTextBox> control.</span></span>  
  
2.  <span data-ttu-id="50a02-110">拖曳<xref:System.Windows.Forms.MaskedTextBox>控制項從**工具箱**加入至表單。</span><span class="sxs-lookup"><span data-stu-id="50a02-110">Drag a <xref:System.Windows.Forms.MaskedTextBox> control from the **Toolbox** to your form.</span></span>  
  
3.  <span data-ttu-id="50a02-111">以滑鼠右鍵按一下控制項，然後選擇 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="50a02-111">Right-click the control and choose **Properties**.</span></span> <span data-ttu-id="50a02-112">在**屬性**視窗中，選取**遮罩**屬性，然後按一下 **...** （省略符號） 按鈕旁的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="50a02-112">In the **Properties** window, select the **Mask** property and click the **...** (ellipsis) button next to the property name.</span></span>  
  
4.  <span data-ttu-id="50a02-113">在**輸入遮罩**對話方塊中，選取**簡短日期**遮罩，並按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="50a02-113">In the **Input Mask** dialog box, select the **Short Date** mask and click **OK**.</span></span>  
  
5.  <span data-ttu-id="50a02-114">在**屬性**視窗中，將<xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="50a02-114">In the **Properties** window set the <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> property to `true`.</span></span> <span data-ttu-id="50a02-115">這個屬性會導致發出短的嗶聲音每次使用者嘗試輸入違反遮罩定義的字元。</span><span class="sxs-lookup"><span data-stu-id="50a02-115">This property causes a short beep to sound every time the user attempts to input a character that violates the mask definition.</span></span>  
  
 <span data-ttu-id="50a02-116">如需摘要的遮罩屬性支援的字元，請參閱的 < 備註 > 一節<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="50a02-116">For a summary of the characters that the Mask property supports, see the Remarks section of the <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property.</span></span>  
  
## <a name="alert-the-user-to-input-errors"></a><span data-ttu-id="50a02-117">警示使用者輸入錯誤</span><span class="sxs-lookup"><span data-stu-id="50a02-117">Alert the User to Input Errors</span></span>  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a><span data-ttu-id="50a02-118">新增拒絕的遮罩輸入氣球提示</span><span class="sxs-lookup"><span data-stu-id="50a02-118">Add a balloon tip for rejected mask input</span></span>  
  
1.  <span data-ttu-id="50a02-119">返回**工具箱**並加入<xref:System.Windows.Forms.ToolTip>加入至表單。</span><span class="sxs-lookup"><span data-stu-id="50a02-119">Return to the **Toolbox** and add a <xref:System.Windows.Forms.ToolTip> to your form.</span></span>  
  
2.  <span data-ttu-id="50a02-120">建立事件處理常式<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>所引發的事件<xref:System.Windows.Forms.ToolTip>發生輸入的錯誤。</span><span class="sxs-lookup"><span data-stu-id="50a02-120">Create an event handler for the <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> event that raises the <xref:System.Windows.Forms.ToolTip> when an input error occurs.</span></span> <span data-ttu-id="50a02-121">五秒，或直到使用者按一下它，仍會顯示汽球提示。</span><span class="sxs-lookup"><span data-stu-id="50a02-121">The balloon tip remains visible for five seconds, or until the user clicks it.</span></span>  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a><span data-ttu-id="50a02-122">警示使用者不是有效的類型</span><span class="sxs-lookup"><span data-stu-id="50a02-122">Alert the User to a Type that Is Not Valid</span></span>  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a><span data-ttu-id="50a02-123">無效的資料類型建立汽球提示</span><span class="sxs-lookup"><span data-stu-id="50a02-123">Add a balloon tip for invalid data types</span></span>  
  
1.  <span data-ttu-id="50a02-124">在您的表單<xref:System.Windows.Forms.Form.Load>事件處理常式，指派<xref:System.Type>物件，代表<xref:System.DateTime>類型<xref:System.Windows.Forms.MaskedTextBox>控制項的<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>屬性：</span><span class="sxs-lookup"><span data-stu-id="50a02-124">In your form's <xref:System.Windows.Forms.Form.Load> event handler, assign a <xref:System.Type> object representing the <xref:System.DateTime> type to the <xref:System.Windows.Forms.MaskedTextBox> control's <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> property:</span></span>  
  
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
  
2.  <span data-ttu-id="50a02-125">新增 <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> 事件的事件處理常式：</span><span class="sxs-lookup"><span data-stu-id="50a02-125">Add an event handler for the <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> event:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="50a02-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50a02-126">See Also</span></span>  
 <xref:System.Windows.Forms.MaskedTextBox>  
 [<span data-ttu-id="50a02-127">MaskedTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="50a02-127">MaskedTextBox Control</span></span>](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)
