---
title: "如何：建立繫結控制項並格式化顯示的資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6088048ed27b2021e297494275f4e80f7c0cb681
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="890c9-102">如何：建立繫結控制項並格式化顯示的資料</span><span class="sxs-lookup"><span data-stu-id="890c9-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="890c9-103">Windows Form 資料繫結，您可以將資料格式化顯示的資料繫結控制項中使用**格式化和進階繫結** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="890c9-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="890c9-104">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="890c9-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="890c9-105">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="890c9-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="890c9-106">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="890c9-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="890c9-107">繫結控制項並格式化顯示的資料</span><span class="sxs-lookup"><span data-stu-id="890c9-107">To bind a control and format the displayed data</span></span>  
  
1.  <span data-ttu-id="890c9-108">連接至資料來源。</span><span class="sxs-lookup"><span data-stu-id="890c9-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="890c9-109">如需詳細資訊，請參閱[連接到資料來源](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)。</span><span class="sxs-lookup"><span data-stu-id="890c9-109">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="890c9-110">在表單中選取控制項，然後開啟屬性視窗。</span><span class="sxs-lookup"><span data-stu-id="890c9-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3.  <span data-ttu-id="890c9-111">展開**(DataBindings)**屬性，然後在**（進階）**方塊中，按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 以顯示**格式化與進階繫結**對話方塊中，具有該控制項屬性的完整清單。</span><span class="sxs-lookup"><span data-stu-id="890c9-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4.  <span data-ttu-id="890c9-112">選取您想要繫結，然後按一下的屬性**繫結**箭號。</span><span class="sxs-lookup"><span data-stu-id="890c9-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="890c9-113">會顯示可用資料來源清單。</span><span class="sxs-lookup"><span data-stu-id="890c9-113">A list of available data sources is displayed.</span></span>  
  
5.  <span data-ttu-id="890c9-114">展開您想要繫結的資料來源，直到您找到您要的單一資料項目。</span><span class="sxs-lookup"><span data-stu-id="890c9-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="890c9-115">例如，如果您要在資料集資料表中繫結資料行值，展開資料集的名稱，然後展開資料表名稱來顯示資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="890c9-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6.  <span data-ttu-id="890c9-116">按一下要繫結項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="890c9-116">Click the name of an element to bind to.</span></span>  
  
7.  <span data-ttu-id="890c9-117">在**格式化類型**方塊中，按一下您想要套用到控制項中顯示資料的格式。</span><span class="sxs-lookup"><span data-stu-id="890c9-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="890c9-118">在所有情況下，如果資料來源包含 <xref:System.DBNull>，則您可以指定顯示在控制項中的值。</span><span class="sxs-lookup"><span data-stu-id="890c9-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="890c9-119">否則，選項會稍微不同，視您所選擇的格式類型而定。</span><span class="sxs-lookup"><span data-stu-id="890c9-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="890c9-120">下列表格顯示格式類型和選項。</span><span class="sxs-lookup"><span data-stu-id="890c9-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="890c9-121">格式類型</span><span class="sxs-lookup"><span data-stu-id="890c9-121">Format type</span></span>|<span data-ttu-id="890c9-122">格式化選項</span><span class="sxs-lookup"><span data-stu-id="890c9-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="890c9-123">沒有格式化</span><span class="sxs-lookup"><span data-stu-id="890c9-123">No Formatting</span></span>|<span data-ttu-id="890c9-124">沒有選項。</span><span class="sxs-lookup"><span data-stu-id="890c9-124">No options.</span></span>|  
    |<span data-ttu-id="890c9-125">數值</span><span class="sxs-lookup"><span data-stu-id="890c9-125">Numeric</span></span>|<span data-ttu-id="890c9-126">使用指定的小數位數**小數位數**上下按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="890c9-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="890c9-127">貨幣</span><span class="sxs-lookup"><span data-stu-id="890c9-127">Currency</span></span>|<span data-ttu-id="890c9-128">使用指定的小數位數**小數位數**上下按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="890c9-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="890c9-129">日期時間</span><span class="sxs-lookup"><span data-stu-id="890c9-129">Date Time</span></span>|<span data-ttu-id="890c9-130">選取如何藉由選取其中一個項目中顯示的日期和時間**類型**選取方塊。</span><span class="sxs-lookup"><span data-stu-id="890c9-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="890c9-131">科學記號</span><span class="sxs-lookup"><span data-stu-id="890c9-131">Scientific</span></span>|<span data-ttu-id="890c9-132">使用指定的小數位數**小數位數**上下按鈕控制項。</span><span class="sxs-lookup"><span data-stu-id="890c9-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="890c9-133">自訂</span><span class="sxs-lookup"><span data-stu-id="890c9-133">Custom</span></span>|<span data-ttu-id="890c9-134">指定使用自訂格式字串。</span><span class="sxs-lookup"><span data-stu-id="890c9-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="890c9-135">如需詳細資訊，請參閱[格式化型別](../../../docs/standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="890c9-135">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="890c9-136">**注意：**自訂格式字串來成功反覆存取資料來源和繫結的控制項之間不保證。</span><span class="sxs-lookup"><span data-stu-id="890c9-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="890c9-137">改為處理 <xref:System.Windows.Forms.Binding.Parse> 或 <xref:System.Windows.Forms.Binding.Format> 繫結的事件，以及在事件處理程式碼中套用自訂格式。</span><span class="sxs-lookup"><span data-stu-id="890c9-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8.  <span data-ttu-id="890c9-138">按一下**確定**關閉**格式化與進階繫結**對話方塊並返回 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="890c9-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="890c9-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="890c9-139">See Also</span></span>  
 [<span data-ttu-id="890c9-140">操作說明：在 Windows Forms 上建立簡單繫結控制項</span><span class="sxs-lookup"><span data-stu-id="890c9-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [<span data-ttu-id="890c9-141">Windows Forms 中的使用者輸入驗證</span><span class="sxs-lookup"><span data-stu-id="890c9-141">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [<span data-ttu-id="890c9-142">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="890c9-142">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
