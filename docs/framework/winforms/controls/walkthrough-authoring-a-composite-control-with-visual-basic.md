---
title: 逐步解說：使用 Visual Basic 撰寫複合控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Visual Basic]
- user controls [Visual Basic]
- UserControl class [Windows Forms], walkthroughs
- user controls [Windows Forms], creating with Visual Basic
- controls [Windows Forms], composite controls
- composite controls [Windows Forms], creating
- custom controls [Windows Forms], creating
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
ms.openlocfilehash: abfb91c61ef72bfc1626b4cc4dcea42b75e2ab35
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040247"
---
# <a name="walkthrough-authoring-a-composite-control-with-visual-basic"></a><span data-ttu-id="23626-102">逐步解說：使用 Visual Basic 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="23626-102">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>
<span data-ttu-id="23626-103">複合控制項提供可以建立及重複使用自訂圖形介面的方法。</span><span class="sxs-lookup"><span data-stu-id="23626-103">Composite controls provide a means by which custom graphical interfaces can be created and reused.</span></span> <span data-ttu-id="23626-104">複合控制項基本上是具有視覺表示的元件。</span><span class="sxs-lookup"><span data-stu-id="23626-104">A composite control is essentially a component with a visual representation.</span></span> <span data-ttu-id="23626-105">因此，它可能包含一或多個 Windows Forms 控制項、元件或程式碼區塊，可以藉由驗證使用者輸入、修改顯示屬性，或執行作者需要的其他工作來擴充功能。</span><span class="sxs-lookup"><span data-stu-id="23626-105">As such, it might consist of one or more Windows Forms controls, components, or blocks of code that can extend functionality by validating user input, modifying display properties, or performing other tasks required by the author.</span></span> <span data-ttu-id="23626-106">複合控制項可以放在 Windows Forms 上，與其他控制項的方式相同。</span><span class="sxs-lookup"><span data-stu-id="23626-106">Composite controls can be placed on Windows Forms in the same manner as other controls.</span></span> <span data-ttu-id="23626-107">在本逐步解說的第一個部分中，您可以建立簡單的複合控制項，稱為 `ctlClock`。</span><span class="sxs-lookup"><span data-stu-id="23626-107">In the first part of this walkthrough, you create a simple composite control called `ctlClock`.</span></span> <span data-ttu-id="23626-108">在逐步解說的第二個部分中，您透過繼承擴充 `ctlClock` 的功能。</span><span class="sxs-lookup"><span data-stu-id="23626-108">In the second part of the walkthrough, you extend the functionality of `ctlClock` through inheritance.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="23626-109">建立專案</span><span class="sxs-lookup"><span data-stu-id="23626-109">Creating the Project</span></span>
 <span data-ttu-id="23626-110">當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="23626-110">When you create a new project, you specify its name to set the root namespace, assembly name, and project name, and ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-ctlclocklib-control-library-and-the-ctlclock-control"></a><span data-ttu-id="23626-111">建立 ctlClockLib 控制項程式庫和 ctlClock 控制項</span><span class="sxs-lookup"><span data-stu-id="23626-111">To create the ctlClockLib control library and the ctlClock control</span></span>

