---
title: 作法：繼承現有的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
ms.openlocfilehash: 9ac18fae126425126712dafeb80f05663dfc2ebc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966592"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="c3180-102">HOW TO：繼承現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="c3180-102">How to: Inherit from Existing Windows Forms Controls</span></span>
<span data-ttu-id="c3180-103">如果您想要擴充現有控制項的功能，您可以透過繼承來建立衍生自現有控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="c3180-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="c3180-104">繼承自現有的控制項時，您會繼承該控制項的所有功能和視覺屬性。</span><span class="sxs-lookup"><span data-stu-id="c3180-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="c3180-105">例如, 如果您要建立繼承自<xref:System.Windows.Forms.Button>的控制項, 新控制項的外觀和作用就和標準<xref:System.Windows.Forms.Button>控制項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="c3180-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="c3180-106">您就可以透過實作自訂方法和屬性，來擴充或修改新控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="c3180-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="c3180-107">在某些控制項中, 您也可以藉由覆寫其<xref:System.Windows.Forms.Control.OnPaint%2A>方法來變更繼承控制項的視覺外觀。</span><span class="sxs-lookup"><span data-stu-id="c3180-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="c3180-108">建立繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="c3180-108">To create an inherited control</span></span>

1. <span data-ttu-id="c3180-109">建立新的 [Windows Forms 應用程式] 專案。</span><span class="sxs-lookup"><span data-stu-id="c3180-109">Create a new **Windows Forms Application** project.</span></span>

2. <span data-ttu-id="c3180-110">從 [專案] 功能表選擇 [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="c3180-110">From the **Project** menu, choose **Add New Item**.</span></span>

     <span data-ttu-id="c3180-111">[新增項目] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c3180-111">The **Add New Item** dialog box appears.</span></span>

3. <span data-ttu-id="c3180-112">在 [新增項目] 對話方塊中，連按兩下 [自訂控制項]。</span><span class="sxs-lookup"><span data-stu-id="c3180-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

     <span data-ttu-id="c3180-113">新的自訂控制項會新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="c3180-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="c3180-114">如果您使用 Visual Basic，請在 [方案總管] 的頂端，按一下 [顯示所有檔案]。</span><span class="sxs-lookup"><span data-stu-id="c3180-114">If you using Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="c3180-115">展開 CustomControl1.vb，然後在程式碼編輯器中開啟 CustomControl1.Designer.vb。</span><span class="sxs-lookup"><span data-stu-id="c3180-115">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>

5. <span data-ttu-id="c3180-116">如果您使用 C#，請在程式碼編輯器中開啟 CustomControl1.cs。</span><span class="sxs-lookup"><span data-stu-id="c3180-116">If you are using C#, open CustomControl1.cs in the Code Editor.</span></span>

6. <span data-ttu-id="c3180-117">找出繼承自<xref:System.Windows.Forms.Control>的類別宣告。</span><span class="sxs-lookup"><span data-stu-id="c3180-117">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

7. <span data-ttu-id="c3180-118">將基底類別變更為您想要繼承的控制項。</span><span class="sxs-lookup"><span data-stu-id="c3180-118">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="c3180-119">例如, 如果您想要繼承自<xref:System.Windows.Forms.Button>, 請將類別宣告變更為下列內容:</span><span class="sxs-lookup"><span data-stu-id="c3180-119">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

8. <span data-ttu-id="c3180-120">如果您使用 Visual Basic，請儲存並關閉 CustomControl1.Designer.vb。</span><span class="sxs-lookup"><span data-stu-id="c3180-120">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="c3180-121">在程式碼編輯器中開啟 CustomControl1.vb。</span><span class="sxs-lookup"><span data-stu-id="c3180-121">Open CustomControl1.vb in the Code Editor.</span></span>

9. <span data-ttu-id="c3180-122">實作您的控制項將併入的任何自訂方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="c3180-122">Implement any custom methods or properties that your control will incorporate.</span></span>

10. <span data-ttu-id="c3180-123">如果您想要修改控制項的圖形外觀, 請覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c3180-123">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c3180-124">覆<xref:System.Windows.Forms.Control.OnPaint%2A>寫將不允許您修改所有控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="c3180-124">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="c3180-125">所有由 Windows 完成其繪製的控制項 (例如, <xref:System.Windows.Forms.TextBox>) 永遠不會呼叫其<xref:System.Windows.Forms.Control.OnPaint%2A>方法, 因此永遠不會使用自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="c3180-125">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="c3180-126">請參閱您想要修改之特定控制項的說明文件, 以查看該<xref:System.Windows.Forms.Control.OnPaint%2A>方法是否可用。</span><span class="sxs-lookup"><span data-stu-id="c3180-126">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="c3180-127">如需所有 Windows Forms 控制項的清單，請參閱[要在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="c3180-127">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="c3180-128">如果控制項未<xref:System.Windows.Forms.Control.OnPaint%2A>列為成員方法, 您就無法藉由覆寫這個方法來改變其外觀。</span><span class="sxs-lookup"><span data-stu-id="c3180-128">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="c3180-129">如需自訂繪製的詳細資訊，請參閱[自訂控制項繪製和轉譯](custom-control-painting-and-rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="c3180-129">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

    ```vb
    Protected Overrides Sub OnPaint(ByVal e As _
       System.Windows.Forms.PaintEventArgs)
       MyBase.OnPaint(e)
       ' Insert code to do custom painting.
       ' If you want to completely change the appearance of your control,
       ' do not call MyBase.OnPaint(e).
    End Sub
    ```

    ```csharp
    protected override void OnPaint(PaintEventArgs pe)
    {
       base.OnPaint(pe);
       // Insert code to do custom painting.
       // If you want to completely change the appearance of your control,
       // do not call base.OnPaint(pe).
    }
    ```

11. <span data-ttu-id="c3180-130">儲存並測試您的控制項。</span><span class="sxs-lookup"><span data-stu-id="c3180-130">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3180-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3180-131">See also</span></span>

- [<span data-ttu-id="c3180-132">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="c3180-132">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="c3180-133">如何：繼承自控制項類別</span><span class="sxs-lookup"><span data-stu-id="c3180-133">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="c3180-134">如何：繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="c3180-134">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="c3180-135">如何：Windows Forms 的作者控制項</span><span class="sxs-lookup"><span data-stu-id="c3180-135">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="c3180-136">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="c3180-136">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="c3180-137">逐步解說：從具有 Visual Basic 的 Windows Forms 控制項繼承</span><span class="sxs-lookup"><span data-stu-id="c3180-137">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="c3180-138">逐步解說：使用視覺效果從 Windows Forms 控制項繼承C#</span><span class="sxs-lookup"><span data-stu-id="c3180-138">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
