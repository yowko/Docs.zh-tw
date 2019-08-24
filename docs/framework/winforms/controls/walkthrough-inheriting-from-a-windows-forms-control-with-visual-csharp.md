---
title: 逐步解說：使用 Visual C# 繼承來自 Windows Form 的控制項
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a9a4b9bc15d2579837c3f4969a8d85293f10967
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015673"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a><span data-ttu-id="0b6fd-102">逐步解說：繼承自具有 C 的 Windows Forms 控制項\#</span><span class="sxs-lookup"><span data-stu-id="0b6fd-102">Walkthrough: Inherit from a Windows Forms Control with C\#</span></span>

<span data-ttu-id="0b6fd-103">使用視覺C#效果, 您可以透過*繼承*來建立功能強大的自訂控制項。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-103">With Visual C#, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="0b6fd-104">您可以透過繼承建立控制項，不僅保留標準 Windows Forms 控制項的所有固有功能，同時也納入自訂功能。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="0b6fd-105">在本逐步解說中，您將會建立簡單的繼承控制項，名為 `ValueButton`。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="0b6fd-106">此按鈕將繼承標準 Windows Forms <xref:System.Windows.Forms.Button>控制項的功能, 並會公開名`ButtonValue`為的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="create-the-project"></a><span data-ttu-id="0b6fd-107">建立專案</span><span class="sxs-lookup"><span data-stu-id="0b6fd-107">Create the Project</span></span>

<span data-ttu-id="0b6fd-108">當您建立新的專案時，您會指定其名稱以設定根命名空間、組件名稱和專案名稱，並且確定預設元件將會在正確的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="0b6fd-109">若要建立 ValueButtonLib 控制項程式庫和 ValueButton 控制項</span><span class="sxs-lookup"><span data-stu-id="0b6fd-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="0b6fd-110">在 Visual Studio 中, 建立新的**Windows Forms 控制項程式庫**專案, 並將其命名為**ValueButtonLib**。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-110">In Visual Studio, create a new **Windows Forms Control Library** project, and name it **ValueButtonLib**.</span></span>

     <span data-ttu-id="0b6fd-111">專案名稱，`ValueButtonLib`，預設也會指派給根命名空間。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-111">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="0b6fd-112">根命名空間是用來限定組件中的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-112">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="0b6fd-113">例如，如果兩個組件提供元件，名為 `ValueButton`，您可以使用 `ValueButtonLib.ValueButton` 指定您的 `ValueButton` 元件。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-113">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="0b6fd-114">如需詳細資訊，請參閱[命名空間](../../../csharp/programming-guide/namespaces/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-114">For more information, see [Namespaces](../../../csharp/programming-guide/namespaces/index.md).</span></span>

2. <span data-ttu-id="0b6fd-115">在 [方案總管] 中，以滑鼠右鍵按一下 [UserControl1.cs]，然後從捷徑功能表選擇 [重新命名]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-115">In **Solution Explorer**, right-click **UserControl1.cs**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="0b6fd-116">將檔案名變更為**ValueButton.cs**。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-116">Change the file name to **ValueButton.cs**.</span></span> <span data-ttu-id="0b6fd-117">當系統詢問您是否要重新命名程式碼元素 '`UserControl1`' 的所有參考時，按一下 [是]按鈕。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-117">Click the **Yes** button when you are asked if you want to rename all references to the code element '`UserControl1`'.</span></span>

3. <span data-ttu-id="0b6fd-118">在 [方案總管] 中，以滑鼠右鍵按一下 [ValueButton.cs]，然後選取 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-118">In **Solution Explorer**, right-click **ValueButton.cs** and select **View Code**.</span></span>

4. <span data-ttu-id="0b6fd-119">找出`class`語句行, `public partial class ValueButton`然後將這個控制項繼承的<xref:System.Windows.Forms.UserControl>目標型別變更為<xref:System.Windows.Forms.Button>。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-119">Locate the `class` statement line, `public partial class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="0b6fd-120">這可讓您的<xref:System.Windows.Forms.Button>繼承控制項繼承控制項的所有功能。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-120">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

