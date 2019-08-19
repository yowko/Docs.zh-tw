---
title: 逐步解說：使用 Visual Basic 繼承 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 0891b64fdb26953ab90f3da931f04513ac9e8bcf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040218"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="911ca-102">逐步解說：使用 Visual Basic 繼承 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="911ca-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="911ca-103">有了 Visual Basic, 您就可以透過*繼承*來建立功能強大的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="911ca-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="911ca-104">您可以透過繼承建立控制項，不僅保留標準 Windows Forms 控制項的所有固有功能，同時也納入自訂功能。</span><span class="sxs-lookup"><span data-stu-id="911ca-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="911ca-105">在本逐步解說中，您將會建立簡單的繼承控制項，名為 `ValueButton`。</span><span class="sxs-lookup"><span data-stu-id="911ca-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="911ca-106">此按鈕將繼承標準 Windows Forms <xref:System.Windows.Forms.Button>控制項的功能, 並會公開名`ButtonValue`為的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="911ca-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="911ca-107">建立專案</span><span class="sxs-lookup"><span data-stu-id="911ca-107">Creating the Project</span></span>
 <span data-ttu-id="911ca-108">當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="911ca-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="911ca-109">若要建立 ValueButtonLib 控制項程式庫和 ValueButton 控制項</span><span class="sxs-lookup"><span data-stu-id="911ca-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="911ca-110">在 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]，開啟 [新增專案] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="911ca-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="911ca-111">從 Visual Basic 專案清單中選取 [ **Windows Forms 控制項程式庫**] 專案範本, 然後`ValueButtonLib`在 [**名稱**] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="911ca-111">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="911ca-112">專案名稱，`ValueButtonLib`，預設也會指派給根命名空間。</span><span class="sxs-lookup"><span data-stu-id="911ca-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="911ca-113">根命名空間是用來限定組件中的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="911ca-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="911ca-114">例如，如果兩個組件提供元件，名為 `ValueButton`，您可以使用 `ValueButtonLib.ValueButton` 指定您的 `ValueButton` 元件。</span><span class="sxs-lookup"><span data-stu-id="911ca-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="911ca-115">如需詳細資訊，請參閱 [Visual Basic 中的命名空間](~/docs/visual-basic/programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="911ca-115">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>

3. <span data-ttu-id="911ca-116">在 [方案總管] 中，以滑鼠右鍵按一下 [UserControl1.vb]，然後從捷徑功能表選擇 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="911ca-116">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="911ca-117">將檔案名稱變更為 `ValueButton.vb`。</span><span class="sxs-lookup"><span data-stu-id="911ca-117">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="911ca-118">當系統詢問您是否要重新命名程式碼元素 'UserControl1' 的所有參考時，按一下 [是]按鈕。</span><span class="sxs-lookup"><span data-stu-id="911ca-118">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>

4. <span data-ttu-id="911ca-119">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="911ca-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="911ca-120">開啟 [ValueButton.vb] 節點以顯示設計工具產生的程式碼檔案，**ValueButton.Designer.vb**。</span><span class="sxs-lookup"><span data-stu-id="911ca-120">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="911ca-121">在 [程式碼編輯器] 中開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="911ca-121">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="911ca-122">找出`Class`語句, `Partial Public Class ValueButton`並將此控制項繼承的<xref:System.Windows.Forms.UserControl>目標型別變更為<xref:System.Windows.Forms.Button>。</span><span class="sxs-lookup"><span data-stu-id="911ca-122">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="911ca-123">這可讓您的<xref:System.Windows.Forms.Button>繼承控制項繼承控制項的所有功能。</span><span class="sxs-lookup"><span data-stu-id="911ca-123">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="911ca-124">找出`InitializeComponent`方法, 並移除<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>指派屬性的行。</span><span class="sxs-lookup"><span data-stu-id="911ca-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="911ca-125">這個屬性不存在於<xref:System.Windows.Forms.Button>控制項中。</span><span class="sxs-lookup"><span data-stu-id="911ca-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="911ca-126">從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="911ca-126">From the **File** menu, choose **Save All** to save the project.</span></span>

     <span data-ttu-id="911ca-127">請注意，視覺化設計工具再也無法使用。</span><span class="sxs-lookup"><span data-stu-id="911ca-127">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="911ca-128"><xref:System.Windows.Forms.Button>由於控制項會進行自己的繪製, 因此您無法在設計工具中修改其外觀。</span><span class="sxs-lookup"><span data-stu-id="911ca-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="911ca-129">它的視覺標記法會與繼承自的類別 (也就是<xref:System.Windows.Forms.Button>) 完全相同, 除非在程式碼中修改。</span><span class="sxs-lookup"><span data-stu-id="911ca-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>

> [!NOTE]
>  <span data-ttu-id="911ca-130">您仍然可以將元件 (其中沒有任何 UI 元素) 新增至設計介面。</span><span class="sxs-lookup"><span data-stu-id="911ca-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="911ca-131">將屬性新增至繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="911ca-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="911ca-132">繼承 Windows Forms 控制項的可能用法之一是建立外觀和行為 (外觀及操作) 與標準的 Windows Forms 控制項相同的控制項，但是公開自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="911ca-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="911ca-133">在本節中，您會將名為 `ButtonValue` 的屬性新增至您的控制項。</span><span class="sxs-lookup"><span data-stu-id="911ca-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="911ca-134">若要新增 Value 屬性</span><span class="sxs-lookup"><span data-stu-id="911ca-134">To add the Value property</span></span>

1. <span data-ttu-id="911ca-135">在 [方案總管] 中，以滑鼠右鍵按一下 [ValueButton.vb]，然後從捷徑功能表按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="911ca-135">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="911ca-136">尋找 `Public Class ValueButton` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="911ca-136">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="911ca-137">緊接在此陳述式底下，輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="911ca-137">Immediately beneath this statement, type the following code:</span></span>

    ```vb
    ' Creates the private variable that will store the value of your
    ' property.
    Private varValue as integer
    ' Declares the property.
    Property ButtonValue() as Integer
    ' Sets the method for retrieving the value of your property.
       Get
          Return varValue
       End Get
    ' Sets the method for setting the value of your property.
       Set(ByVal Value as Integer)
          varValue = Value
       End Set
    End Property
    ```

     <span data-ttu-id="911ca-138">此程式碼會設定方法，系統會使用該方法來儲存和擷取 `ButtonValue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="911ca-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="911ca-139">          `Get` 陳述式會將傳回值設為儲存在私用變數 `varValue` 的值，而 `Set` 陳述式會使用 `Value` 關鍵字設定私用變數的值。</span><span class="sxs-lookup"><span data-stu-id="911ca-139">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>

3. <span data-ttu-id="911ca-140">從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="911ca-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="911ca-141">測試您的控制項</span><span class="sxs-lookup"><span data-stu-id="911ca-141">Testing Your Control</span></span>
 <span data-ttu-id="911ca-142">控制項不是獨立專案；它們必須裝載在容器中。</span><span class="sxs-lookup"><span data-stu-id="911ca-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="911ca-143">若要測試您的控制項，您必須提供測試專案讓控制項在其中執行。</span><span class="sxs-lookup"><span data-stu-id="911ca-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="911ca-144">您也必須藉由建置 (編譯) 控制項，讓控制項可供測試專案存取。</span><span class="sxs-lookup"><span data-stu-id="911ca-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="911ca-145">在本節中，您將會建置您的控制項，並且在 Windows Form 中進行測試。</span><span class="sxs-lookup"><span data-stu-id="911ca-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="911ca-146">若要建置您的控制項</span><span class="sxs-lookup"><span data-stu-id="911ca-146">To build your control</span></span>

1. <span data-ttu-id="911ca-147">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="911ca-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="911ca-148">建置應該會成功，沒有編譯器錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="911ca-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="911ca-149">若要建立測試專案</span><span class="sxs-lookup"><span data-stu-id="911ca-149">To create a test project</span></span>

1. <span data-ttu-id="911ca-150">在 [檔案] 功能表上，指向 [新增]，然後選取 [新增專案]，以開啟 [加入新的專案]對話方塊。</span><span class="sxs-lookup"><span data-stu-id="911ca-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="911ca-151">選取 [Visual Basic 專案] 節點, 然後按一下 [ **Windows Forms 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="911ca-151">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="911ca-152">在 [名稱] 方塊中，輸入 `Test`。</span><span class="sxs-lookup"><span data-stu-id="911ca-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="911ca-153">在方案總管中，按一下 [顯示所有檔案] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="911ca-153">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="911ca-154">在 [方案總管] 中，以滑鼠右鍵按一下測試專案的 [參考] 節點，然後從捷徑功能表選取 [加入參考]，以顯示 [加入參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="911ca-154">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

6. <span data-ttu-id="911ca-155">按一下 [專案] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="911ca-155">Click the **Projects** tab.</span></span>

7. <span data-ttu-id="911ca-156">按一下標籤為 [專案] 的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="911ca-156">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="911ca-157">您的 `ValueButtonLib` 專案會列在 [專案名稱] 底下。</span><span class="sxs-lookup"><span data-stu-id="911ca-157">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="911ca-158">按兩下專案以將參考新增至測試專案。</span><span class="sxs-lookup"><span data-stu-id="911ca-158">Double-click the project to add the reference to the test project.</span></span>

8. <span data-ttu-id="911ca-159">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後選取 [建置]。</span><span class="sxs-lookup"><span data-stu-id="911ca-159">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="911ca-160">若要將控制項新增至表單</span><span class="sxs-lookup"><span data-stu-id="911ca-160">To add your control to the form</span></span>

1. <span data-ttu-id="911ca-161">在 [方案總管] 中，以滑鼠右鍵按一下 [Form1.vb]，然後從捷徑功能表選擇 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="911ca-161">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="911ca-162">在 [工具箱] 中，按一下 [ValueButtonLib 元件]。</span><span class="sxs-lookup"><span data-stu-id="911ca-162">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="911ca-163">按兩下 [ValueButton]。</span><span class="sxs-lookup"><span data-stu-id="911ca-163">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="911ca-164">[ValueButton] 隨即出現在表單上。</span><span class="sxs-lookup"><span data-stu-id="911ca-164">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="911ca-165">以滑鼠右鍵按一下 [ValueButton]，然後從捷徑功能表選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="911ca-165">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="911ca-166">在 [屬性] 視窗中，檢查此控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="911ca-166">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="911ca-167">請注意，它們與標準按鈕所公開的屬性相同，不同之處是有一個額外屬性，`ButtonValue`。</span><span class="sxs-lookup"><span data-stu-id="911ca-167">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="911ca-168">將 `ButtonValue` 屬性設定為 `5`。</span><span class="sxs-lookup"><span data-stu-id="911ca-168">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="911ca-169">在 [**工具箱**] 的 [**所有 Windows Forms** ] 索引<xref:System.Windows.Forms.Label> **標籤**上, 按兩下 [Label] 將控制項新增至表單。</span><span class="sxs-lookup"><span data-stu-id="911ca-169">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="911ca-170">重新將標籤放置在表單的中央。</span><span class="sxs-lookup"><span data-stu-id="911ca-170">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="911ca-171">按兩下 `ValueButton1`。</span><span class="sxs-lookup"><span data-stu-id="911ca-171">Double-click `ValueButton1`.</span></span>

     <span data-ttu-id="911ca-172">在 [程式碼編輯器] 中開啟至 `ValueButton1_Click` 事件。</span><span class="sxs-lookup"><span data-stu-id="911ca-172">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>

9. <span data-ttu-id="911ca-173">輸入下列程式碼行。</span><span class="sxs-lookup"><span data-stu-id="911ca-173">Type the following line of code.</span></span>

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. <span data-ttu-id="911ca-174">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後從捷徑功能表選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="911ca-174">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="911ca-175">從 [偵錯] 功能表中，選取 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="911ca-175">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="911ca-176">`Form1` 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="911ca-176">`Form1` appears.</span></span>

12. <span data-ttu-id="911ca-177">按一下 `Valuebutton1`。</span><span class="sxs-lookup"><span data-stu-id="911ca-177">Click `Valuebutton1`.</span></span>

     <span data-ttu-id="911ca-178">數字 '5' 會顯示在 `Label1` 中，示範繼承的控制項之 `ButtonValue` 屬性已透過 `ValueButton1_Click` 方法傳遞至 `Label1`。</span><span class="sxs-lookup"><span data-stu-id="911ca-178">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="911ca-179">因此，`ValueButton` 控制項會繼承標準 Windows Forms 按鈕的所有功能，但是會公開額外的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="911ca-179">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="911ca-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="911ca-180">See also</span></span>

- [<span data-ttu-id="911ca-181">逐步解說：使用 Visual Basic 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="911ca-181">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- <span data-ttu-id="911ca-182">[如何：在 [選擇工具箱專案] 對話方塊中顯示控制項](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="911ca-182">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>
- [<span data-ttu-id="911ca-183">使用 .NET Framework 開發自訂的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="911ca-183">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="911ca-184">繼承基本概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="911ca-184">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
