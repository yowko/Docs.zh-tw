---
title: Windows Form 資料繫結
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: cfb4c59c76142420f479b0b16a6d80317e98d159
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486006"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="3307e-102">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="3307e-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="3307e-103">在 Windows Form 中的資料繫結會提供方法，讓您在表單上的控制項顯示及變更來自資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="3307e-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="3307e-104">您不只可以繫結至傳統的資料來源，也能繫結至幾乎任何包含資料的結構。</span><span class="sxs-lookup"><span data-stu-id="3307e-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3307e-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="3307e-105">In This Section</span></span>  
 [<span data-ttu-id="3307e-106">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3307e-106">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 <span data-ttu-id="3307e-107">提供在 Windows Form 中的資料繫結概觀。</span><span class="sxs-lookup"><span data-stu-id="3307e-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="3307e-108">Windows Forms 支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="3307e-108">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="3307e-109">描述可以搭配 Windows Form 使用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="3307e-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="3307e-110">與資料繫結相關的介面</span><span class="sxs-lookup"><span data-stu-id="3307e-110">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 <span data-ttu-id="3307e-111">描述數個與 Windows Form 資料繫結搭配使用的介面。</span><span class="sxs-lookup"><span data-stu-id="3307e-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="3307e-112">操作說明：巡覽 Windows Forms 中的資料</span><span class="sxs-lookup"><span data-stu-id="3307e-112">How to: Navigate Data in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="3307e-113">示範如何瀏覽資料來源中的項目。</span><span class="sxs-lookup"><span data-stu-id="3307e-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="3307e-114">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="3307e-114">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="3307e-115">說明不同類型的 Windows Form 資料繫結變更通知。</span><span class="sxs-lookup"><span data-stu-id="3307e-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="3307e-116">操作說明：實作 INotifyPropertyChanged 介面</span><span class="sxs-lookup"><span data-stu-id="3307e-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="3307e-117">示範如何實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。</span><span class="sxs-lookup"><span data-stu-id="3307e-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="3307e-118">介面會與繫結的控制項溝通商務物件的屬性變更</span><span class="sxs-lookup"><span data-stu-id="3307e-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="3307e-119">操作說明：套用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="3307e-119">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="3307e-120">示範如何套用*PropertyName*模式的 Windows Forms 使用者控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="3307e-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="3307e-121">操作說明：實作 ITypedList 介面</span><span class="sxs-lookup"><span data-stu-id="3307e-121">How to: Implement the ITypedList Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="3307e-122">示範如何藉由實作 <xref:System.ComponentModel.ITypedList> 介面，讓您探索可繫結清單的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3307e-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="3307e-123">操作說明：實作 IListSource 介面</span><span class="sxs-lookup"><span data-stu-id="3307e-123">How to: Implement the IListSource Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="3307e-124">示範如何實作 <xref:System.ComponentModel.IListSource> 介面來建立可繫結的類別，它不會實作 <xref:System.Collections.IList>，而是從另一個位置提供清單。</span><span class="sxs-lookup"><span data-stu-id="3307e-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="3307e-125">操作說明：確保繫結至相同資料來源的多個控制項都能保持同步</span><span class="sxs-lookup"><span data-stu-id="3307e-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="3307e-126">示範如何處理 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件以確保繫結至資料來源的所有控制項都能保持同步。</span><span class="sxs-lookup"><span data-stu-id="3307e-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="3307e-127">操作說明：確認子資料表中選取的資料列保持在正確位置</span><span class="sxs-lookup"><span data-stu-id="3307e-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="3307e-128">示範在變更父資料表的欄位時，如何確定子資料表的所選取資料列不會變更。</span><span class="sxs-lookup"><span data-stu-id="3307e-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="3307e-129">另請參閱[介面與相關的資料繫結](https://msdn.microsoft.com/library/41e17s4b\(v=vs.110\))，[如何： 在 Windows Form 中的 瀏覽資料](https://msdn.microsoft.com/library/b63ha24w\(v=vs.110\))， [How to： 建立簡單繫結控制項在 Windows Form 上](https://msdn.microsoft.com/library/sw223a62\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="3307e-129">Also see [Interfaces Related to Data Binding](https://msdn.microsoft.com/library/41e17s4b\(v=vs.110\)), [How to: Navigate Data in Windows Forms](https://msdn.microsoft.com/library/b63ha24w\(v=vs.110\)), [How to: Create a Simple-Bound Control on a Windows Form](https://msdn.microsoft.com/library/sw223a62\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3307e-130">參考資料</span><span class="sxs-lookup"><span data-stu-id="3307e-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="3307e-131">描述代表可繫結元件和資料來源之間繫結的類別。</span><span class="sxs-lookup"><span data-stu-id="3307e-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="3307e-132">描述封裝資料來源以便繫結至控制項的類別。</span><span class="sxs-lookup"><span data-stu-id="3307e-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3307e-133">相關章節</span><span class="sxs-lookup"><span data-stu-id="3307e-133">Related Sections</span></span>  
 [<span data-ttu-id="3307e-134">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="3307e-134">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 <span data-ttu-id="3307e-135">包含主題的清單，這些主題會示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件。</span><span class="sxs-lookup"><span data-stu-id="3307e-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="3307e-136">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="3307e-136">DataGridView Control</span></span>](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="3307e-137">提供主題的清單，這些主題會示範如何使用可繫結 datagrid 控制項。</span><span class="sxs-lookup"><span data-stu-id="3307e-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="3307e-138">另請參閱[Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="3307e-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