5. <span data-ttu-id="0b6fd-121">在 [方案總管] 中，開啟 [ValueButton.cs] 節點以顯示設計工具產生的程式碼檔案，**ValueButton.Designer.cs**。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-121">In **Solution Explorer**, open the **ValueButton.cs** node to display the designer-generated code file, **ValueButton.Designer.cs**.</span></span> <span data-ttu-id="0b6fd-122">在 [程式碼編輯器] 中開啟此檔案。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-122">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="0b6fd-123">找出`InitializeComponent`方法, 並移除<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>指派屬性的行。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-123">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="0b6fd-124">這個屬性不存在於<xref:System.Windows.Forms.Button>控制項中。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-124">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="0b6fd-125">從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-125">From the **File** menu, choose **Save All** to save the project.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0b6fd-126">視覺化設計工具再也無法使用。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-126">A visual designer is no longer available.</span></span> <span data-ttu-id="0b6fd-127"><xref:System.Windows.Forms.Button>由於控制項會進行自己的繪製, 因此您無法在設計工具中修改其外觀。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-127">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="0b6fd-128">它的視覺標記法會與繼承自的類別 (也就是<xref:System.Windows.Forms.Button>) 完全相同, 除非在程式碼中修改。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-128">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span> <span data-ttu-id="0b6fd-129">您仍然可以將元件 (其中沒有任何 UI 元素) 新增至設計介面。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-129">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="add-a-property-to-your-inherited-control"></a><span data-ttu-id="0b6fd-130">將屬性加入至繼承的控制項</span><span class="sxs-lookup"><span data-stu-id="0b6fd-130">Add a Property to Your Inherited Control</span></span>

<span data-ttu-id="0b6fd-131">繼承 Windows Forms 控制項的可能用法之一是建立外觀及操作與標準的 Windows Forms 控制項相同的控制項，但是公開自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-131">One possible use of inherited Windows Forms controls is the creation of controls that are identical in look and feel of standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="0b6fd-132">在本節中，您會將名為 `ButtonValue` 的屬性新增至您的控制項。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-132">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="0b6fd-133">若要新增 Value 屬性</span><span class="sxs-lookup"><span data-stu-id="0b6fd-133">To add the Value property</span></span>

1. <span data-ttu-id="0b6fd-134">在 [方案總管] 中，以滑鼠右鍵按一下 [ValueButton.cs]，然後從捷徑功能表按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-134">In **Solution Explorer**, right-click **ValueButton.cs**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="0b6fd-135">尋找 `class` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-135">Locate the `class` statement.</span></span> <span data-ttu-id="0b6fd-136">緊接在 `{` 後面，輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0b6fd-136">Immediately after the `{`, type the following code:</span></span>

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     <span data-ttu-id="0b6fd-137">此程式碼會設定方法，系統會使用該方法來儲存和擷取 `ButtonValue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-137">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="0b6fd-138">`get` 陳述式會將傳回值設為儲存在私用變數 `varValue` 的值，而 `set` 陳述式會使用 `value` 關鍵字設定私用變數的值。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-138">The `get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `set` statement sets the value of the private variable by use of the `value` keyword.</span></span>

3. <span data-ttu-id="0b6fd-139">從 [檔案] 功能表選擇 [全部儲存] 以儲存專案。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-139">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="test-the-control"></a><span data-ttu-id="0b6fd-140">測試控制項</span><span class="sxs-lookup"><span data-stu-id="0b6fd-140">Test the control</span></span>

<span data-ttu-id="0b6fd-141">控制項不是獨立專案；它們必須裝載在容器中。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-141">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="0b6fd-142">若要測試您的控制項，您必須提供測試專案讓控制項在其中執行。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-142">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="0b6fd-143">您也必須藉由建置 (編譯) 控制項，讓控制項可供測試專案存取。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-143">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="0b6fd-144">在本節中，您將會建置您的控制項，並且在 Windows Form 中進行測試。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-144">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="0b6fd-145">若要建置您的控制項</span><span class="sxs-lookup"><span data-stu-id="0b6fd-145">To build your control</span></span>

<span data-ttu-id="0b6fd-146">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-146">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="0b6fd-147">建置應該會成功，沒有編譯器錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-147">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="0b6fd-148">若要建立測試專案</span><span class="sxs-lookup"><span data-stu-id="0b6fd-148">To create a test project</span></span>

1. <span data-ttu-id="0b6fd-149">在 [檔案] 功能表上，指向 [新增]，然後選取 [新增專案]，以開啟 [加入新的專案]對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-149">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="0b6fd-150">選取 [Visual C#] 節點下方的 [Windows] 節點，然後按一下 [Windows Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-150">Select the **Windows** node, beneath the **Visual C#** node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="0b6fd-151">在 [**名稱**] 方塊中, 輸入**Test**。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-151">In the **Name** box, enter **Test**.</span></span>

