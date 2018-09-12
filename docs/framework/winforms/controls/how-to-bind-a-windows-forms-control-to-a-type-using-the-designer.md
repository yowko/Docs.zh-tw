---
title: 如何：使用設計工具將 Windows Forms 控制項繫結至型別
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 33df9e050dd8c2b3ace8ff89cbd5939b538fcd95
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44098338"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a><span data-ttu-id="29980-102">如何：使用設計工具將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="29980-102">How to: Bind a Windows Forms Control to a Type Using the Designer</span></span>
<span data-ttu-id="29980-103">當您在建立與資料互動的控制項時，有時需要將控制項繫結至類型，而非物件。</span><span class="sxs-lookup"><span data-stu-id="29980-103">When you are building controls that interact with data, you sometimes need to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="29980-104">您在設計階段通常需要將控制項繫結至類型，當時資料可能無法使用，但您仍希望資料繫結的控制項顯示類型公用介面中的資料。</span><span class="sxs-lookup"><span data-stu-id="29980-104">You typically need to bind a control to a type at design time, when data may not be available, but you still want your data-bound controls to display data from a type's public interface.</span></span> <span data-ttu-id="29980-105">下列程序示範如何建立新<xref:System.Windows.Forms.BindingSource>也就是繫結至型別，以及如何將其中一個類型的屬性，以繫結<xref:System.Windows.Forms.TextBox.Text%2A>屬性<xref:System.Windows.Forms.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="29980-105">The following procedures demonstrate how to create a new <xref:System.Windows.Forms.BindingSource> that is bound to a type, and then how to bind one of the type's properties to the <xref:System.Windows.Forms.TextBox.Text%2A> property of a <xref:System.Windows.Forms.TextBox>.</span></span>  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a><span data-ttu-id="29980-106">將 BindingSource 繫結至類型</span><span class="sxs-lookup"><span data-stu-id="29980-106">To bind the BindingSource to a type</span></span>  
  
1.  <span data-ttu-id="29980-107">建立 Windows Forms 專案 (**檔案** > **新增** > **專案** > **Visual C#** 或**Visual Basic** > **傳統桌面** > **Windows Forms 應用程式**)。</span><span class="sxs-lookup"><span data-stu-id="29980-107">Create a Windows Forms project (**File** > **New** > **Project** > **Visual C#** or **Visual Basic** > **Classic Desktop** > **Windows Forms Application**).</span></span>  
  
2.  <span data-ttu-id="29980-108">在 **設計**檢視中，將<xref:System.Windows.Forms.BindingSource>元件拖曳至表單。</span><span class="sxs-lookup"><span data-stu-id="29980-108">In **Design** view, drag a <xref:System.Windows.Forms.BindingSource> component onto the form.</span></span>  
  
3.  <span data-ttu-id="29980-109">在 [**屬性**] 視窗中，按一下箭號<xref:System.Windows.Forms.BindingSource.DataSource%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="29980-109">In the **Properties** window, click the arrow for the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property.</span></span>  
  
4.  <span data-ttu-id="29980-110">在 [DataSource UI 類型編輯器] 中，按一下 [新增專案資料來源]。</span><span class="sxs-lookup"><span data-stu-id="29980-110">In the **DataSource UI Type Editor**, click **Add Project Data Source**.</span></span>  
  
5.  <span data-ttu-id="29980-111">在 [選擇資料來源類型] 頁面中，選取 [物件]，再按 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="29980-111">On the **Choose a Data Source Type** page, select **Object** and click **Next**.</span></span>  
  
6.  <span data-ttu-id="29980-112">選取要繫結的類型︰</span><span class="sxs-lookup"><span data-stu-id="29980-112">Select the type to bind to:</span></span>  
  
    -   <span data-ttu-id="29980-113">如果您想要繫結的類型是在目前專案中，或包含此類型的組件已新增為參考，請展開節點以找出您想要的類型，然後選取它。</span><span class="sxs-lookup"><span data-stu-id="29980-113">If the type you want to bind to is in the current project, or the assembly that contains the type is already added as a reference, expand the nodes to find the type you want, and then select it.</span></span>  
  
         <span data-ttu-id="29980-114">-或-</span><span class="sxs-lookup"><span data-stu-id="29980-114">-or-</span></span>  
  
    -   <span data-ttu-id="29980-115">如果您想要繫結的類型是在另一個組件中，目前不在參考清單中，請按一下 [新增參考]，然後按一下 [專案] 索引標籤。選取包含您想要之商務物件的專案，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="29980-115">If the type you want to bind to is in another assembly, not currently in the list of references, click **Add Reference**, and then click the **Projects** tab. Select the project that contains the business object you want and click **OK**.</span></span> <span data-ttu-id="29980-116">此專案會出現在組件清單中，所以您可展開節點以找出您想要的類型，然後選取它。</span><span class="sxs-lookup"><span data-stu-id="29980-116">This project will appear in the list of assemblies, so you can expand the nodes to find the type you want, and then select it.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="29980-117">如果您想要繫結至架構或 Microsoft 組件中的類型，請清除 [隱藏以 Microsoft 或 System 開頭的組件] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="29980-117">If you want to bind to a type in a framework or Microsoft assembly, clear the **Hide assemblies that begin with Microsoft or System** check box.</span></span>  
  
7.  <span data-ttu-id="29980-118">按 [下一步] ，然後按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="29980-118">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a><span data-ttu-id="29980-119">將控制項繫結至 BindingSource</span><span class="sxs-lookup"><span data-stu-id="29980-119">To bind the control to the BindingSource</span></span>  
  
1.  <span data-ttu-id="29980-120">將 <xref:System.Windows.Forms.TextBox> 加入表單。</span><span class="sxs-lookup"><span data-stu-id="29980-120">Add a <xref:System.Windows.Forms.TextBox> to the form.</span></span>  
  
2.  <span data-ttu-id="29980-121">在 [屬性] 視窗中，展開 [(DataBindings)]  節點。</span><span class="sxs-lookup"><span data-stu-id="29980-121">In the **Properties** window, expand the **(DataBindings)** node.</span></span>  
  
3.  <span data-ttu-id="29980-122">按一下箭號旁<xref:System.Windows.Forms.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="29980-122">Click the arrow next to the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
4.  <span data-ttu-id="29980-123">在  **DataSource UI 類型編輯器**，展開的節點<xref:System.Windows.Forms.BindingSource>之前，所新增，然後選取您想要繫結的繫結類型屬性<xref:System.Windows.Forms.TextBox.Text%2A>屬性<xref:System.Windows.Forms.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="29980-123">In the **DataSource UI Type Editor**, expand the node for the <xref:System.Windows.Forms.BindingSource> added previously, and select the property of the bound type you want to bind to the <xref:System.Windows.Forms.TextBox.Text%2A> property of the <xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29980-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29980-124">See Also</span></span>  
 [<span data-ttu-id="29980-125">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="29980-125">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="29980-126">操作說明：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="29980-126">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [<span data-ttu-id="29980-127">將控制項繫結至 Visual Studio 中的資料</span><span class="sxs-lookup"><span data-stu-id="29980-127">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