1. <span data-ttu-id="23626-112">在 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]，開啟 [新增專案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="23626-112">On the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="23626-113">從 Visual Basic 專案清單中, 選取 [ **Windows 控制項程式庫**] 專案範本, `ctlClockLib`在 [**名稱**] 方塊中輸入, 然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="23626-113">From the list of Visual Basic projects, select the **Windows Control Library** project template, type `ctlClockLib` in the **Name** box, and then click **OK**.</span></span>

     <span data-ttu-id="23626-114">專案名稱，`ctlClockLib`，預設也會指派給根命名空間。</span><span class="sxs-lookup"><span data-stu-id="23626-114">The project name, `ctlClockLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="23626-115">根命名空間是用來限定組件中的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="23626-115">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="23626-116">例如，如果兩個組件提供元件，名為 `ctlClock`，您可以使用 `ctlClockLib.ctlClock.` 指定您的 `ctlClock` 元件</span><span class="sxs-lookup"><span data-stu-id="23626-116">For example, if two assemblies provide components named `ctlClock`, you can specify your `ctlClock` component using `ctlClockLib.ctlClock.`</span></span>

3. <span data-ttu-id="23626-117">以滑鼠右鍵按一下 [方案總管] 中的 [UserControl1.vb]，然後按一下 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="23626-117">In Solution Explorer, right-click **UserControl1.vb**, and then click **Rename**.</span></span> <span data-ttu-id="23626-118">將檔案名稱變更為 `ctlClock.vb`。</span><span class="sxs-lookup"><span data-stu-id="23626-118">Change the file name to `ctlClock.vb`.</span></span> <span data-ttu-id="23626-119">當系統詢問您是否要重新命名程式碼元素 "UserControl1" 的所有參考時，按一下 [是]按鈕。</span><span class="sxs-lookup"><span data-stu-id="23626-119">Click the **Yes** button when you are asked if you want to rename all references to the code element "UserControl1".</span></span>

    > [!NOTE]
    >  <span data-ttu-id="23626-120">根據預設, 複合控制項會繼承系統所提供<xref:System.Windows.Forms.UserControl>的類別。</span><span class="sxs-lookup"><span data-stu-id="23626-120">By default, a composite control inherits from the <xref:System.Windows.Forms.UserControl> class provided by the system.</span></span> <span data-ttu-id="23626-121">類別<xref:System.Windows.Forms.UserControl>提供所有複合控制項所需的功能, 並實作為標準方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="23626-121">The <xref:System.Windows.Forms.UserControl> class provides functionality required by all composite controls, and implements standard methods and properties.</span></span>

4. <span data-ttu-id="23626-122">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="23626-122">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-windows-controls-and-components-to-the-composite-control"></a><span data-ttu-id="23626-123">將 Windows 控制項和元件新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="23626-123">Adding Windows Controls and Components to the Composite Control</span></span>
 <span data-ttu-id="23626-124">視覺化介面是複合控制項不可或缺的一部分。</span><span class="sxs-lookup"><span data-stu-id="23626-124">A visual interface is an essential part of your composite control.</span></span> <span data-ttu-id="23626-125">這個視覺化介面是藉由將一或多個 Windows 控制項新增至設計工具介面來實作。</span><span class="sxs-lookup"><span data-stu-id="23626-125">This visual interface is implemented by the addition of one or more Windows controls to the designer surface.</span></span> <span data-ttu-id="23626-126">在下列示範中，您將 Windows 控制項合併到您的複合控制項，並且撰寫程式碼來實作功能。</span><span class="sxs-lookup"><span data-stu-id="23626-126">In the following demonstration, you will incorporate Windows controls into your composite control and write code to implement functionality.</span></span>

### <a name="to-add-a-label-and-a-timer-to-your-composite-control"></a><span data-ttu-id="23626-127">將標籤和計時器新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="23626-127">To add a Label and a Timer to your composite control</span></span>

1. <span data-ttu-id="23626-128">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClock.vb]，然後按一下 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="23626-128">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="23626-129">在 [工具箱] 中展開 [通用控制項] 節點，然後再按兩下 [標籤]。</span><span class="sxs-lookup"><span data-stu-id="23626-129">In the Toolbox, expand the **Common Controls** node, and then double-click **Label**.</span></span>

     <span data-ttu-id="23626-130"><xref:System.Windows.Forms.Label> 名`Label1`為的控制項會加入至設計工具介面上的控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-130">A <xref:System.Windows.Forms.Label> control named `Label1` is added to your control on the designer surface.</span></span>

3. <span data-ttu-id="23626-131">在設計工具中，按一下 [Label1]。</span><span class="sxs-lookup"><span data-stu-id="23626-131">In the designer, click **Label1**.</span></span> <span data-ttu-id="23626-132">在 [屬性] 視窗中設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="23626-132">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="23626-133">屬性</span><span class="sxs-lookup"><span data-stu-id="23626-133">Property</span></span>|<span data-ttu-id="23626-134">變更為</span><span class="sxs-lookup"><span data-stu-id="23626-134">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="23626-135">**名稱**</span><span class="sxs-lookup"><span data-stu-id="23626-135">**Name**</span></span>|`lblDisplay`|
    |<span data-ttu-id="23626-136">**Text**</span><span class="sxs-lookup"><span data-stu-id="23626-136">**Text**</span></span>|`(blank space)`|
    |<span data-ttu-id="23626-137">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="23626-137">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="23626-138">**Font.Size**</span><span class="sxs-lookup"><span data-stu-id="23626-138">**Font.Size**</span></span>|`14`|

4. <span data-ttu-id="23626-139">在 [工具箱] 中展開 [元件] 節點，然後再按兩下 [計時器]。</span><span class="sxs-lookup"><span data-stu-id="23626-139">In the **Toolbox**, expand the **Components** node, and then double-click **Timer**.</span></span>

     <span data-ttu-id="23626-140"><xref:System.Windows.Forms.Timer>因為是元件, 所以在執行時間沒有視覺表示。</span><span class="sxs-lookup"><span data-stu-id="23626-140">Because a <xref:System.Windows.Forms.Timer> is a component, it has no visual representation at run time.</span></span> <span data-ttu-id="23626-141">因此，它不會與控制項一起出現在設計工具介面上，而是會出現在元件設計工具中 (位於設計工具介面底部的系統匣)。</span><span class="sxs-lookup"><span data-stu-id="23626-141">Therefore, it does not appear with the controls on the designer surface, but rather in the Component Designer (a tray at the bottom of the designer surface).</span></span>

5. <span data-ttu-id="23626-142">在元件設計工具中, 按一下 [ **Timer1**], 然後<xref:System.Windows.Forms.Timer.Interval%2A>將<xref:System.Windows.Forms.Timer.Enabled%2A>屬性`1000`設為, 並`True`將屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="23626-142">In the Component Designer, click **Timer1**, and then set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `1000` and the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `True`.</span></span>

     <span data-ttu-id="23626-143"><xref:System.Windows.Forms.Timer.Interval%2A>屬性會控制計時器元件刻度的頻率。</span><span class="sxs-lookup"><span data-stu-id="23626-143">The <xref:System.Windows.Forms.Timer.Interval%2A> property controls the frequency with which the timer component ticks.</span></span> <span data-ttu-id="23626-144">每次 `Timer1` 走動時，它會執行 `Timer1_Tick` 事件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="23626-144">Each time `Timer1` ticks, it runs the code in the `Timer1_Tick` event.</span></span> <span data-ttu-id="23626-145">間隔代表刻度之間的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="23626-145">The interval represents the number of milliseconds between ticks.</span></span>

6. <span data-ttu-id="23626-146">在元件設計工具中，按兩下 [Timer1] 以前往 `ctlClock` 的 `Timer1_Tick` 事件。</span><span class="sxs-lookup"><span data-stu-id="23626-146">In the Component Designer, double-click **Timer1** to go to the `Timer1_Tick` event for `ctlClock`.</span></span>

7. <span data-ttu-id="23626-147">修改程式碼，使它類似下列程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="23626-147">Modify the code so that it resembles the following code sample.</span></span> <span data-ttu-id="23626-148">請確定將存取修飾詞從 `Private` 變更為 `Protected`。</span><span class="sxs-lookup"><span data-stu-id="23626-148">Be sure to change the access modifier from `Private` to `Protected`.</span></span>

    ```vb
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles Timer1.Tick
        ' Causes the label to display the current time.
        lblDisplay.Text = Format(Now, "hh:mm:ss")
    End Sub
    ```

     <span data-ttu-id="23626-149">此程式碼會造成目前時間在 `lblDisplay` 中顯示。</span><span class="sxs-lookup"><span data-stu-id="23626-149">This code will cause the current time to be shown in `lblDisplay`.</span></span> <span data-ttu-id="23626-150">因為 `Timer1` 的間隔設為 `1000`，每一千毫秒便會發生此事件，因此每秒會更新目前時間。</span><span class="sxs-lookup"><span data-stu-id="23626-150">Because the interval of `Timer1` was set to `1000`, this event will occur every thousand milliseconds, thus updating the current time every second.</span></span>

8. <span data-ttu-id="23626-151">修改方法為可覆寫。</span><span class="sxs-lookup"><span data-stu-id="23626-151">Modify the method to be overridable.</span></span> <span data-ttu-id="23626-152">如需詳細資訊，請參閱以下的「從使用者控制項繼承」一節。</span><span class="sxs-lookup"><span data-stu-id="23626-152">For more information, see the "Inheriting from a User Control" section below.</span></span>

    ```vb
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _
        e As System.EventArgs) Handles Timer1.Tick
    ```

9. <span data-ttu-id="23626-153">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="23626-153">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="adding-properties-to-the-composite-control"></a><span data-ttu-id="23626-154">將屬性新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="23626-154">Adding Properties to the Composite Control</span></span>
 <span data-ttu-id="23626-155">您的時鐘控制項現在會<xref:System.Windows.Forms.Label>封裝控制項<xref:System.Windows.Forms.Timer>和元件, 每個都有自己的一組固有屬性。</span><span class="sxs-lookup"><span data-stu-id="23626-155">Your clock control now encapsulates a <xref:System.Windows.Forms.Label> control and a <xref:System.Windows.Forms.Timer> component, each with its own set of inherent properties.</span></span> <span data-ttu-id="23626-156">雖然這些控制項的個別屬性無法供控制項的後續使用者存取，但是您可以建立並公開自訂屬性，方法是撰寫適當的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="23626-156">While the individual properties of these controls will not be accessible to subsequent users of your control, you can create and expose custom properties by writing the appropriate blocks of code.</span></span> <span data-ttu-id="23626-157">在下列程序中，您會將屬性新增至控制項，讓使用者變更背景與文字的色彩。</span><span class="sxs-lookup"><span data-stu-id="23626-157">In the following procedure, you will add properties to your control that enable the user to change the color of the background and text.</span></span>

### <a name="to-add-a-property-to-your-composite-control"></a><span data-ttu-id="23626-158">若要將屬性新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="23626-158">To add a property to your composite control</span></span>

1. <span data-ttu-id="23626-159">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClock.vb]，然後按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="23626-159">In Solution Explorer, right-click **ctlClock.vb**, and then click **View Code**.</span></span>

     <span data-ttu-id="23626-160">控制項的程式碼編輯器隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="23626-160">The Code Editor for your control opens.</span></span>

2. <span data-ttu-id="23626-161">尋找 `Public Class ctlClock` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="23626-161">Locate the `Public Class ctlClock` statement.</span></span> <span data-ttu-id="23626-162">在其下輸入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="23626-162">Beneath it, type the following code.</span></span>

    ```vb
    Private colFColor as Color
    Private colBColor as Color
    ```

     <span data-ttu-id="23626-163">這些陳述式會建立私用變數，您將用來儲存您即將建立之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="23626-163">These statements create the private variables that you will use to store the values for the properties you are about to create.</span></span>

3. <span data-ttu-id="23626-164">在 步驟 2 的變數宣告底下插入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="23626-164">Insert the following code beneath the variable declarations from step 2.</span></span>

    ```vb
    ' Declares the name and type of the property.
    Property ClockBackColor() as Color
        ' Retrieves the value of the private variable colBColor.
        Get
            Return colBColor
        End Get
        ' Stores the selected value in the private variable colBColor, and
        ' updates the background color of the label control lblDisplay.
        Set(ByVal value as Color)
            colBColor = value
            lblDisplay.BackColor = colBColor
        End Set

    End Property
    ' Provides a similar set of instructions for the foreground color.
    Property ClockForeColor() as Color
        Get
            Return colFColor
        End Get
        Set(ByVal value as Color)
            colFColor = value
            lblDisplay.ForeColor = colFColor
        End Set
    End Property
    ```

     <span data-ttu-id="23626-165">上述程式碼會製作兩個自訂屬性，`ClockForeColor` 和 `ClockBackColor`，藉由叫用 `Property` 陳述式，以供此控制項的後續使用者使用。</span><span class="sxs-lookup"><span data-stu-id="23626-165">The preceding code makes two custom properties, `ClockForeColor` and `ClockBackColor`, available to subsequent users of this control by invoking the `Property` statement.</span></span> <span data-ttu-id="23626-166">          `Get` 和 `Set` 陳述式提供屬性值的儲存和擷取，以及用來實作適合該屬性之功能的程式碼。</span><span class="sxs-lookup"><span data-stu-id="23626-166">The `Get` and `Set` statements provide for storage and retrieval of the property value, as well as code to implement functionality appropriate to the property.</span></span>

4. <span data-ttu-id="23626-167">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="23626-167">On the **File** menu, click **Save All** to save the project.</span></span>

## <a name="testing-the-control"></a><span data-ttu-id="23626-168">測試控制項</span><span class="sxs-lookup"><span data-stu-id="23626-168">Testing the Control</span></span>
 <span data-ttu-id="23626-169">控制項不是獨立專案；它們必須裝載在容器中。</span><span class="sxs-lookup"><span data-stu-id="23626-169">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="23626-170">測試控制項的執行階段行為，並且使用 **UserControl 測試容器**執行其屬性。</span><span class="sxs-lookup"><span data-stu-id="23626-170">Test your control's run-time behavior and exercise its properties with the **UserControl Test Container**.</span></span> <span data-ttu-id="23626-171">如需詳細資訊，請參閱[如何：測試 UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="23626-171">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

### <a name="to-test-your-control"></a><span data-ttu-id="23626-172">若要測試控制項</span><span class="sxs-lookup"><span data-stu-id="23626-172">To test your control</span></span>

1. <span data-ttu-id="23626-173">按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-173">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>

2. <span data-ttu-id="23626-174">在測試容器的屬性方格中，選取 `ClockBackColor` 屬性，然後按一下下拉箭號以顯示色彩調色盤。</span><span class="sxs-lookup"><span data-stu-id="23626-174">In the test container's property grid, select the `ClockBackColor` property, and then click the drop-down arrow to display the color palette.</span></span>

3. <span data-ttu-id="23626-175">按一下它以選擇色彩。</span><span class="sxs-lookup"><span data-stu-id="23626-175">Choose a color by clicking it.</span></span>

     <span data-ttu-id="23626-176">控制項的背景色彩會變更為您所選取的色彩。</span><span class="sxs-lookup"><span data-stu-id="23626-176">The background color of your control changes to the color you selected.</span></span>

4. <span data-ttu-id="23626-177">使用類似的一連串事件，確認 `ClockForeColor` 屬性是否如預期運作。</span><span class="sxs-lookup"><span data-stu-id="23626-177">Use a similar sequence of events to verify that the `ClockForeColor` property is functioning as expected.</span></span>

5. <span data-ttu-id="23626-178">按一下 [關閉] 以關閉 **UserControl 測試容器**。</span><span class="sxs-lookup"><span data-stu-id="23626-178">Click **Close** to close the **UserControl Test Container**.</span></span>

     <span data-ttu-id="23626-179">在本節和先前的章節中，您已經知道元件和 Windows 控制項如何與程式碼合併並且封裝，以複合控制項的形式提供自訂功能。</span><span class="sxs-lookup"><span data-stu-id="23626-179">In this section and the preceding sections, you have seen how components and Windows controls can be combined with code and packaging to provide custom functionality in the form of a composite control.</span></span> <span data-ttu-id="23626-180">您已經了解如何在您的複合控制項中公開屬性，以及如何在完成之後測試您的控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-180">You have learned to expose properties in your composite control, and how to test your control after it is complete.</span></span> <span data-ttu-id="23626-181">在下一節中，您將學習如何使用 `ctlClock` 做為基底，建構繼承的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-181">In the next section you will learn how to construct an inherited composite control using `ctlClock` as a base.</span></span>

## <a name="inheriting-from-a-composite-control"></a><span data-ttu-id="23626-182">繼承自複合控制項</span><span class="sxs-lookup"><span data-stu-id="23626-182">Inheriting from a Composite Control</span></span>
 <span data-ttu-id="23626-183">在先前章節中，您了解如何將 Windows 控制項、元件和程式碼合併成可重複使用的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-183">In the previous sections, you learned how to combine Windows controls, components, and code into reusable composite controls.</span></span> <span data-ttu-id="23626-184">複合控制項現在可以做為建置其他控制項的基底。</span><span class="sxs-lookup"><span data-stu-id="23626-184">Your composite control can now be used as a base upon which other controls can be built.</span></span> <span data-ttu-id="23626-185">從基底類別衍生類別的處理序稱為「繼承」。</span><span class="sxs-lookup"><span data-stu-id="23626-185">The process of deriving a class from a base class is called *inheritance*.</span></span> <span data-ttu-id="23626-186">在本節中，您將建立稱為 `ctlAlarmClock` 的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-186">In this section, you will create a composite control called `ctlAlarmClock`.</span></span> <span data-ttu-id="23626-187">這個控制項將會從其父控制項 (`ctlClock`) 衍生。</span><span class="sxs-lookup"><span data-stu-id="23626-187">This control will be derived from its parent control, `ctlClock`.</span></span> <span data-ttu-id="23626-188">您將學習藉由覆寫父方法並且新增新方法和屬性，來擴充 `ctlClock` 的功能。</span><span class="sxs-lookup"><span data-stu-id="23626-188">You will learn to extend the functionality of `ctlClock` by overriding parent methods and adding new methods and properties.</span></span>

 <span data-ttu-id="23626-189">建立繼承的控制項的第一個步驟是從其父代衍生。</span><span class="sxs-lookup"><span data-stu-id="23626-189">The first step in creating an inherited control is to derive it from its parent.</span></span> <span data-ttu-id="23626-190">這個動作會建立新的控制項，其中具有父控制項的所有屬性、方法和圖形特性，但是也可以做為基底，以新增新的或修改功能。</span><span class="sxs-lookup"><span data-stu-id="23626-190">This action creates a new control that has all of the properties, methods, and graphical characteristics of the parent control, but can also act as a base for the addition of new or modified functionality.</span></span>

### <a name="to-create-the-inherited-control"></a><span data-ttu-id="23626-191">若要建立繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="23626-191">To create the inherited control</span></span>

1. <span data-ttu-id="23626-192">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClockLib]，指向 [新增]，然後按一下 [使用者控制項]。</span><span class="sxs-lookup"><span data-stu-id="23626-192">In Solution Explorer, right-click **ctlClockLib**, point to **Add**, and then click **User Control**.</span></span>

     <span data-ttu-id="23626-193">[新增項目] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="23626-193">The **Add New Item** dialog box opens.</span></span>

2. <span data-ttu-id="23626-194">選取**繼承的使用者控制項**範本。</span><span class="sxs-lookup"><span data-stu-id="23626-194">Select the **Inherited User Control** template.</span></span>

3. <span data-ttu-id="23626-195">在 [名稱] 方塊中，輸入 `ctlAlarmClock.vb` 然後按一下 [新增]。</span><span class="sxs-lookup"><span data-stu-id="23626-195">In the **Name** box, type `ctlAlarmClock.vb`, and then click **Add**.</span></span>

     <span data-ttu-id="23626-196">[繼承選取器] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="23626-196">The **Inheritance Picker** dialog box appears.</span></span>

4. <span data-ttu-id="23626-197">在 [元件名稱] 底下，按兩下 [ctlClock]。</span><span class="sxs-lookup"><span data-stu-id="23626-197">Under **Component Name**, double-click **ctlClock**.</span></span>

5. <span data-ttu-id="23626-198">在 [方案總管] 中，瀏覽目前的專案。</span><span class="sxs-lookup"><span data-stu-id="23626-198">In Solution Explorer, browse through the current projects.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="23626-199">名為 **ctlAlarmClock.vb** 的檔案已新增至目前的專案。</span><span class="sxs-lookup"><span data-stu-id="23626-199">A file called **ctlAlarmClock.vb** has been added to the current project.</span></span>

### <a name="adding-the-alarm-properties"></a><span data-ttu-id="23626-200">新增警示屬性</span><span class="sxs-lookup"><span data-stu-id="23626-200">Adding the Alarm Properties</span></span>
 <span data-ttu-id="23626-201">屬性會以新增至複合控制項的相同方式，新增至繼承的控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-201">Properties are added to an inherited control in the same way they are added to a composite control.</span></span> <span data-ttu-id="23626-202">您現在會使用屬性宣告語法將兩個屬性新增至您的控制項︰`AlarmTime`，它將會儲存警示停止之日期和時間的值，以及 `AlarmSet`，它將會指示是否已設定警示。</span><span class="sxs-lookup"><span data-stu-id="23626-202">You will now use the property declaration syntax to add two properties to your control: `AlarmTime`, which will store the value of the date and time the alarm is to go off, and `AlarmSet`, which will indicate whether the alarm is set.</span></span>

#### <a name="to-add-properties-to-your-composite-control"></a><span data-ttu-id="23626-203">若要將屬性新增至複合控制項</span><span class="sxs-lookup"><span data-stu-id="23626-203">To add properties to your composite control</span></span>

1. <span data-ttu-id="23626-204">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock]，然後按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="23626-204">In Solution Explorer, right-click **ctlAlarmClock**, and then click **View Code**.</span></span>

2. <span data-ttu-id="23626-205">尋找 ctlAlarmClock 控制項的類別宣告，它會顯示為 `Public Class ctlAlarmClock`。</span><span class="sxs-lookup"><span data-stu-id="23626-205">Locate the class declaration for the ctlAlarmClock control, which appears as `Public Class ctlAlarmClock`.</span></span>  <span data-ttu-id="23626-206">在類別宣告中插入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="23626-206">In the class declaration, insert the following code.</span></span>

    ```vb
    Private dteAlarmTime As Date
    Private blnAlarmSet As Boolean
    ' These properties will be declared as Public to allow future
    ' developers to access them.
    Public Property AlarmTime() As Date
        Get
            Return dteAlarmTime
        End Get
        Set(ByVal value as Date)
            dteAlarmTime = value
        End Set
    End Property
    Public Property AlarmSet() As Boolean
        Get
            Return blnAlarmSet
        End Get
        Set(ByVal value as Boolean)
            blnAlarmSet = value
        End Set
    End Property
    ```

### <a name="adding-to-the-graphical-interface-of-the-control"></a><span data-ttu-id="23626-207">新增至控制項的圖形化介面</span><span class="sxs-lookup"><span data-stu-id="23626-207">Adding to the Graphical Interface of the Control</span></span>
 <span data-ttu-id="23626-208">繼承的控制項具有視覺化介面，與它所繼承的控制項相同。</span><span class="sxs-lookup"><span data-stu-id="23626-208">Your inherited control has a visual interface that is identical to the control it inherits from.</span></span> <span data-ttu-id="23626-209">它擁有與其父控制項相同的組成控制項，但是無法使用組成控制項的屬性，除非特別公開。</span><span class="sxs-lookup"><span data-stu-id="23626-209">It possesses the same constituent controls as its parent control, but the properties of the constituent controls will not be available unless they were specifically exposed.</span></span> <span data-ttu-id="23626-210">您可以使用新增至任何複合控制項的相同方式，新增至繼承的複合控制項的圖形化介面。</span><span class="sxs-lookup"><span data-stu-id="23626-210">You may add to the graphical interface of an inherited composite control in the same manner as you would add to any composite control.</span></span> <span data-ttu-id="23626-211">若要繼續新增至警示時鐘的視覺化介面，您要新增標籤控制項，該控制項會在警示響起時閃爍。</span><span class="sxs-lookup"><span data-stu-id="23626-211">To continue adding to your alarm clock's visual interface, you will add a label control that will flash when the alarm is sounding.</span></span>

#### <a name="to-add-the-label-control"></a><span data-ttu-id="23626-212">若要新增標籤控制項</span><span class="sxs-lookup"><span data-stu-id="23626-212">To add the label control</span></span>

1. <span data-ttu-id="23626-213">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock]，然後按一下 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="23626-213">In Solution Explorer, right-click **ctlAlarmClock**, and click **View Designer**.</span></span>

     <span data-ttu-id="23626-214">          `ctlAlarmClock` 的設計工具隨即在主視窗中開啟。</span><span class="sxs-lookup"><span data-stu-id="23626-214">The designer for `ctlAlarmClock` opens in the main window.</span></span>

2. <span data-ttu-id="23626-215">按一下 `lblDisplay` (控制項的顯示部分)，並檢視 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="23626-215">Click `lblDisplay` (the display portion of the control), and view the Properties window.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="23626-216">所有屬性顯示時，它們會以灰色顯示。</span><span class="sxs-lookup"><span data-stu-id="23626-216">While all the properties are displayed, they are dimmed.</span></span> <span data-ttu-id="23626-217">這表示這些屬性是 `lblDisplay` 的原生屬性，而且無法修改或在 [屬性] 視窗中存取。</span><span class="sxs-lookup"><span data-stu-id="23626-217">This indicates that these properties are native to `lblDisplay` and cannot be modified or accessed in the Properties window.</span></span> <span data-ttu-id="23626-218">根據預設，包含在複合控制項中的控制項是 `Private`，而且其屬性無法使用任何方法存取。</span><span class="sxs-lookup"><span data-stu-id="23626-218">By default, controls contained in a composite control are `Private`, and their properties are not accessible by any means.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="23626-219">如果您想要讓複合控制項的後續使用者可以存取其內部控制項，請將它們宣告為 `Public` 或 `Protected`。</span><span class="sxs-lookup"><span data-stu-id="23626-219">If you want subsequent users of your composite control to have access to its internal controls, declare them as `Public` or `Protected`.</span></span> <span data-ttu-id="23626-220">這可讓您使用適當的程式碼，設定及修改包含在複合控制項中的控制項屬性。</span><span class="sxs-lookup"><span data-stu-id="23626-220">This will allow you to set and modify properties of controls contained within your composite control by using the appropriate code.</span></span>

3. <span data-ttu-id="23626-221"><xref:System.Windows.Forms.Label>將控制項新增至您的複合控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-221">Add a <xref:System.Windows.Forms.Label> control to your composite control.</span></span>

4. <span data-ttu-id="23626-222">使用滑鼠, 將<xref:System.Windows.Forms.Label>控制項拖曳到顯示方塊的正下方。</span><span class="sxs-lookup"><span data-stu-id="23626-222">Using the mouse, drag the <xref:System.Windows.Forms.Label> control immediately beneath the display box.</span></span> <span data-ttu-id="23626-223">在 [屬性] 視窗中設定下列屬性。</span><span class="sxs-lookup"><span data-stu-id="23626-223">In the Properties window, set the following properties.</span></span>

    |<span data-ttu-id="23626-224">屬性</span><span class="sxs-lookup"><span data-stu-id="23626-224">Property</span></span>|<span data-ttu-id="23626-225">設定</span><span class="sxs-lookup"><span data-stu-id="23626-225">Setting</span></span>|
    |--------------|-------------|
    |<span data-ttu-id="23626-226">**名稱**</span><span class="sxs-lookup"><span data-stu-id="23626-226">**Name**</span></span>|`lblAlarm`|
    |<span data-ttu-id="23626-227">**Text**</span><span class="sxs-lookup"><span data-stu-id="23626-227">**Text**</span></span>|<span data-ttu-id="23626-228">**Alarm!**</span><span class="sxs-lookup"><span data-stu-id="23626-228">**Alarm!**</span></span>|
    |<span data-ttu-id="23626-229">**TextAlign**</span><span class="sxs-lookup"><span data-stu-id="23626-229">**TextAlign**</span></span>|`MiddleCenter`|
    |<span data-ttu-id="23626-230">**可見**</span><span class="sxs-lookup"><span data-stu-id="23626-230">**Visible**</span></span>|`False`|

### <a name="adding-the-alarm-functionality"></a><span data-ttu-id="23626-231">新增警示功能</span><span class="sxs-lookup"><span data-stu-id="23626-231">Adding the Alarm Functionality</span></span>
 <span data-ttu-id="23626-232">在先前的程序中，您新增屬性和控制項，在您的複合控制項中啟用警示功能。</span><span class="sxs-lookup"><span data-stu-id="23626-232">In the previous procedures, you added properties and a control that will enable alarm functionality in your composite control.</span></span> <span data-ttu-id="23626-233">在此程序中，您將會新增程式碼以比較目前時間與警示時間，如果它們相同，則讓警示發出聲響與閃爍。</span><span class="sxs-lookup"><span data-stu-id="23626-233">In this procedure, you will add code to compare the current time to the alarm time and, if they are the same, to sound and flash an alarm.</span></span> <span data-ttu-id="23626-234">藉由覆寫 `ctlClock` 的 `Timer1_Tick` 方法，並且將額外程式碼新增至其中，您就可以擴充 `ctlAlarmClock` 的功能，同時保留 `ctlClock` 的所有固有功能。</span><span class="sxs-lookup"><span data-stu-id="23626-234">By overriding the `Timer1_Tick` method of `ctlClock` and adding additional code to it, you will extend the capability of `ctlAlarmClock` while retaining all of the inherent functionality of `ctlClock`.</span></span>

#### <a name="to-override-the-timer1_tick-method-of-ctlclock"></a><span data-ttu-id="23626-235">若要覆寫 ctlClock 的 Timer1_Tick 方法</span><span class="sxs-lookup"><span data-stu-id="23626-235">To override the Timer1_Tick method of ctlClock</span></span>

1. <span data-ttu-id="23626-236">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock.vb]，然後按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="23626-236">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Code**.</span></span>

2. <span data-ttu-id="23626-237">尋找 `Private blnAlarmSet As Boolean` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="23626-237">Locate the `Private blnAlarmSet As Boolean` statement.</span></span> <span data-ttu-id="23626-238">緊接著在其下新增下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="23626-238">Immediately beneath it, add the following statement.</span></span>

    ```vb
    Dim blnColorTicker as Boolean
    ```

3. <span data-ttu-id="23626-239">在頁面底部尋找 `End Class` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="23626-239">Locate the `End Class` statement at the bottom of the page.</span></span> <span data-ttu-id="23626-240">緊接在 `End Class` 陳述式之前，新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="23626-240">Just before the `End Class` statement, add the following code.</span></span>

    ```vb
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _
        As System.EventArgs)
        ' Calls the Timer1_Tick method of ctlClock.
        MyBase.Timer1_Tick(sender, e)
        ' Checks to see if the Alarm is set.
        If AlarmSet = False Then
            Exit Sub
        End If
        ' If the date, hour, and minute of the alarm time are the same as
        ' now, flash and beep an alarm.
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _
            AlarmTime.Minute = Now.Minute Then
            ' Sounds an audible beep.
            Beep()
            ' Sets lblAlarmVisible to True, and changes the background color based on the
            ' value of blnColorTicker. The background color of the label will
            ' flash once per tick of the clock.
            lblAlarm.Visible = True
            If blnColorTicker = False Then
                lblAlarm.BackColor = Color.PeachPuff
                blnColorTicker = True
            Else
                lblAlarm.BackColor = Color.Plum
                blnColorTicker = False
            End If
        Else
            ' Once the alarm has sounded for a minute, the label is made
            ' invisible again.
            lblAlarm.Visible = False
        End If
    End Sub
    ```

     <span data-ttu-id="23626-241">新增這個程式碼會完成幾項工作。</span><span class="sxs-lookup"><span data-stu-id="23626-241">The addition of this code accomplishes several tasks.</span></span> <span data-ttu-id="23626-242">          `Overrides` 陳述式會指示控制項使用這個方法來取代繼承自基底控制項的方法。</span><span class="sxs-lookup"><span data-stu-id="23626-242">The `Overrides` statement directs the control to use this method in place of the method that was inherited from the base control.</span></span> <span data-ttu-id="23626-243">呼叫這個方法時，它會呼叫它藉由叫用 `MyBase.Timer1_Tick` 陳述式覆寫的方法，確保併入原始控制項的所有功能在此控制項中重現。</span><span class="sxs-lookup"><span data-stu-id="23626-243">When this method is called, it calls the method it overrides by invoking the `MyBase.Timer1_Tick` statement, ensuring that all of the functionality incorporated in the original control is reproduced in this control.</span></span> <span data-ttu-id="23626-244">接著，它會執行其他程式碼以併入警示功能。</span><span class="sxs-lookup"><span data-stu-id="23626-244">It then runs additional code to incorporate the alarm functionality.</span></span> <span data-ttu-id="23626-245">發生警示時，閃爍標籤控制項就會出現，而且會聽到嗶聲。</span><span class="sxs-lookup"><span data-stu-id="23626-245">A flashing label control will appear when the alarm occurs, and an audible beep will be heard.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="23626-246">因為您正在覆寫繼承的事件處理常式，您不需要指定事件與 `Handles` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="23626-246">Because you are overriding an inherited event handler, you do not have to specify the event with the `Handles` keyword.</span></span> <span data-ttu-id="23626-247">事件已傳入。</span><span class="sxs-lookup"><span data-stu-id="23626-247">The event is already hooked up.</span></span> <span data-ttu-id="23626-248">您覆寫的所有項目是處理常式的實作。</span><span class="sxs-lookup"><span data-stu-id="23626-248">All you are overriding is the implementation of the handler.</span></span>

     <span data-ttu-id="23626-249">警示時鐘控制項已接近完成。</span><span class="sxs-lookup"><span data-stu-id="23626-249">Your alarm clock control is almost complete.</span></span> <span data-ttu-id="23626-250">唯一剩餘的事項是實作將它關閉的方式。</span><span class="sxs-lookup"><span data-stu-id="23626-250">The only thing that remains is to implement a way to turn it off.</span></span> <span data-ttu-id="23626-251">若要這樣做，您要將程式碼新增至 `lblAlarm_Click` 方法。</span><span class="sxs-lookup"><span data-stu-id="23626-251">To do this, you will add code to the `lblAlarm_Click` method.</span></span>

#### <a name="to-implement-the-shutoff-method"></a><span data-ttu-id="23626-252">若要實作關閉方法</span><span class="sxs-lookup"><span data-stu-id="23626-252">To implement the shutoff method</span></span>

1. <span data-ttu-id="23626-253">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlAlarmClock.vb]，然後按一下 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="23626-253">In Solution Explorer, right-click **ctlAlarmClock.vb**, and then click **View Designer**.</span></span>

2. <span data-ttu-id="23626-254">在設計工具中，按兩下 [lblAlarm]。</span><span class="sxs-lookup"><span data-stu-id="23626-254">In the designer, double-click **lblAlarm**.</span></span> <span data-ttu-id="23626-255">[程式碼編輯器] 隨即開啟至 `Private Sub lblAlarm_Click` 行。</span><span class="sxs-lookup"><span data-stu-id="23626-255">The **Code Editor** opens to the `Private Sub lblAlarm_Click` line.</span></span>

3. <span data-ttu-id="23626-256">修改此方法，使它類似下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="23626-256">Modify this method so that it resembles the following code.</span></span>

    ```vb
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _
     System.EventArgs) Handles lblAlarm.Click
        ' Turns off the alarm.
        AlarmSet = False
        ' Hides the flashing label.
        lblAlarm.Visible = False
    End Sub
    ```

4. <span data-ttu-id="23626-257">在 [檔案] 功能表上按一下 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="23626-257">On the **File** menu, click **Save All** to save the project.</span></span>

### <a name="using-the-inherited-control-on-a-form"></a><span data-ttu-id="23626-258">在表單上使用繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="23626-258">Using the Inherited Control on a Form</span></span>
 <span data-ttu-id="23626-259">您可以依照測試基類控制項`ctlClock`的相同方式來測試繼承的控制項:按下 F5 鍵以建置專案，並且在 **UserControl 測試容器**中執行您的控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-259">You can test your inherited control the same way you tested the base class control, `ctlClock`: Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="23626-260">如需詳細資訊，請參閱[如何：測試 UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="23626-260">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

 <span data-ttu-id="23626-261">若要使用控制項，您必須將它裝載在表單上。</span><span class="sxs-lookup"><span data-stu-id="23626-261">To put your control to use, you will need to host it on a form.</span></span> <span data-ttu-id="23626-262">如同標準複合控制項，繼承的複合控制項無法獨立存在，而且必須裝載在表單或其他容器。</span><span class="sxs-lookup"><span data-stu-id="23626-262">As with a standard composite control, an inherited composite control cannot stand alone and must be hosted in a form or other container.</span></span> <span data-ttu-id="23626-263">由於 `ctlAlarmClock` 有更深入的功能，需要額外的程式碼來進行測試。</span><span class="sxs-lookup"><span data-stu-id="23626-263">Since `ctlAlarmClock` has a greater depth of functionality, additional code is required to test it.</span></span> <span data-ttu-id="23626-264">在此程序中，您將撰寫一個簡單的程式來測試 `ctlAlarmClock` 的功能。</span><span class="sxs-lookup"><span data-stu-id="23626-264">In this procedure, you will write a simple program to test the functionality of `ctlAlarmClock`.</span></span> <span data-ttu-id="23626-265">您將撰寫程式碼以設定及顯示 `ctlAlarmClock` 的 `AlarmTime` 屬性，然後測試其固有功能。</span><span class="sxs-lookup"><span data-stu-id="23626-265">You will write code to set and display the `AlarmTime` property of `ctlAlarmClock`, and will test its inherent functions.</span></span>

#### <a name="to-build-and-add-your-control-to-a-test-form"></a><span data-ttu-id="23626-266">若要建置控制項並且新增至測試表單</span><span class="sxs-lookup"><span data-stu-id="23626-266">To build and add your control to a test form</span></span>

1. <span data-ttu-id="23626-267">在 [方案總管] 中，以滑鼠右鍵按一下 [ctlClockLib]，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="23626-267">In Solution Explorer, right-click **ctlClockLib**, and then click **Build**.</span></span>

2. <span data-ttu-id="23626-268">在 [檔案] 功能表上，指向 [加入]，然後按一下 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="23626-268">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>

3. <span data-ttu-id="23626-269">將新的 **Windows 應用程式**專案新增至解決方案，並且將它命名為 `Test`。</span><span class="sxs-lookup"><span data-stu-id="23626-269">Add a new **Windows Application** project to the solution, and name it `Test`.</span></span>

     <span data-ttu-id="23626-270">[測試] 專案隨即新增至 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="23626-270">The **Test** project is added to Solution Explorer.</span></span>

4. <span data-ttu-id="23626-271">在 [方案總管] 中，以滑鼠右鍵按一下 `Test` 專案節點，然後按一下 [加入參考]以顯示 [加入參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="23626-271">In Solution Explorer, right-click the `Test` project node, and then click **Add Reference** to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="23626-272">按一下標籤為 [專案] 的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="23626-272">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="23626-273">專案 **ctlClockLib** 會列在 [專案名稱] 底下。</span><span class="sxs-lookup"><span data-stu-id="23626-273">The project **ctlClockLib** will be listed under **Project Name**.</span></span> <span data-ttu-id="23626-274">按兩下 [ctlClockLib] 以將參考新增至測試專案。</span><span class="sxs-lookup"><span data-stu-id="23626-274">Double-click **ctlClockLib** to add the reference to the test project.</span></span>

6. <span data-ttu-id="23626-275">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後按一下 [建置]。</span><span class="sxs-lookup"><span data-stu-id="23626-275">In Solution Explorer, right-click **Test**, and then click **Build**.</span></span>

7. <span data-ttu-id="23626-276">在 [工具箱] 中，展開 [ctlClockLib 元件] 節點。</span><span class="sxs-lookup"><span data-stu-id="23626-276">In the **Toolbox**, expand the **ctlClockLib Components** node.</span></span>

8. <span data-ttu-id="23626-277">按兩下 [ctlAlarmClock] 以將 `ctlAlarmClock` 的執行個體新增至表單。</span><span class="sxs-lookup"><span data-stu-id="23626-277">Double-click **ctlAlarmClock** to add an instance of `ctlAlarmClock` to your form.</span></span>

9. <span data-ttu-id="23626-278">在 [**工具箱**] 中, 找出並按兩下 [ **DateTimePicker** ] <xref:System.Windows.Forms.DateTimePicker>將控制項新增至<xref:System.Windows.Forms.Label>表單, 然後按兩下 [**標籤**] 來加入控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-278">In the **Toolbox**, locate and double-click **DateTimePicker** to add a <xref:System.Windows.Forms.DateTimePicker> control to your form, and then add a <xref:System.Windows.Forms.Label> control by double-clicking **Label**.</span></span>

10. <span data-ttu-id="23626-279">使用滑鼠將控制項放置在表單上方便的位置。</span><span class="sxs-lookup"><span data-stu-id="23626-279">Use the mouse to position the controls in a convenient place on the form.</span></span>

11. <span data-ttu-id="23626-280">以下列方式設定這些控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="23626-280">Set the properties of these controls in the following manner.</span></span>

    |<span data-ttu-id="23626-281">控制項</span><span class="sxs-lookup"><span data-stu-id="23626-281">Control</span></span>|<span data-ttu-id="23626-282">屬性</span><span class="sxs-lookup"><span data-stu-id="23626-282">Property</span></span>|<span data-ttu-id="23626-283">值</span><span class="sxs-lookup"><span data-stu-id="23626-283">Value</span></span>|
    |-------------|--------------|-----------|
    |`label1`|<span data-ttu-id="23626-284">**Text**</span><span class="sxs-lookup"><span data-stu-id="23626-284">**Text**</span></span>|`(blank space)`|
    ||<span data-ttu-id="23626-285">**名稱**</span><span class="sxs-lookup"><span data-stu-id="23626-285">**Name**</span></span>|`lblTest`|
    |`dateTimePicker1`|<span data-ttu-id="23626-286">**名稱**</span><span class="sxs-lookup"><span data-stu-id="23626-286">**Name**</span></span>|`dtpTest`|
    ||<span data-ttu-id="23626-287">**格式**</span><span class="sxs-lookup"><span data-stu-id="23626-287">**Format**</span></span>|<xref:System.Windows.Forms.DateTimePickerFormat.Time>|

12. <span data-ttu-id="23626-288">在設計工具中，按兩下 [dtpTest]。</span><span class="sxs-lookup"><span data-stu-id="23626-288">In the designer, double-click **dtpTest**.</span></span>

     <span data-ttu-id="23626-289">[程式碼編輯器] 隨即開啟至 `Private Sub dtpTest_ValueChanged`。</span><span class="sxs-lookup"><span data-stu-id="23626-289">The **Code Editor** opens to `Private Sub dtpTest_ValueChanged`.</span></span>

13. <span data-ttu-id="23626-290">修改此程式碼，使它類似下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="23626-290">Modify the code so that it resembles the following.</span></span>

    ```vb
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _
        System.EventArgs) Handles dtpTest.ValueChanged
        ctlAlarmClock1.AlarmTime = dtpTest.Value
        ctlAlarmClock1.AlarmSet = True
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _
            "hh:mm")
    End Sub
    ```

14. <span data-ttu-id="23626-291">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後按一下 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="23626-291">In Solution Explorer, right-click **Test**, and then click **Set as StartUp Project**.</span></span>

15. <span data-ttu-id="23626-292">按一下 [偵錯] 功能表上的 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="23626-292">On the **Debug** menu, click **Start Debugging**.</span></span>

     <span data-ttu-id="23626-293">測試程式隨即啟動。</span><span class="sxs-lookup"><span data-stu-id="23626-293">The test program starts.</span></span> <span data-ttu-id="23626-294">請注意, `ctlAlarmClock`控制項中的目前時間已更新, 而且開始時間會顯示<xref:System.Windows.Forms.DateTimePicker>在控制項中。</span><span class="sxs-lookup"><span data-stu-id="23626-294">Note that the current time is updated in the `ctlAlarmClock` control, and that the starting time is shown in the <xref:System.Windows.Forms.DateTimePicker> control.</span></span>

16. <span data-ttu-id="23626-295">按一下顯示<xref:System.Windows.Forms.DateTimePicker>該小時分鐘數的。</span><span class="sxs-lookup"><span data-stu-id="23626-295">Click the <xref:System.Windows.Forms.DateTimePicker> where the minutes of the hour are displayed.</span></span>

17. <span data-ttu-id="23626-296">使用鍵盤，將分鐘值設定為大於 `ctlAlarmClock` 顯示的目前時間一分鐘。</span><span class="sxs-lookup"><span data-stu-id="23626-296">Using the keyboard, set a value for minutes that is one minute greater than the current time shown by `ctlAlarmClock`.</span></span>

     <span data-ttu-id="23626-297">警示設定的時間會在 `lblTest` 中顯示。</span><span class="sxs-lookup"><span data-stu-id="23626-297">The time for the alarm setting is shown in `lblTest`.</span></span> <span data-ttu-id="23626-298">等候顯示的時間達到警示設定時間。</span><span class="sxs-lookup"><span data-stu-id="23626-298">Wait for the displayed time to reach the alarm setting time.</span></span> <span data-ttu-id="23626-299">當顯示的時間達到警示設定時間，則會響起嗶聲且 `lblAlarm` 會閃爍。</span><span class="sxs-lookup"><span data-stu-id="23626-299">When the displayed time reaches the time to which the alarm is set, the beep will sound and `lblAlarm` will flash.</span></span>

18. <span data-ttu-id="23626-300">按一下 `lblAlarm` 來關閉警示。</span><span class="sxs-lookup"><span data-stu-id="23626-300">Turn off the alarm by clicking `lblAlarm`.</span></span> <span data-ttu-id="23626-301">您現在可以重設警示。</span><span class="sxs-lookup"><span data-stu-id="23626-301">You may now reset the alarm.</span></span>

     <span data-ttu-id="23626-302">本逐步解說涵蓋了數個重要概念。</span><span class="sxs-lookup"><span data-stu-id="23626-302">This walkthrough has covered a number of key concepts.</span></span> <span data-ttu-id="23626-303">您已經了解藉由將控制項和元件合併成複合控制項容器，來建立複合控制項。</span><span class="sxs-lookup"><span data-stu-id="23626-303">You have learned to create a composite control by combining controls and components into a composite control container.</span></span> <span data-ttu-id="23626-304">您已經了解將屬性新增至您的控制項，以及撰寫程式碼來實作自訂功能。</span><span class="sxs-lookup"><span data-stu-id="23626-304">You have learned to add properties to your control, and to write code to implement custom functionality.</span></span> <span data-ttu-id="23626-305">在最後一節中，您會了解透過繼承擴充指定複合控制項的功能，並且藉由覆寫這些方法來變更主方法的功能。</span><span class="sxs-lookup"><span data-stu-id="23626-305">In the last section, you learned to extend the functionality of a given composite control through inheritance, and to alter the functionality of host methods by overriding those methods.</span></span>

## <a name="see-also"></a><span data-ttu-id="23626-306">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23626-306">See also</span></span>

- [<span data-ttu-id="23626-307">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="23626-307">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="23626-308">如何：撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="23626-308">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)
- <span data-ttu-id="23626-309">[如何：在 [選擇工具箱專案] 對話方塊中顯示控制項](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="23626-309">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>
