---
title: 作法：撰寫複合控制項
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 08cb07ceebf08b3096415f9b7370e2d955152cb6
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015927"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="8937c-102">作法：撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="8937c-102">How to: Author composite controls</span></span>

<span data-ttu-id="8937c-103">複合控制項的運用方式有許多種。</span><span class="sxs-lookup"><span data-stu-id="8937c-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="8937c-104">您可以將它們撰寫成 Windows 桌面應用程式專案的一部分，且只在專案中的表單上使用它們。</span><span class="sxs-lookup"><span data-stu-id="8937c-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="8937c-105">或者，您可以在 Windows 控制項程式庫專案中撰寫它們、將專案編譯成組件，然後在其他專案中使用控制項。</span><span class="sxs-lookup"><span data-stu-id="8937c-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="8937c-106">您甚至可以從它們繼承, 並使用視覺繼承來快速地自訂它們以進行特殊用途。</span><span class="sxs-lookup"><span data-stu-id="8937c-106">You can even inherit from them and use visual inheritance to customize them quickly for special purposes.</span></span>

## <a name="to-author-a-composite-control"></a><span data-ttu-id="8937c-107">撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="8937c-107">To author a composite control</span></span>

1. <span data-ttu-id="8937c-108">在 Visual Studio 中, 建立新的**Windows 應用程式**專案, 並將其命名為**DemoControlHost**。</span><span class="sxs-lookup"><span data-stu-id="8937c-108">In Visual Studio, create a new **Windows Application** project, and name it **DemoControlHost**.</span></span>

2. <span data-ttu-id="8937c-109">在 [專案] 功能表上，按一下 [加入使用者控制項]。</span><span class="sxs-lookup"><span data-stu-id="8937c-109">On the **Project** menu, click **Add User Control**.</span></span>

3. <span data-ttu-id="8937c-110">在 [新增項目] 對話方塊中，為類別檔案 (.vb 或 .cs 檔案) 指定您希望複合控制項擁有的名稱。</span><span class="sxs-lookup"><span data-stu-id="8937c-110">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>

4. <span data-ttu-id="8937c-111">選取 [**新增**] 按鈕, 以建立複合控制項的類別檔案。</span><span class="sxs-lookup"><span data-stu-id="8937c-111">Select the **Add** button to create the class file for the composite control.</span></span>

5. <span data-ttu-id="8937c-112">將控制項從 [工具箱] 新增至複合控制項介面。</span><span class="sxs-lookup"><span data-stu-id="8937c-112">Add controls from the **Toolbox** to the composite control surface.</span></span>

6. <span data-ttu-id="8937c-113">將程式碼放在事件程序中，以處理複合控制項或其組成控制項所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="8937c-113">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>

7. <span data-ttu-id="8937c-114">關閉複合控制項的設計工具，並在系統提示時儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="8937c-114">Close the designer for the composite control, and save the file when you are prompted.</span></span>

8. <span data-ttu-id="8937c-115">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="8937c-115">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="8937c-116">必須建置專案，以便自訂要顯示於 [工具箱] 的控制項。</span><span class="sxs-lookup"><span data-stu-id="8937c-116">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>

9. <span data-ttu-id="8937c-117">使用 [工具箱] 的 [DemoControlHost] 索引標籤，將控制項的執行個體新增至 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="8937c-117">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>

## <a name="to-author-a-control-class-library"></a><span data-ttu-id="8937c-118">撰寫控制項類別庫</span><span class="sxs-lookup"><span data-stu-id="8937c-118">To author a control class library</span></span>

1. <span data-ttu-id="8937c-119">開啟新的 [Windows 控制項程式庫] 專案。</span><span class="sxs-lookup"><span data-stu-id="8937c-119">Open a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="8937c-120">根據預設，專案會包含複合控制項。</span><span class="sxs-lookup"><span data-stu-id="8937c-120">By default, the project contains a composite control.</span></span>

2. <span data-ttu-id="8937c-121">如上述程序所述，新增控制項和程式碼。</span><span class="sxs-lookup"><span data-stu-id="8937c-121">Add controls and code as described in the procedure above.</span></span>

3. <span data-ttu-id="8937c-122">選擇您不希望繼承類別變更的控制項，並將此控制項的 [修飾詞] 屬性設定為 [私人]。</span><span class="sxs-lookup"><span data-stu-id="8937c-122">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>

4. <span data-ttu-id="8937c-123">建置 DLL。</span><span class="sxs-lookup"><span data-stu-id="8937c-123">Build the DLL.</span></span>

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="8937c-124">繼承自控制項類別庫中的複合控制項</span><span class="sxs-lookup"><span data-stu-id="8937c-124">To inherit from a composite control in a control class library</span></span>

1. <span data-ttu-id="8937c-125">在 [檔案] 功能表上，指向 [新增]，然後選取 [新增專案]，以將新的 [Windows 應用程式] 專案新增至方案。</span><span class="sxs-lookup"><span data-stu-id="8937c-125">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>

2. <span data-ttu-id="8937c-126">在 [方案總管] 中，以滑鼠右鍵按一下新專案的 [參考] 資料夾，然後選擇 [新增參考] 以開啟 [新增參考] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="8937c-126">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

3. <span data-ttu-id="8937c-127">選取 [專案] 索引標籤並連按兩下您的控制項程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="8937c-127">Select the **Projects** tab and double-click your control library project.</span></span>

4. <span data-ttu-id="8937c-128">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="8937c-128">On the **Build** menu, click **Build Solution**.</span></span>

5. <span data-ttu-id="8937c-129">在 [方案總管] 中，以滑鼠右鍵按一下您的控制項程式庫專案並選取捷徑功能表中的 [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="8937c-129">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>

6. <span data-ttu-id="8937c-130">從 [新增項目] 對話方塊中，選取 [繼承的使用者控制項] 範本。</span><span class="sxs-lookup"><span data-stu-id="8937c-130">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>

7. <span data-ttu-id="8937c-131">在 [繼承選取器] 對話方塊方塊中，連按兩下您想要繼承的控制項。</span><span class="sxs-lookup"><span data-stu-id="8937c-131">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>

     <span data-ttu-id="8937c-132">新的控制項會新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="8937c-132">A new control is added to your project.</span></span>

8. <span data-ttu-id="8937c-133">開啟新控制項的視覺化設計工具並新增其他組成控制項。</span><span class="sxs-lookup"><span data-stu-id="8937c-133">Open the visual designer for the new control and add additional constituent controls.</span></span>

     <span data-ttu-id="8937c-134">您可以在 DLL 中看見繼承自複合控制項的組成控制項，而且可以修改其 [修飾詞] 屬性為 [公用] 之控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="8937c-134">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="8937c-135">您無法變更其 [修飾詞] 屬性為 [私人] 之控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="8937c-135">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8937c-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8937c-136">See also</span></span>

- [<span data-ttu-id="8937c-137">逐步解說：撰寫複合控制項</span><span class="sxs-lookup"><span data-stu-id="8937c-137">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="8937c-138">逐步解說：繼承自 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="8937c-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="8937c-139">控制項類型建議</span><span class="sxs-lookup"><span data-stu-id="8937c-139">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="8937c-140">如何：Windows Forms 的作者控制項</span><span class="sxs-lookup"><span data-stu-id="8937c-140">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="8937c-141">各種自訂控制項</span><span class="sxs-lookup"><span data-stu-id="8937c-141">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
