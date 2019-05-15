---
title: 作法：確認子資料表中選取的資料列保持在正確位置
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
ms.openlocfilehash: 1047958a5600d8e6ee0ba461305e09395151ab14
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592281"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a><span data-ttu-id="73d91-102">作法：確認子資料表中選取的資料列保持在正確位置</span><span class="sxs-lookup"><span data-stu-id="73d91-102">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>
<span data-ttu-id="73d91-103">有時候當您使用 Windows Form 中的資料繫結時，您會在所謂父/子或主要/詳細資料檢視中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="73d91-103">Oftentimes when you work with data binding in Windows Forms, you will display data in what is called a parent/child or master/details view.</span></span> <span data-ttu-id="73d91-104">這是指來自相同來源的資料顯示在兩個控制項中的資料繫結案例。</span><span class="sxs-lookup"><span data-stu-id="73d91-104">This refers to a data-binding scenario where data from the same source is displayed in two controls.</span></span> <span data-ttu-id="73d91-105">在一個控制項中變更選取範圍會造成第二個控制項中顯示的資料也變更。</span><span class="sxs-lookup"><span data-stu-id="73d91-105">Changing the selection in one control causes the data displayed in the second control to change.</span></span> <span data-ttu-id="73d91-106">比方說，第一個控制項可能包含客戶清單，而第二個控制項包含與第一個控制項中所選取客戶相關的訂單清單。</span><span class="sxs-lookup"><span data-stu-id="73d91-106">For example, the first control might contain a list of customers and the second a list of orders related to the selected customer in the first control.</span></span>  
  
 <span data-ttu-id="73d91-107">從 .NET Framework 2.0 版開始，當您在父/子檢視中顯示資料時，您可能必須採取額外的步驟，以確定子資料表中目前選取的資料列不會重設為資料表的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="73d91-107">Starting with the .NET Framework version 2.0, when you display data in a parent/child view you might have to take extra steps to make sure that the currently selected row in the child table is not reset to the first row of the table.</span></span> <span data-ttu-id="73d91-108">若要這樣做，您必須快取子系資料表位置並在父資料表變更之後重設它。</span><span class="sxs-lookup"><span data-stu-id="73d91-108">In order to do this, you will have to cache the child table position and reset it after the parent table changes.</span></span> <span data-ttu-id="73d91-109">重設子系通常會發生在父資料表的資料列欄位第一次變更時。</span><span class="sxs-lookup"><span data-stu-id="73d91-109">Typically the child reset occurs the first time a field in a row of the parent table changes.</span></span>  
  
### <a name="to-cache-the-current-child-position"></a><span data-ttu-id="73d91-110">快取目前的子系位置</span><span class="sxs-lookup"><span data-stu-id="73d91-110">To Cache the Current Child Position</span></span>  
  
1. <span data-ttu-id="73d91-111">宣告整數變數來儲存子系清單位置，並宣告布林值變數來儲存是否要快取子系位置。</span><span class="sxs-lookup"><span data-stu-id="73d91-111">Declare an integer variable to store the child list position and a Boolean variable to store whether to cache the child position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2. <span data-ttu-id="73d91-112">處理繫結 <xref:System.Windows.Forms.CurrencyManager> 的 <xref:System.Windows.Forms.CurrencyManager.ListChanged> 事件，並檢查 <xref:System.ComponentModel.ListChangedType.Reset> 的 <xref:System.ComponentModel.ListChangedType>。</span><span class="sxs-lookup"><span data-stu-id="73d91-112">Handle the <xref:System.Windows.Forms.CurrencyManager.ListChanged> event for the binding's <xref:System.Windows.Forms.CurrencyManager> and check for a <xref:System.ComponentModel.ListChangedType> of <xref:System.ComponentModel.ListChangedType.Reset>.</span></span>  
  
3. <span data-ttu-id="73d91-113">檢查 <xref:System.Windows.Forms.CurrencyManager> 的目前位置。</span><span class="sxs-lookup"><span data-stu-id="73d91-113">Check the current position of the <xref:System.Windows.Forms.CurrencyManager>.</span></span> <span data-ttu-id="73d91-114">如果大於清單中的第一個項目 (通常為 0)，將它儲存到變數。</span><span class="sxs-lookup"><span data-stu-id="73d91-114">If it is greater than first entry in the list (typically 0), save it to a variable.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="73d91-115">處理父貨幣管理員的父清單 <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="73d91-115">Handle the parent list's <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> event for the parent currency manager.</span></span> <span data-ttu-id="73d91-116">在處理常式中，設定布林值以表示不是快取案例。</span><span class="sxs-lookup"><span data-stu-id="73d91-116">In the handler, set the Boolean value to indicate it is not a caching scenario.</span></span> <span data-ttu-id="73d91-117">如果發生 <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged>，父系的變更是清單位置變更，而不是項目值變更。</span><span class="sxs-lookup"><span data-stu-id="73d91-117">If the <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> occurs, the change to the parent is a list position change and not an item value change.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a><span data-ttu-id="73d91-118">重設子系位置</span><span class="sxs-lookup"><span data-stu-id="73d91-118">To Reset the Child Position</span></span>  
  
