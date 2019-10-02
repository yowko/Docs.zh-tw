---
title: 作法：在 Windows Form 上建立簡單繫結控制項
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: df87f00e6e03de67c3fb1adc28472c96f4a47ef4
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015637"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="1043f-102">HOW TO：在 Windows Form 上建立簡單繫結控制項</span><span class="sxs-lookup"><span data-stu-id="1043f-102">How to: Create a simple-bound control on a Windows Form</span></span>

<span data-ttu-id="1043f-103">使用*簡單*系結, 您可以在控制項中顯示單一資料元素, 例如資料集資料表中的資料行值。</span><span class="sxs-lookup"><span data-stu-id="1043f-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="1043f-104">您可以簡單地將控制項的任何屬性系結至資料值。</span><span class="sxs-lookup"><span data-stu-id="1043f-104">You can simple-bind any property of a control to a data value.</span></span>

## <a name="to-simple-bind-a-control"></a><span data-ttu-id="1043f-105">簡單-系結控制項</span><span class="sxs-lookup"><span data-stu-id="1043f-105">To simple-bind a control</span></span>

1. <span data-ttu-id="1043f-106">連接至資料來源。</span><span class="sxs-lookup"><span data-stu-id="1043f-106">Connect to a data source.</span></span> <span data-ttu-id="1043f-107">如需詳細資訊, 請參閱[連接到資料來源](../data/adonet/connecting-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="1043f-107">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="1043f-108">在 Visual Studio 中, 選取表單上的控制項, 並顯示 [**屬性**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="1043f-108">In Visual Studio, select the control on the form and display the **Properties** window.</span></span>

3. <span data-ttu-id="1043f-109">展開 [ **(** 系結)] 屬性。</span><span class="sxs-lookup"><span data-stu-id="1043f-109">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="1043f-110">最常系結的屬性會顯示在 [(系結 **)** ] 屬性底下。</span><span class="sxs-lookup"><span data-stu-id="1043f-110">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="1043f-111">例如, 在大部分的控制項中, **Text**屬性最常系結。</span><span class="sxs-lookup"><span data-stu-id="1043f-111">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="1043f-112">如果您要系結的屬性不是其中一個常用的屬性, 請按一下 [ **(Advanced)** ] 方塊中的](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)**省略號**按鈕 (![屬性視窗中 Visual Studio 的省略號按鈕 (...), 以顯示 **[格式化] 和 [Advanced Binding** ] 對話方塊, 其中包含該控制項的完整屬性清單。</span><span class="sxs-lookup"><span data-stu-id="1043f-112">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="1043f-113">選取您想要系結的屬性, 然後按一下 [系結]底下的下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="1043f-113">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="1043f-114">會顯示可用資料來源清單。</span><span class="sxs-lookup"><span data-stu-id="1043f-114">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="1043f-115">展開您想要繫結的資料來源，直到您找到您要的單一資料項目。</span><span class="sxs-lookup"><span data-stu-id="1043f-115">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="1043f-116">例如，如果您要在資料集資料表中繫結資料行值，展開資料集的名稱，然後展開資料表名稱來顯示資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="1043f-116">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="1043f-117">按一下要繫結項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="1043f-117">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="1043f-118">如果您是在 [**格式化和 Advanced Binding** ] 對話方塊中工作, 請按一下 **[確定**] 以返回 [**屬性**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="1043f-118">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="1043f-119">如果您想要系結控制項的其他屬性, 請重複步驟3到7。</span><span class="sxs-lookup"><span data-stu-id="1043f-119">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1043f-120">由於簡單繫結控制項只會顯示單一資料元素, 因此通常會將導覽邏輯包含在具有簡單繫結控制項的 Windows Form 中。</span><span class="sxs-lookup"><span data-stu-id="1043f-120">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="1043f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1043f-121">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="1043f-122">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="1043f-122">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="1043f-123">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1043f-123">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
