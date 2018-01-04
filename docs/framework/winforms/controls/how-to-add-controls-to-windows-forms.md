---
title: "如何：將控制項加入至 Windows Form"
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
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d9075c93181b68828a307924259a9170c046baa6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="832ed-102">如何：將控制項加入至 Windows Form</span><span class="sxs-lookup"><span data-stu-id="832ed-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="832ed-103">大部分表單都設計成將控制項加入至表單的表面，以定義使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="832ed-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="832ed-104">A*控制項*是用來顯示資訊或可接受使用者輸入表單上的元件。</span><span class="sxs-lookup"><span data-stu-id="832ed-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="832ed-105">如需將控制項的詳細資訊，請參閱[Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="832ed-105">For more information about controls, see [Windows Forms Controls](../../../../docs/framework/winforms/controls/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="832ed-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="832ed-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="832ed-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="832ed-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="832ed-108">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="832ed-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="832ed-109">若要繪製控制項在表單上</span><span class="sxs-lookup"><span data-stu-id="832ed-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="832ed-110">開啟表單。</span><span class="sxs-lookup"><span data-stu-id="832ed-110">Open the form.</span></span> <span data-ttu-id="832ed-111">如需詳細資訊，請參閱[如何： 顯示 Windows Form 設計工具中](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。</span><span class="sxs-lookup"><span data-stu-id="832ed-111">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="832ed-112">在**工具箱**，按一下您想要新增至表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="832ed-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="832ed-113">在表單中，按一下想要找出，控制項的左上角的位置並拖曳至想要找出控制項的右下角。</span><span class="sxs-lookup"><span data-stu-id="832ed-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="832ed-114">控制項會加入至表單，以指定的位置和大小。</span><span class="sxs-lookup"><span data-stu-id="832ed-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="832ed-115">每個控制項具有定義的預設大小。</span><span class="sxs-lookup"><span data-stu-id="832ed-115">Each control has a default size defined.</span></span> <span data-ttu-id="832ed-116">您可以將控制項加入至您的表單控制項的預設大小中將它從**工具箱**至表單。</span><span class="sxs-lookup"><span data-stu-id="832ed-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="832ed-117">若要將控制項拖曳至表單</span><span class="sxs-lookup"><span data-stu-id="832ed-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="832ed-118">開啟表單。</span><span class="sxs-lookup"><span data-stu-id="832ed-118">Open the form.</span></span> <span data-ttu-id="832ed-119">如需詳細資訊，請參閱[如何： 顯示 Windows Form 設計工具中](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。</span><span class="sxs-lookup"><span data-stu-id="832ed-119">For more information, see [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/en-us/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="832ed-120">在**工具箱**，按一下您想要並將它拖曳至表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="832ed-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="832ed-121">控制項會加入至表單，以預設大小的指定位置。</span><span class="sxs-lookup"><span data-stu-id="832ed-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="832ed-122">您可以按兩下中的控制項**工具箱**將它加入至表單的預設大小的左上角。</span><span class="sxs-lookup"><span data-stu-id="832ed-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="832ed-123">您也可以加入控制項動態表單在執行階段。</span><span class="sxs-lookup"><span data-stu-id="832ed-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="832ed-124">在下列程式碼範例中，<xref:System.Windows.Forms.TextBox>將控制項加入表單時<xref:System.Windows.Forms.Button>按一下控制項時。</span><span class="sxs-lookup"><span data-stu-id="832ed-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="832ed-125">下列程序需要具有的表單有**按鈕**控制項， `Button1`、 已放置在其上。</span><span class="sxs-lookup"><span data-stu-id="832ed-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="832ed-126">若要以程式設計方式將控制項加入表單</span><span class="sxs-lookup"><span data-stu-id="832ed-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="832ed-127">在方法中處理按鈕的`Click`事件表單的類別，如下所示將參考加入至您的控制項變數的插入程式碼內設定控制項的`Location`，並加入控制項。</span><span class="sxs-lookup"><span data-stu-id="832ed-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="832ed-128">您也可以加入程式碼以初始化控制項的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="832ed-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="832ed-129">您可能會藉由參考惡意公開本機電腦透過網路的安全性風險`UserControl`。</span><span class="sxs-lookup"><span data-stu-id="832ed-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="832ed-130">這只會考量使用者惡意破壞性的自訂控制項，且您不小心將其加入您專案的建立。</span><span class="sxs-lookup"><span data-stu-id="832ed-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="832ed-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="832ed-131">See Also</span></span>  
 [<span data-ttu-id="832ed-132">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="832ed-132">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="832ed-133">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="832ed-133">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="832ed-134">操作說明：重新調整 Windows Forms 上控制項的大小</span><span class="sxs-lookup"><span data-stu-id="832ed-134">How to: Resize Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [<span data-ttu-id="832ed-135">操作說明：設定由 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="832ed-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="832ed-136">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="832ed-136">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