1. <span data-ttu-id="73d91-119">處理子系繫結的 <xref:System.Windows.Forms.CurrencyManager> 的 <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> 事件。</span><span class="sxs-lookup"><span data-stu-id="73d91-119">Handle the <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> event for the child binding's <xref:System.Windows.Forms.CurrencyManager>.</span></span>  
  
2. <span data-ttu-id="73d91-120">將子資料表位置重設為儲存在先前程序中的快取位置。</span><span class="sxs-lookup"><span data-stu-id="73d91-120">Reset the child table position to the cached position saved in the previous procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="73d91-121">範例</span><span class="sxs-lookup"><span data-stu-id="73d91-121">Example</span></span>  
 <span data-ttu-id="73d91-122">下列範例示範如何儲存子資料表在 <xref:System.Windows.Forms.CurrencyManager> 上的目前位置，並在父資料表上編輯完成之後重設位置。</span><span class="sxs-lookup"><span data-stu-id="73d91-122">The following example demonstrates how to save the current position on the <xref:System.Windows.Forms.CurrencyManager>.for a child table and reset the position after an edit is completed on the parent table.</span></span> <span data-ttu-id="73d91-123">此範例包含兩個 <xref:System.Windows.Forms.DataGridView> 控制項，它們已使用 <xref:System.Windows.Forms.BindingSource> 元件繫結至 <xref:System.Data.DataSet> 中的兩個資料表。</span><span class="sxs-lookup"><span data-stu-id="73d91-123">This example contains two <xref:System.Windows.Forms.DataGridView> controls bound to two tables in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="73d91-124">兩個資料表之間會建立關聯性，而關聯性則加入至 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="73d91-124">A relation is established between the two tables and the relation is added to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="73d91-125">子資料表中的位置一開始會設為第三個資料列，以做為示範之用。</span><span class="sxs-lookup"><span data-stu-id="73d91-125">The position in the child table is initially set to the third row for demonstration purposes.</span></span>  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 <span data-ttu-id="73d91-126">若要測試程式碼範例，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="73d91-126">To test the code example, perform the following steps:</span></span>  
  
1. <span data-ttu-id="73d91-127">執行範例。</span><span class="sxs-lookup"><span data-stu-id="73d91-127">Run the example.</span></span>  
  
2. <span data-ttu-id="73d91-128">確定已選取 [快取和重設位置] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="73d91-128">Make sure the **Cache and reset position** check box is selected.</span></span>  
  
3. <span data-ttu-id="73d91-129">按一下 [清除父欄位] 按鈕，使父資料表的欄位變更。</span><span class="sxs-lookup"><span data-stu-id="73d91-129">Click the **Clear parent field** button to cause a change in a field of the parent table.</span></span> <span data-ttu-id="73d91-130">請注意，子資料表中的選取資料列不會變更。</span><span class="sxs-lookup"><span data-stu-id="73d91-130">Notice that the selected row in the child table does not change.</span></span>  
  
4. <span data-ttu-id="73d91-131">關閉並重新執行此範例。</span><span class="sxs-lookup"><span data-stu-id="73d91-131">Close and run the example again.</span></span> <span data-ttu-id="73d91-132">您要執行這項操作，因為重設行為只會在父資料列中的第一次變更時發生。</span><span class="sxs-lookup"><span data-stu-id="73d91-132">You need to do this because the reset behavior occurs only on the first change in the parent row.</span></span>  
  
5. <span data-ttu-id="73d91-133">清除 [快取和重設位置] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="73d91-133">Clear the **Cache and reset position** check box.</span></span>  
  
6. <span data-ttu-id="73d91-134">按一下 [清除父欄位] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="73d91-134">Click the **Clear parent field** button.</span></span> <span data-ttu-id="73d91-135">請注意，子資料表中的選取資料列會變更為第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="73d91-135">Notice that the selected row in the child table changes to the first row.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73d91-136">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="73d91-136">Compiling the Code</span></span>  
 <span data-ttu-id="73d91-137">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="73d91-137">This example requires:</span></span>  
  
- <span data-ttu-id="73d91-138">System、System.Data、System.Drawing、System.Windows.Forms 和 System.XML 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="73d91-138">References to the System, System.Data, System.Drawing, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73d91-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73d91-139">See also</span></span>

- [<span data-ttu-id="73d91-140">如何：請確定多個控制項繫結至相同的資料來源都能保持同步</span><span class="sxs-lookup"><span data-stu-id="73d91-140">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)
- [<span data-ttu-id="73d91-141">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="73d91-141">BindingSource Component</span></span>](./controls/bindingsource-component.md)
- [<span data-ttu-id="73d91-142">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73d91-142">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
