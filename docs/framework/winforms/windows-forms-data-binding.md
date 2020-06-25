---
title: 資料繫結
description: 瞭解如何在 Windows Forms 中使用資料系結，以在表單上的控制項中顯示資料來源的資訊，並對其進行變更。
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: 3dfce24147caf9b138916ca8dc3b7a9010439f58
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325544"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="3e069-103">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="3e069-103">Windows Forms Data Binding</span></span>
<span data-ttu-id="3e069-104">在 Windows Form 中的資料繫結會提供方法，讓您在表單上的控制項顯示及變更來自資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="3e069-104">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="3e069-105">您不只可以繫結至傳統的資料來源，也能繫結至幾乎任何包含資料的結構。</span><span class="sxs-lookup"><span data-stu-id="3e069-105">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e069-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="3e069-106">In This Section</span></span>  
 [<span data-ttu-id="3e069-107">資料繫結和 Windows Form</span><span class="sxs-lookup"><span data-stu-id="3e069-107">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)  
 <span data-ttu-id="3e069-108">提供在 Windows Form 中的資料繫結概觀。</span><span class="sxs-lookup"><span data-stu-id="3e069-108">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="3e069-109">Windows Form 支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="3e069-109">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="3e069-110">描述可以搭配 Windows Form 使用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="3e069-110">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="3e069-111">與資料繫結相關的介面</span><span class="sxs-lookup"><span data-stu-id="3e069-111">Interfaces Related to Data Binding</span></span>](interfaces-related-to-data-binding.md)  
 <span data-ttu-id="3e069-112">描述數個與 Windows Form 資料繫結搭配使用的介面。</span><span class="sxs-lookup"><span data-stu-id="3e069-112">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="3e069-113">作法：巡覽 Windows Forms 中的資料</span><span class="sxs-lookup"><span data-stu-id="3e069-113">How to: Navigate Data in Windows Forms</span></span>](how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="3e069-114">示範如何瀏覽資料來源中的項目。</span><span class="sxs-lookup"><span data-stu-id="3e069-114">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="3e069-115">Windows Form 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="3e069-115">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="3e069-116">說明不同類型的 Windows Form 資料繫結變更通知。</span><span class="sxs-lookup"><span data-stu-id="3e069-116">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="3e069-117">作法：實作 INotifyPropertyChanged 介面</span><span class="sxs-lookup"><span data-stu-id="3e069-117">How to: Implement the INotifyPropertyChanged Interface</span></span>](how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="3e069-118">示範如何實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。</span><span class="sxs-lookup"><span data-stu-id="3e069-118">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="3e069-119">介面會與繫結的控制項溝通商務物件的屬性變更</span><span class="sxs-lookup"><span data-stu-id="3e069-119">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="3e069-120">作法：套用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="3e069-120">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="3e069-121">示範如何將*PropertyName*已變更模式套用至 Windows Forms 使用者控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="3e069-121">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="3e069-122">作法：實作 ITypedList 介面</span><span class="sxs-lookup"><span data-stu-id="3e069-122">How to: Implement the ITypedList Interface</span></span>](how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="3e069-123">示範如何藉由實作 <xref:System.ComponentModel.ITypedList> 介面，讓您探索可繫結清單的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3e069-123">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="3e069-124">作法：實作 IListSource 介面</span><span class="sxs-lookup"><span data-stu-id="3e069-124">How to: Implement the IListSource Interface</span></span>](how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="3e069-125">示範如何實作 <xref:System.ComponentModel.IListSource> 介面來建立可繫結的類別，它不會實作 <xref:System.Collections.IList>，而是從另一個位置提供清單。</span><span class="sxs-lookup"><span data-stu-id="3e069-125">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="3e069-126">作法：確保繫結至相同資料來源的多個控制項都能保持同步</span><span class="sxs-lookup"><span data-stu-id="3e069-126">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="3e069-127">示範如何處理 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件以確保繫結至資料來源的所有控制項都能保持同步。</span><span class="sxs-lookup"><span data-stu-id="3e069-127">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="3e069-128">作法：確認子資料表中選取的資料列保持在正確位置</span><span class="sxs-lookup"><span data-stu-id="3e069-128">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="3e069-129">示範在變更父資料表的欄位時，如何確定子資料表的所選取資料列不會變更。</span><span class="sxs-lookup"><span data-stu-id="3e069-129">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="3e069-130">另請參閱與資料系結[相關的介面](interfaces-related-to-data-binding.md)、[如何：導覽 Windows Forms 中的資料](how-to-navigate-data-in-windows-forms.md)，以及[如何：在 Windows Form 上建立簡單繫結控制項](how-to-create-a-simple-bound-control-on-a-windows-form.md)。</span><span class="sxs-lookup"><span data-stu-id="3e069-130">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3e069-131">參考</span><span class="sxs-lookup"><span data-stu-id="3e069-131">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="3e069-132">描述代表可繫結元件和資料來源之間繫結的類別。</span><span class="sxs-lookup"><span data-stu-id="3e069-132">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="3e069-133">描述封裝資料來源以便繫結至控制項的類別。</span><span class="sxs-lookup"><span data-stu-id="3e069-133">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3e069-134">相關章節</span><span class="sxs-lookup"><span data-stu-id="3e069-134">Related Sections</span></span>  
 [<span data-ttu-id="3e069-135">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="3e069-135">BindingSource Component</span></span>](./controls/bindingsource-component.md)  
 <span data-ttu-id="3e069-136">包含主題的清單，這些主題會示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件。</span><span class="sxs-lookup"><span data-stu-id="3e069-136">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="3e069-137">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="3e069-137">DataGridView Control</span></span>](./controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="3e069-138">提供主題的清單，這些主題會示範如何使用可繫結 datagrid 控制項。</span><span class="sxs-lookup"><span data-stu-id="3e069-138">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="3e069-139">另請參閱[存取 Visual Studio 中的資料](/visualstudio/data-tools/accessing-data-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="3e069-139">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