4. <span data-ttu-id="0b6fd-152">在 [方案總管] 中，以滑鼠右鍵按一下測試專案的 [參考] 節點，然後從捷徑功能表選取 [加入參考]，以顯示 [加入參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-152">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

5. <span data-ttu-id="0b6fd-153">按一下標籤為 [專案] 的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-153">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="0b6fd-154">您的 ValueButtonLib 專案將會列在 [**專案名稱**] 底下。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-154">Your ValueButtonLib project will be listed under **Project Name**.</span></span> <span data-ttu-id="0b6fd-155">按兩下專案以將參考新增至測試專案。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-155">Double-click the project to add the reference to the test project.</span></span>

6. <span data-ttu-id="0b6fd-156">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後選取 [建置]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-156">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="0b6fd-157">若要將控制項新增至表單</span><span class="sxs-lookup"><span data-stu-id="0b6fd-157">To add your control to the form</span></span>

1. <span data-ttu-id="0b6fd-158">在 [方案總管] 中，以滑鼠右鍵按一下 [Form1.cs]，然後從捷徑功能表選擇 [檢視表設計工具]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-158">In **Solution Explorer**, right-click **Form1.cs** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="0b6fd-159">在 [**工具箱**] 中, 選取 [ **ValueButtonLib 元件**]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-159">In the **Toolbox**, select **ValueButtonLib Components**.</span></span> <span data-ttu-id="0b6fd-160">按兩下 [ValueButton]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-160">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="0b6fd-161">[ValueButton] 隨即出現在表單上。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-161">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="0b6fd-162">以滑鼠右鍵按一下 [ValueButton]，然後從捷徑功能表選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-162">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="0b6fd-163">在 [屬性] 視窗中，檢查此控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-163">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="0b6fd-164">請注意, 它們與標準按鈕所公開的屬性相同, 不同之處在于還有額外的屬性 ButtonValue。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-164">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, ButtonValue.</span></span>

5. <span data-ttu-id="0b6fd-165">將 [ **ButtonValue** ] 屬性設定為 [ **5**]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-165">Set the **ButtonValue** property to **5**.</span></span>

6. <span data-ttu-id="0b6fd-166">在 [**工具箱**] 的 [**所有 Windows Forms** ] 索引<xref:System.Windows.Forms.Label> **標籤**中, 按兩下 [Label] 將控制項新增至表單。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-166">In the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="0b6fd-167">重新將標籤放置在表單的中央。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-167">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="0b6fd-168">按兩下 `valueButton1`。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-168">Double-click `valueButton1`.</span></span>

     <span data-ttu-id="0b6fd-169">在 [程式碼編輯器] 中開啟至 `valueButton1_Click` 事件。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-169">The **Code Editor** opens to the `valueButton1_Click` event.</span></span>

9. <span data-ttu-id="0b6fd-170">插入下列程式碼行。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-170">Insert the following line of code.</span></span>

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. <span data-ttu-id="0b6fd-171">在 [方案總管] 中，以滑鼠右鍵按一下 [測試]，然後從捷徑功能表選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-171">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="0b6fd-172">從 [偵錯] 功能表中，選取 [開始偵錯]。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-172">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="0b6fd-173">`Form1` 隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-173">`Form1` appears.</span></span>

12. <span data-ttu-id="0b6fd-174">按一下 `valueButton1`。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-174">Click `valueButton1`.</span></span>

     <span data-ttu-id="0b6fd-175">數字 '5' 會顯示在 `label1` 中，示範繼承的控制項之 `ButtonValue` 屬性已透過 `valueButton1_Click` 方法傳遞至 `label1`。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-175">The numeral '5' is displayed in `label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `label1` through the `valueButton1_Click` method.</span></span> <span data-ttu-id="0b6fd-176">因此，`ValueButton` 控制項會繼承標準 Windows Forms 按鈕的所有功能，但是會公開額外的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="0b6fd-176">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b6fd-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b6fd-177">See also</span></span>

- <span data-ttu-id="0b6fd-178">[如何：在 [選擇工具箱專案] 對話方塊中顯示控制項](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="0b6fd-178">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>
- [<span data-ttu-id="0b6fd-179">逐步解說：使用視覺效果撰寫複合控制項C#</span><span class="sxs-lookup"><span data-stu-id="0b6fd-179">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
