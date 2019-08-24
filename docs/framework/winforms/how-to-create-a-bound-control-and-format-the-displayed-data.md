---
title: HOW TO：建立繫結控制項並格式化顯示的資料
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 543775894994c518d6069f697b145cedaa7af5b0
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015654"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="286e3-102">作法：建立繫結控制項並格式化顯示的資料</span><span class="sxs-lookup"><span data-stu-id="286e3-102">How to: Create a Bound Control and Format the Displayed Data</span></span>

<span data-ttu-id="286e3-103">藉由 Windows Forms 資料系結, 您可以使用 [**格式化] 和 [高級**系結] 對話方塊來格式化資料繫結控制項中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="286e3-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>

## <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="286e3-104">繫結控制項並格式化顯示的資料</span><span class="sxs-lookup"><span data-stu-id="286e3-104">To bind a control and format the displayed data</span></span>

1. <span data-ttu-id="286e3-105">連接至資料來源。</span><span class="sxs-lookup"><span data-stu-id="286e3-105">Connect to a data source.</span></span> <span data-ttu-id="286e3-106">如需詳細資訊, 請參閱[連接到資料來源](../data/adonet/connecting-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="286e3-106">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="286e3-107">在 Visual Studio 中, 選取表單上的控制項, 然後開啟 **屬性** 視窗。</span><span class="sxs-lookup"><span data-stu-id="286e3-107">In Visual Studio, select the control on the form, and then open the **Properties** window.</span></span>

3. <span data-ttu-id="286e3-108">展開 [ **(** 系結)] 屬性, 然後在 [ **(Advanced)** ] 方塊中, 按一下省略號![按鈕 (Visual Studio](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)的屬性視窗中的省略號按鈕 (...), 以顯示**格式設定和 [高級]** [系結] 對話方塊, 其中包含該控制項的完整屬性清單。</span><span class="sxs-lookup"><span data-stu-id="286e3-108">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>

4. <span data-ttu-id="286e3-109">選取您想要系結的屬性, 然後選取 [系結] 箭號。</span><span class="sxs-lookup"><span data-stu-id="286e3-109">Select the property you want to bind, and then select the **Binding** arrow.</span></span>

     <span data-ttu-id="286e3-110">會顯示可用資料來源清單。</span><span class="sxs-lookup"><span data-stu-id="286e3-110">A list of available data sources is displayed.</span></span>

5. <span data-ttu-id="286e3-111">展開您想要繫結的資料來源，直到您找到您要的單一資料項目。</span><span class="sxs-lookup"><span data-stu-id="286e3-111">Expand the data source you want to bind to until you find the single data element you want.</span></span>

     <span data-ttu-id="286e3-112">例如，如果您要在資料集資料表中繫結資料行值，展開資料集的名稱，然後展開資料表名稱來顯示資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="286e3-112">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

6. <span data-ttu-id="286e3-113">選取要系結之元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="286e3-113">Select the name of an element to bind to.</span></span>

7. <span data-ttu-id="286e3-114">在 [**格式類型**] 方塊中, 選取您想要套用至控制項中所顯示之資料的格式。</span><span class="sxs-lookup"><span data-stu-id="286e3-114">In the **Format type** box, select the format you want to apply to the data displayed in the control.</span></span>

     <span data-ttu-id="286e3-115">在所有情況下，如果資料來源包含 <xref:System.DBNull>，則您可以指定顯示在控制項中的值。</span><span class="sxs-lookup"><span data-stu-id="286e3-115">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="286e3-116">否則，選項會稍微不同，視您所選擇的格式類型而定。</span><span class="sxs-lookup"><span data-stu-id="286e3-116">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="286e3-117">下列表格顯示格式類型和選項。</span><span class="sxs-lookup"><span data-stu-id="286e3-117">The following table shows the format types and options.</span></span>

    |<span data-ttu-id="286e3-118">格式類型</span><span class="sxs-lookup"><span data-stu-id="286e3-118">Format type</span></span>|<span data-ttu-id="286e3-119">格式化選項</span><span class="sxs-lookup"><span data-stu-id="286e3-119">Formatting option</span></span>|
    |-----------------|-----------------------|
    |<span data-ttu-id="286e3-120">沒有格式化</span><span class="sxs-lookup"><span data-stu-id="286e3-120">No Formatting</span></span>|<span data-ttu-id="286e3-121">沒有選項。</span><span class="sxs-lookup"><span data-stu-id="286e3-121">No options.</span></span>|
    |<span data-ttu-id="286e3-122">數值</span><span class="sxs-lookup"><span data-stu-id="286e3-122">Numeric</span></span>|<span data-ttu-id="286e3-123">使用 [**小**數位數] 上下按鈕控制項來指定小數點位數。</span><span class="sxs-lookup"><span data-stu-id="286e3-123">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="286e3-124">貨幣</span><span class="sxs-lookup"><span data-stu-id="286e3-124">Currency</span></span>|<span data-ttu-id="286e3-125">使用 [**小**數位數] 上下按鈕控制項來指定小數點位數。</span><span class="sxs-lookup"><span data-stu-id="286e3-125">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="286e3-126">日期時間</span><span class="sxs-lookup"><span data-stu-id="286e3-126">Date Time</span></span>|<span data-ttu-id="286e3-127">選取 [**類型**] 選取方塊中的其中一個專案, 以選取應如何顯示日期和時間。</span><span class="sxs-lookup"><span data-stu-id="286e3-127">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|
    |<span data-ttu-id="286e3-128">科學記號</span><span class="sxs-lookup"><span data-stu-id="286e3-128">Scientific</span></span>|<span data-ttu-id="286e3-129">使用 [**小**數位數] 上下按鈕控制項來指定小數點位數。</span><span class="sxs-lookup"><span data-stu-id="286e3-129">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="286e3-130">自訂</span><span class="sxs-lookup"><span data-stu-id="286e3-130">Custom</span></span>|<span data-ttu-id="286e3-131">指定使用自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="286e3-131">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="286e3-132">如需詳細資訊，請參閱[格式類型](../../standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="286e3-132">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="286e3-133">**注意：** 自訂格式字串不保證能成功地在資料來源和繫結的控制項之間反覆存取。</span><span class="sxs-lookup"><span data-stu-id="286e3-133">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="286e3-134">改為處理 <xref:System.Windows.Forms.Binding.Parse> 或 <xref:System.Windows.Forms.Binding.Format> 繫結的事件，以及在事件處理程式碼中套用自訂格式。</span><span class="sxs-lookup"><span data-stu-id="286e3-134">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|

8. <span data-ttu-id="286e3-135">選取 **[確定]** 關閉 [**格式化和高級**系結] 對話方塊, 並返回屬性視窗。</span><span class="sxs-lookup"><span data-stu-id="286e3-135">Select **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>

## <a name="see-also"></a><span data-ttu-id="286e3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="286e3-136">See also</span></span>

- [<span data-ttu-id="286e3-137">如何：在 Windows Form 上建立簡單繫結控制項</span><span class="sxs-lookup"><span data-stu-id="286e3-137">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="286e3-138">Windows Forms 中的使用者輸入驗證</span><span class="sxs-lookup"><span data-stu-id="286e3-138">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="286e3-139">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="286e3-139">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
