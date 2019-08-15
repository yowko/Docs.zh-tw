---
title: HOW TO：將控制項新增至 Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 5c57d86b2f08733dc4a729bf6091eab23c6035f2
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039715"
---
# <a name="how-to-add-controls-to-windows-forms"></a><span data-ttu-id="a8ff3-102">作法：將控制項新增至 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a8ff3-102">How to: Add Controls to Windows Forms</span></span>
<span data-ttu-id="a8ff3-103">大部分的表單都是藉由將控制項新增至表單介面來定義使用者介面 (UI) 而設計。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-103">Most forms are designed by adding controls to the surface of the form to define a user interface (UI).</span></span> <span data-ttu-id="a8ff3-104">*控制項*是表單上用來顯示資訊或接受使用者輸入的元件。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-104">A *control* is a component on a form used to display information or accept user input.</span></span> <span data-ttu-id="a8ff3-105">如需控制項的詳細資訊, 請參閱[Windows Forms 控制項](index.md)。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-105">For more information about controls, see [Windows Forms Controls](index.md).</span></span>

## <a name="to-draw-a-control-on-a-form"></a><span data-ttu-id="a8ff3-106">若要在表單上繪製控制項</span><span class="sxs-lookup"><span data-stu-id="a8ff3-106">To draw a control on a form</span></span>

1. <span data-ttu-id="a8ff3-107">開啟表單。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-107">Open the form.</span></span> <span data-ttu-id="a8ff3-108">如需詳細資訊，請參閱[如何：在設計](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))工具中顯示 Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-108">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="a8ff3-109">在 [**工具箱**] 中, 按一下您想要新增至表單的控制項。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-109">In the **Toolbox**, click the control you want to add to your form.</span></span>

3. <span data-ttu-id="a8ff3-110">在表單上, 按一下您想要找出控制項左上角的位置, 並將其拖曳至您想要放置控制項右下角的位置。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-110">On the form, click where you want the upper-left corner of the control to be located, and drag to where you want the lower-right corner of the control to be located.</span></span>

     <span data-ttu-id="a8ff3-111">控制項會以指定的位置和大小加入表單中。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-111">The control is added to the form with the specified location and size.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="a8ff3-112">每個控制項都有定義的預設大小。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-112">Each control has a default size defined.</span></span> <span data-ttu-id="a8ff3-113">您可以將控制項從 [**工具箱**] 拖曳至表單, 以將控制項的預設大小加入表單中。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-113">You can add a control to your form in the control's default size by dragging it from the **Toolbox** to the form.</span></span>

## <a name="to-drag-a-control-to-a-form"></a><span data-ttu-id="a8ff3-114">將控制項拖曳至表單</span><span class="sxs-lookup"><span data-stu-id="a8ff3-114">To drag a control to a form</span></span>

1. <span data-ttu-id="a8ff3-115">開啟表單。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-115">Open the form.</span></span> <span data-ttu-id="a8ff3-116">如需詳細資訊，請參閱[如何：在設計](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))工具中顯示 Windows Forms。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-116">For more information, see [How to: Display Windows Forms in the Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).</span></span>

2. <span data-ttu-id="a8ff3-117">在 [**工具箱**] 中, 按一下您想要的控制項, 並將它拖曳至您的表單。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-117">In the **Toolbox**, click the control you want and drag it to your form.</span></span>

     <span data-ttu-id="a8ff3-118">控制項會在其預設大小的指定位置加入表單中。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-118">The control is added to the form at the specified location in its default size.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="a8ff3-119">您可以在 [**工具箱**] 中按兩下控制項, 將它新增至表單的左上角 (其預設大小)。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-119">You can double-click a control in the **Toolbox** to add it to the upper-left corner of the form in its default size.</span></span>

     <span data-ttu-id="a8ff3-120">您也可以在執行時間以動態方式將控制項新增至表單。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-120">You can also add controls dynamically to a form at run time.</span></span> <span data-ttu-id="a8ff3-121">在下列程式碼範例中, <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Button>當您按一下控制項時, 控制項就會加入表單中。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-121">In the following code example, a <xref:System.Windows.Forms.TextBox> control will be added to the form when a <xref:System.Windows.Forms.Button> control is clicked.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="a8ff3-122">下列程序需要有的表單 **按鈕** 控制項， `Button1` 、 已放在其上。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-122">The following procedure requires the existence of a form with a **Button** control, `Button1`, already placed on it.</span></span>

## <a name="to-add-a-control-to-a-form-programmatically"></a><span data-ttu-id="a8ff3-123">以程式設計方式將控制項新增至表單</span><span class="sxs-lookup"><span data-stu-id="a8ff3-123">To add a control to a form programmatically</span></span>

1. <span data-ttu-id="a8ff3-124">在處理表單類別內按鈕`Click`之事件的方法中, 插入與下列類似的程式碼, 以將參考加入控制項變數、設定控制項的`Location`, 以及加入控制項。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-124">In the method that handles the button's `Click` event within your form's class, insert code similar to the following to add a reference to your control variable, set the control's `Location`, and add the control.</span></span>

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
    >  <span data-ttu-id="a8ff3-125">您也可以加入程式碼來初始化控制項的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-125">You can also add code to initialize other properties of the control.</span></span>

    > [!IMPORTANT]
    >  <span data-ttu-id="a8ff3-126">藉由參考惡意`UserControl`, 您可能會透過網路將本機電腦暴露在安全性風險中。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-126">You might expose your local computer to a security risk through the network by referencing a malicious `UserControl`.</span></span> <span data-ttu-id="a8ff3-127">這只是在惡意人士建立損毀的自訂控制項, 然後誤將它新增至專案時的問題。</span><span class="sxs-lookup"><span data-stu-id="a8ff3-127">This would only be a concern in the case of a malicious person creating a damaging custom control, followed by you mistakenly adding it to your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="a8ff3-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8ff3-128">See also</span></span>

- [<span data-ttu-id="a8ff3-129">Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="a8ff3-129">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="a8ff3-130">排列 Windows Forms 上的控制項</span><span class="sxs-lookup"><span data-stu-id="a8ff3-130">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="a8ff3-131">如何：調整 Windows Forms 上控制項的大小</span><span class="sxs-lookup"><span data-stu-id="a8ff3-131">How to: Resize Controls on Windows Forms</span></span>](how-to-resize-controls-on-windows-forms.md)
- [<span data-ttu-id="a8ff3-132">如何：設定 Windows Forms 控制項所顯示的文字</span><span class="sxs-lookup"><span data-stu-id="a8ff3-132">How to: Set the Text Displayed by a Windows Forms Control</span></span>](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [<span data-ttu-id="a8ff3-133">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="a8ff3-133">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
