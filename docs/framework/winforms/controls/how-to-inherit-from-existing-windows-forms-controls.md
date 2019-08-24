---
title: HOW TO：繼承現有的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0571bd6b169b94b1626bffb0d0793bbb22a93ba0
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015880"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a><span data-ttu-id="c4c25-102">作法：繼承現有的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="c4c25-102">How to: Inherit from Existing Windows Forms Controls</span></span>

<span data-ttu-id="c4c25-103">如果您想要擴充現有控制項的功能，您可以透過繼承來建立衍生自現有控制項的控制項。</span><span class="sxs-lookup"><span data-stu-id="c4c25-103">If you want to extend the functionality of an existing control, you can create a control derived from an existing control through inheritance.</span></span> <span data-ttu-id="c4c25-104">繼承自現有的控制項時，您會繼承該控制項的所有功能和視覺屬性。</span><span class="sxs-lookup"><span data-stu-id="c4c25-104">When inheriting from an existing control, you inherit all of the functionality and visual properties of that control.</span></span> <span data-ttu-id="c4c25-105">例如, 如果您要建立繼承自<xref:System.Windows.Forms.Button>的控制項, 新控制項的外觀和作用就和標準<xref:System.Windows.Forms.Button>控制項完全一樣。</span><span class="sxs-lookup"><span data-stu-id="c4c25-105">For example, if you were creating a control that inherited from <xref:System.Windows.Forms.Button>, your new control would look and act exactly like a standard <xref:System.Windows.Forms.Button> control.</span></span> <span data-ttu-id="c4c25-106">您就可以透過實作自訂方法和屬性，來擴充或修改新控制項的功能。</span><span class="sxs-lookup"><span data-stu-id="c4c25-106">You could then extend or modify the functionality of your new control through the implementation of custom methods and properties.</span></span> <span data-ttu-id="c4c25-107">在某些控制項中, 您也可以藉由覆寫其<xref:System.Windows.Forms.Control.OnPaint%2A>方法來變更繼承控制項的視覺外觀。</span><span class="sxs-lookup"><span data-stu-id="c4c25-107">In some controls, you can also change the visual appearance of your inherited control by overriding its <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

## <a name="to-create-an-inherited-control"></a><span data-ttu-id="c4c25-108">建立繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="c4c25-108">To create an inherited control</span></span>

1. <span data-ttu-id="c4c25-109">在 Visual Studio 中, 建立新的**Windows Forms 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="c4c25-109">In Visual Studio, create a new **Windows Forms Application** project.</span></span>

