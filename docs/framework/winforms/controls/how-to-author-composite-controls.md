---
title: 作法：撰寫複合控制項
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
ms.openlocfilehash: 7b0ee8efa62175e2ced2a810ca6dd76e8adc103b
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039887"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="3c3c0-102">作法：撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="3c3c0-102">How to: Author Composite Controls</span></span>

<span data-ttu-id="3c3c0-103">複合控制項的運用方式有許多種。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="3c3c0-104">您可以將它們撰寫成 Windows 桌面應用程式專案的一部分，且只在專案中的表單上使用它們。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="3c3c0-105">或者，您可以在 Windows 控制項程式庫專案中撰寫它們、將專案編譯成組件，然後在其他專案中使用控制項。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="3c3c0-106">您甚至可以從它們繼承, 並使用視覺繼承來快速地自訂它們以進行特殊用途。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-106">You can even inherit from them and use visual inheritance to customize them quickly for special purposes.</span></span>

> [!NOTE]
> <span data-ttu-id="3c3c0-107">如果您想要撰寫複合控制項以在 Web Forms 上使用，請參閱[開發自訂 ASP.NET 伺服器控制項](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-107">If you want to author a composite control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="to-author-a-composite-control"></a><span data-ttu-id="3c3c0-108">撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="3c3c0-108">To author a composite control</span></span>

1. <span data-ttu-id="3c3c0-109">在 Visual Studio 中, 建立名`DemoControlHost`為的新**Windows 應用程式**專案。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-109">In Visual Studio, create a new **Windows Application** project called `DemoControlHost`.</span></span>

2. <span data-ttu-id="3c3c0-110">在 [專案] 功能表上，按一下 [加入使用者控制項]。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-110">On the **Project** menu, click **Add User Control**.</span></span>

3. <span data-ttu-id="3c3c0-111">在 [新增項目] 對話方塊中，為類別檔案 (.vb 或 .cs 檔案) 指定您希望複合控制項擁有的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-111">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>

4. <span data-ttu-id="3c3c0-112">選取 [**新增**] 按鈕, 以建立複合控制項的類別檔案。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-112">Select the **Add** button to create the class file for the composite control.</span></span>

5. <span data-ttu-id="3c3c0-113">將控制項從 [工具箱] 新增至複合控制項介面。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-113">Add controls from the **Toolbox** to the composite control surface.</span></span>

6. <span data-ttu-id="3c3c0-114">將程式碼放在事件程序中，以處理複合控制項或其組成控制項所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-114">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>

7. <span data-ttu-id="3c3c0-115">關閉複合控制項的設計工具，並在系統提示時儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-115">Close the designer for the composite control, and save the file when you are prompted.</span></span>

8. <span data-ttu-id="3c3c0-116">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-116">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="3c3c0-117">必須建置專案，以便自訂要顯示於 [工具箱] 的控制項。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-117">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>

9. <span data-ttu-id="3c3c0-118">使用 [工具箱] 的 [DemoControlHost] 索引標籤，將控制項的執行個體新增至 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-118">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>

## <a name="to-author-a-control-class-library"></a><span data-ttu-id="3c3c0-119">撰寫控制項類別庫</span><span class="sxs-lookup"><span data-stu-id="3c3c0-119">To author a control class library</span></span>

1. <span data-ttu-id="3c3c0-120">開啟新的 [Windows 控制項程式庫] 專案。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-120">Open a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="3c3c0-121">根據預設，專案會包含複合控制項。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-121">By default, the project contains a composite control.</span></span>

2. <span data-ttu-id="3c3c0-122">如上述程序所述，新增控制項和程式碼。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-122">Add controls and code as described in the procedure above.</span></span>

3. <span data-ttu-id="3c3c0-123">選擇您不希望繼承類別變更的控制項，並將此控制項的 [修飾詞] 屬性設定為 [私人]。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-123">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>

4. <span data-ttu-id="3c3c0-124">建置 DLL。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-124">Build the DLL.</span></span>

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="3c3c0-125">繼承自控制項類別庫中的複合控制項</span><span class="sxs-lookup"><span data-stu-id="3c3c0-125">To inherit from a composite control in a control class library</span></span>

1. <span data-ttu-id="3c3c0-126">在 [檔案] 功能表上，指向 [新增]，然後選取 [新增專案]，以將新的 [Windows 應用程式] 專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-126">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>

2. <span data-ttu-id="3c3c0-127">在 [方案總管] 中，以滑鼠右鍵按一下新專案的 [參考] 資料夾，然後選擇 [新增參考] 以開啟 [新增參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-127">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

3. <span data-ttu-id="3c3c0-128">選取 [專案] 索引標籤並連按兩下您的控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-128">Select the **Projects** tab and double-click your control library project.</span></span>

4. <span data-ttu-id="3c3c0-129">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-129">On the **Build** menu, click **Build Solution**.</span></span>

5. <span data-ttu-id="3c3c0-130">在 [方案總管] 中，以滑鼠右鍵按一下您的控制項程式庫專案並選取捷徑功能表中的 [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-130">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>

6. <span data-ttu-id="3c3c0-131">從 [新增項目] 對話方塊中，選取 [繼承的使用者控制項] 範本。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-131">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>

7. <span data-ttu-id="3c3c0-132">在 [繼承選取器] 對話方塊方塊中，連按兩下您想要繼承的控制項。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-132">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>

     <span data-ttu-id="3c3c0-133">新的控制項會新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-133">A new control is added to your project.</span></span>

8. <span data-ttu-id="3c3c0-134">開啟新控制項的視覺化設計工具並新增其他組成控制項。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-134">Open the visual designer for the new control and add additional constituent controls.</span></span>

     <span data-ttu-id="3c3c0-135">您可以在 DLL 中看見繼承自複合控制項的組成控制項，而且可以修改其 [修飾詞] 屬性為 [公用] 之控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-135">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="3c3c0-136">您無法變更其 [修飾詞] 屬性為 [私人] 之控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="3c3c0-136">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c3c0-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c3c0-137">See also</span></span>

- [<span data-ttu-id="3c3c0-138">逐步解說：使用 Visual Basic 撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="3c3c0-138">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="3c3c0-139">逐步解說：使用視覺效果撰寫複合控制項C#</span><span class="sxs-lookup"><span data-stu-id="3c3c0-139">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="3c3c0-140">逐步解說：從具有 Visual Basic 的 Windows Forms 控制項繼承</span><span class="sxs-lookup"><span data-stu-id="3c3c0-140">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="3c3c0-141">逐步解說：使用視覺效果從 Windows Forms 控制項繼承C#</span><span class="sxs-lookup"><span data-stu-id="3c3c0-141">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="3c3c0-142">控制項類型建議</span><span class="sxs-lookup"><span data-stu-id="3c3c0-142">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="3c3c0-143">如何：Windows Forms 的作者控制項</span><span class="sxs-lookup"><span data-stu-id="3c3c0-143">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="3c3c0-144">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="3c3c0-144">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
