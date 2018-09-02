---
title: 如何：將控制項加入至 Windows Form
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 1b803a93f865eaa4db6751187213c4bb01d2a5ee
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422545"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="df4c5-102">如何：將控制項加入至 Windows Form</span><span class="sxs-lookup"><span data-stu-id="df4c5-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="df4c5-103">大部分的表單都設計成將控制項加入表單的介面，來定義使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="df4c5-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="df4c5-104">A*控制*是用來顯示資訊，或接受使用者輸入表單上的元件。</span><span class="sxs-lookup"><span data-stu-id="df4c5-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="df4c5-105">如需控制項的詳細資訊，請參閱[Windows Forms 控制項](../../../../docs/framework/winforms/controls/index.md)。</span><span class="sxs-lookup"><span data-stu-id="df4c5-105">For more information about controls, see [Windows Forms Controls](../../../../docs/framework/winforms/controls/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df4c5-106">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="df4c5-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="df4c5-107">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="df4c5-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="df4c5-108">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="df4c5-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="df4c5-109">若要繪製在表單上控制項</span><span class="sxs-lookup"><span data-stu-id="df4c5-109">To draw a control on a form</span></span>  
  
1.  <span data-ttu-id="df4c5-110">開啟表單。</span><span class="sxs-lookup"><span data-stu-id="df4c5-110">Open the form.</span></span> <span data-ttu-id="df4c5-111">如需詳細資訊，請參閱 <<c0> [ 如何： 顯示 Windows Form 設計工具中](https://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。</span><span class="sxs-lookup"><span data-stu-id="df4c5-111">For more information, see [How to: Display Windows Forms in the Designer](https://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="df4c5-112">在 **工具箱**，按一下您想要新增至表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="df4c5-112">In the **Toolbox**, click the control you want to add to your form.</span></span>  
  
3.  <span data-ttu-id="df4c5-113">在表單中，按一下您想要找出，控制項的左上角並拖曳至要放置控制項的右下角的位置。</span><span class="sxs-lookup"><span data-stu-id="df4c5-113">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>  
  
     <span data-ttu-id="df4c5-114">控制項會加入至表單的指定的位置和大小。</span><span class="sxs-lookup"><span data-stu-id="df4c5-114">The control is added to the form with the specified location and size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df4c5-115">每個控制項已定義的預設大小。</span><span class="sxs-lookup"><span data-stu-id="df4c5-115">Each control has a default size defined.</span></span> <span data-ttu-id="df4c5-116">您可以將控制項加入您的表單控制項的預設大小從拖曳**工具箱**至表單。</span><span class="sxs-lookup"><span data-stu-id="df4c5-116">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>  
  
### <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="df4c5-117">若要將控制項拖曳至表單</span><span class="sxs-lookup"><span data-stu-id="df4c5-117">To drag a control to a form</span></span>  
  
1.  <span data-ttu-id="df4c5-118">開啟表單。</span><span class="sxs-lookup"><span data-stu-id="df4c5-118">Open the form.</span></span> <span data-ttu-id="df4c5-119">如需詳細資訊，請參閱 <<c0> [ 如何： 顯示 Windows Form 設計工具中](https://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。</span><span class="sxs-lookup"><span data-stu-id="df4c5-119">For more information, see [How to: Display Windows Forms in the Designer](https://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).</span></span>  
  
2.  <span data-ttu-id="df4c5-120">在 **工具箱**，按一下您想要並將它拖曳至表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="df4c5-120">In the **Toolbox**, click the control you want and drag it to your form.</span></span>  
  
     <span data-ttu-id="df4c5-121">控制項會加入至指定的位置，以預設大小的表單。</span><span class="sxs-lookup"><span data-stu-id="df4c5-121">The control is added to the form at the specified location in its default size.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df4c5-122">您可以按兩下中的控制項**工具箱**將它新增至其預設大小 中表單的左上角。</span><span class="sxs-lookup"><span data-stu-id="df4c5-122">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>  
  
     <span data-ttu-id="df4c5-123">您可以也將控制項以動態方式加入表單在執行階段。</span><span class="sxs-lookup"><span data-stu-id="df4c5-123">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="df4c5-124">在下列程式碼範例中，<xref:System.Windows.Forms.TextBox>控制項將會加入至表單時<xref:System.Windows.Forms.Button>按一下控制項時。</span><span class="sxs-lookup"><span data-stu-id="df4c5-124">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df4c5-125">下列程序需要有的表單** 按鈕**控制項， `Button1`、 已放在其上。</span><span class="sxs-lookup"><span data-stu-id="df4c5-125">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="df4c5-126">若要以程式設計方式將控制項加入表單</span><span class="sxs-lookup"><span data-stu-id="df4c5-126">To add a control to a form programmatically</span></span>  
  
1.  <span data-ttu-id="df4c5-127">在方法中處理按鈕的`Click`事件，在您的表單類別中，插入程式碼如下所示將參考加入至您的控制項變數，將控制項的`Location`，並加入控制項。</span><span class="sxs-lookup"><span data-stu-id="df4c5-127">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>  
  
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
    >  <span data-ttu-id="df4c5-128">您也可以加入程式碼以初始化控制項的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="df4c5-128">You can also add code to initialize other properties of the control.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="df4c5-129">您可能會公開本機電腦透過網路的安全性風險，藉由參考惡意`UserControl`。</span><span class="sxs-lookup"><span data-stu-id="df4c5-129">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="df4c5-130">這只會在惡意人士建立破壞性的自訂控制項，且您不小心將它新增至您的專案的情況下需要考量。</span><span class="sxs-lookup"><span data-stu-id="df4c5-130">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df4c5-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df4c5-131">See Also</span></span>  
 [<span data-ttu-id="df4c5-132">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="df4c5-132">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="df4c5-133">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="df4c5-133">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="df4c5-134">操作說明：重新調整 Windows Forms 上控制項的大小</span><span class="sxs-lookup"><span data-stu-id="df4c5-134">How to: Resize Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [<span data-ttu-id="df4c5-135">操作說明：設定由 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="df4c5-135">How to: Set the Text Displayed by a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [<span data-ttu-id="df4c5-136">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="df4c5-136">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