2. <span data-ttu-id="c4c25-110">從 [專案] 功能表選擇 [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="c4c25-110">From the **Project** menu, choose **Add New Item**.</span></span>

     <span data-ttu-id="c4c25-111">[新增項目] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="c4c25-111">The **Add New Item** dialog box appears.</span></span>

3. <span data-ttu-id="c4c25-112">在 [新增項目] 對話方塊中，連按兩下 [自訂控制項]。</span><span class="sxs-lookup"><span data-stu-id="c4c25-112">In the **Add New Item** dialog box, double-click **Custom Control**.</span></span>

     <span data-ttu-id="c4c25-113">新的自訂控制項會新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="c4c25-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="c4c25-114">如果您使用:</span><span class="sxs-lookup"><span data-stu-id="c4c25-114">If you using:</span></span>

   - <span data-ttu-id="c4c25-115">Visual Basic 中, 按一下**方案總管**頂端的 [**顯示所有**檔案]。</span><span class="sxs-lookup"><span data-stu-id="c4c25-115">Visual Basic, at the top of **Solution Explorer**, click **Show All Files**.</span></span> <span data-ttu-id="c4c25-116">展開 CustomControl1.vb，然後在程式碼編輯器中開啟 CustomControl1.Designer.vb。</span><span class="sxs-lookup"><span data-stu-id="c4c25-116">Expand CustomControl1.vb and then open CustomControl1.Designer.vb in the Code Editor.</span></span>
   - <span data-ttu-id="c4c25-117">C#, 在程式碼編輯器中開啟 CustomControl1.cs。</span><span class="sxs-lookup"><span data-stu-id="c4c25-117">C#, open CustomControl1.cs in the Code Editor.</span></span>

6. <span data-ttu-id="c4c25-118">找出繼承自<xref:System.Windows.Forms.Control>的類別宣告。</span><span class="sxs-lookup"><span data-stu-id="c4c25-118">Locate the class declaration, which inherits from <xref:System.Windows.Forms.Control>.</span></span>

7. <span data-ttu-id="c4c25-119">將基底類別變更為您想要繼承的控制項。</span><span class="sxs-lookup"><span data-stu-id="c4c25-119">Change the base class to the control that you want to inherit from.</span></span>

     <span data-ttu-id="c4c25-120">例如, 如果您想要繼承自<xref:System.Windows.Forms.Button>, 請將類別宣告變更為下列內容:</span><span class="sxs-lookup"><span data-stu-id="c4c25-120">For example, if you want to inherit from <xref:System.Windows.Forms.Button>, change the class declaration to the following:</span></span>

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

8. <span data-ttu-id="c4c25-121">如果您使用 Visual Basic，請儲存並關閉 CustomControl1.Designer.vb。</span><span class="sxs-lookup"><span data-stu-id="c4c25-121">If you are using Visual Basic, save and close CustomControl1.Designer.vb.</span></span> <span data-ttu-id="c4c25-122">在程式碼編輯器中開啟 CustomControl1.vb。</span><span class="sxs-lookup"><span data-stu-id="c4c25-122">Open CustomControl1.vb in the Code Editor.</span></span>

9. <span data-ttu-id="c4c25-123">實作您的控制項將併入的任何自訂方法或屬性。</span><span class="sxs-lookup"><span data-stu-id="c4c25-123">Implement any custom methods or properties that your control will incorporate.</span></span>

10. <span data-ttu-id="c4c25-124">如果您想要修改控制項的圖形外觀, 請覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c4c25-124">If you want to modify the graphical appearance of your control, override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c4c25-125">覆<xref:System.Windows.Forms.Control.OnPaint%2A>寫將不允許您修改所有控制項的外觀。</span><span class="sxs-lookup"><span data-stu-id="c4c25-125">Overriding <xref:System.Windows.Forms.Control.OnPaint%2A> will not allow you to modify the appearance of all controls.</span></span> <span data-ttu-id="c4c25-126">所有由 Windows 完成其繪製的控制項 (例如, <xref:System.Windows.Forms.TextBox>) 永遠不會呼叫其<xref:System.Windows.Forms.Control.OnPaint%2A>方法, 因此永遠不會使用自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="c4c25-126">Those controls that have all of their painting done by Windows (for example, <xref:System.Windows.Forms.TextBox>) never call their <xref:System.Windows.Forms.Control.OnPaint%2A> method, and thus will never use the custom code.</span></span> <span data-ttu-id="c4c25-127">請參閱您想要修改之特定控制項的說明文件, 以查看該<xref:System.Windows.Forms.Control.OnPaint%2A>方法是否可用。</span><span class="sxs-lookup"><span data-stu-id="c4c25-127">Refer to the Help documentation for the particular control you want to modify to see if the <xref:System.Windows.Forms.Control.OnPaint%2A> method is available.</span></span> <span data-ttu-id="c4c25-128">如需所有 Windows Forms 控制項的清單，請參閱[要在 Windows Forms 上使用的控制項](controls-to-use-on-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c25-128">For a list of all the Windows Form Controls, see [Controls to Use on Windows Forms](controls-to-use-on-windows-forms.md).</span></span> <span data-ttu-id="c4c25-129">如果控制項未<xref:System.Windows.Forms.Control.OnPaint%2A>列為成員方法, 您就無法藉由覆寫這個方法來改變其外觀。</span><span class="sxs-lookup"><span data-stu-id="c4c25-129">If a control does not have <xref:System.Windows.Forms.Control.OnPaint%2A> listed as a member method, you cannot alter its appearance by overriding this method.</span></span> <span data-ttu-id="c4c25-130">如需自訂繪製的詳細資訊，請參閱[自訂控制項繪製和轉譯](custom-control-painting-and-rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c25-130">For more information about custom painting, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

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

11. <span data-ttu-id="c4c25-131">儲存並測試您的控制項。</span><span class="sxs-lookup"><span data-stu-id="c4c25-131">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4c25-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4c25-132">See also</span></span>

- [<span data-ttu-id="c4c25-133">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="c4c25-133">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="c4c25-134">如何：繼承自控制項類別</span><span class="sxs-lookup"><span data-stu-id="c4c25-134">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="c4c25-135">如何：繼承自 UserControl 類別</span><span class="sxs-lookup"><span data-stu-id="c4c25-135">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="c4c25-136">如何：Windows Forms 的作者控制項</span><span class="sxs-lookup"><span data-stu-id="c4c25-136">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="c4c25-137">Visual Basic 中的繼承事件處理常式疑難排解</span><span class="sxs-lookup"><span data-stu-id="c4c25-137">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="c4c25-138">逐步解說：繼承自 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="c4c25-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
