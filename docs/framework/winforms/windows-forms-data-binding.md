---
title: Windows Form 資料繫結
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms]
- Windows Forms, data binding
- data [Windows Forms], architecture
- Windows Forms controls, data binding
ms.assetid: c3826d8e-ea25-4ad4-a669-45bfb19192aa
ms.openlocfilehash: b33ad9d78230588b9c1afd5d59fd0333e2cd18a6
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747057"
---
# <a name="windows-forms-data-binding"></a><span data-ttu-id="bf806-102">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="bf806-102">Windows Forms Data Binding</span></span>
<span data-ttu-id="bf806-103">在 Windows Form 中的資料繫結會提供方法，讓您在表單上的控制項顯示及變更來自資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="bf806-103">Data binding in Windows Forms gives you the means to display and make changes to information from a data source in controls on the form.</span></span> <span data-ttu-id="bf806-104">您不只可以繫結至傳統的資料來源，也能繫結至幾乎任何包含資料的結構。</span><span class="sxs-lookup"><span data-stu-id="bf806-104">You can bind to both traditional data sources as well as almost any structure that contains data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf806-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="bf806-105">In This Section</span></span>  
 [<span data-ttu-id="bf806-106">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf806-106">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 <span data-ttu-id="bf806-107">提供在 Windows Form 中的資料繫結概觀。</span><span class="sxs-lookup"><span data-stu-id="bf806-107">Provides an overview of data binding in Windows Forms.</span></span>  
  
 [<span data-ttu-id="bf806-108">Windows Forms 支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="bf806-108">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 <span data-ttu-id="bf806-109">描述可以搭配 Windows Form 使用的資料來源。</span><span class="sxs-lookup"><span data-stu-id="bf806-109">Describes the data sources that can be used with Windows Forms.</span></span>  
  
 [<span data-ttu-id="bf806-110">與資料繫結相關的介面</span><span class="sxs-lookup"><span data-stu-id="bf806-110">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 <span data-ttu-id="bf806-111">描述數個與 Windows Form 資料繫結搭配使用的介面。</span><span class="sxs-lookup"><span data-stu-id="bf806-111">Describes several of the interfaces used with Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="bf806-112">如何：瀏覽 Windows Form 中的資料</span><span class="sxs-lookup"><span data-stu-id="bf806-112">How to: Navigate Data in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 <span data-ttu-id="bf806-113">示範如何瀏覽資料來源中的項目。</span><span class="sxs-lookup"><span data-stu-id="bf806-113">Shows how to navigate through items in a data source.</span></span>  
  
 [<span data-ttu-id="bf806-114">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="bf806-114">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 <span data-ttu-id="bf806-115">說明不同類型的 Windows Form 資料繫結變更通知。</span><span class="sxs-lookup"><span data-stu-id="bf806-115">Describes different types of change notification for Windows Forms data binding.</span></span>  
  
 [<span data-ttu-id="bf806-116">如何：實作 INotifyPropertyChanged 介面</span><span class="sxs-lookup"><span data-stu-id="bf806-116">How to: Implement the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 <span data-ttu-id="bf806-117">示範如何實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。</span><span class="sxs-lookup"><span data-stu-id="bf806-117">Shows how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="bf806-118">介面會與繫結的控制項溝通商務物件的屬性變更</span><span class="sxs-lookup"><span data-stu-id="bf806-118">The interface  communicates to a bound control the property changes on a business object</span></span>  
  
 [<span data-ttu-id="bf806-119">如何：套用 PropertyNameChanged 模式</span><span class="sxs-lookup"><span data-stu-id="bf806-119">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 <span data-ttu-id="bf806-120">示範如何套用*PropertyName*模式的 Windows Forms 使用者控制項的屬性。</span><span class="sxs-lookup"><span data-stu-id="bf806-120">Shows how to apply the *PropertyName*Changed pattern to properties of a Windows Forms user control.</span></span>  
  
 [<span data-ttu-id="bf806-121">如何：實作 ITypedList 介面</span><span class="sxs-lookup"><span data-stu-id="bf806-121">How to: Implement the ITypedList Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 <span data-ttu-id="bf806-122">示範如何藉由實作 <xref:System.ComponentModel.ITypedList> 介面，讓您探索可繫結清單的結構描述。</span><span class="sxs-lookup"><span data-stu-id="bf806-122">Shows how to enable discovery of the schema for a bindable list by implementing the <xref:System.ComponentModel.ITypedList> interface.</span></span>  
  
 [<span data-ttu-id="bf806-123">如何：實作 IListSource 介面</span><span class="sxs-lookup"><span data-stu-id="bf806-123">How to: Implement the IListSource Interface</span></span>](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 <span data-ttu-id="bf806-124">示範如何實作 <xref:System.ComponentModel.IListSource> 介面來建立可繫結的類別，它不會實作 <xref:System.Collections.IList>，而是從另一個位置提供清單。</span><span class="sxs-lookup"><span data-stu-id="bf806-124">Shows how to implement the <xref:System.ComponentModel.IListSource> interface to create a bindable class does not implement <xref:System.Collections.IList>, but provides a list from another location.</span></span>  
  
 [<span data-ttu-id="bf806-125">如何：請確定多個控制項繫結至相同的資料來源都能保持同步</span><span class="sxs-lookup"><span data-stu-id="bf806-125">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 <span data-ttu-id="bf806-126">示範如何處理 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件以確保繫結至資料來源的所有控制項都能保持同步。</span><span class="sxs-lookup"><span data-stu-id="bf806-126">Shows how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event to ensure all controls bound to a data source remain synchronized.</span></span>  
  
 [<span data-ttu-id="bf806-127">如何：確認子資料表中選取的資料列保持在正確的位置</span><span class="sxs-lookup"><span data-stu-id="bf806-127">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 <span data-ttu-id="bf806-128">示範在變更父資料表的欄位時，如何確定子資料表的所選取資料列不會變更。</span><span class="sxs-lookup"><span data-stu-id="bf806-128">Shows how to ensure the selected row of a child table does not change, when a change is made to a field of the parent table.</span></span>  
  
 <span data-ttu-id="bf806-129">另請參閱[介面與相關的資料繫結](interfaces-related-to-data-binding.md)， [How to:瀏覽 Windows Form 中的資料](how-to-navigate-data-in-windows-forms.md)，和[How to:建立簡單繫結控制項在 Windows Form 上的](how-to-create-a-simple-bound-control-on-a-windows-form.md)。</span><span class="sxs-lookup"><span data-stu-id="bf806-129">Also see [Interfaces Related to Data Binding](interfaces-related-to-data-binding.md), [How to: Navigate Data in Windows Forms](how-to-navigate-data-in-windows-forms.md), and [How to: Create a Simple-Bound Control on a Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bf806-130">參考資料</span><span class="sxs-lookup"><span data-stu-id="bf806-130">Reference</span></span>  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 <span data-ttu-id="bf806-131">描述代表可繫結元件和資料來源之間繫結的類別。</span><span class="sxs-lookup"><span data-stu-id="bf806-131">Describes the class that represents the binding between a bindable component and a data source.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 <span data-ttu-id="bf806-132">描述封裝資料來源以便繫結至控制項的類別。</span><span class="sxs-lookup"><span data-stu-id="bf806-132">Describes the class that encapsulates a data source for binding to controls.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bf806-133">相關章節</span><span class="sxs-lookup"><span data-stu-id="bf806-133">Related Sections</span></span>  
 [<span data-ttu-id="bf806-134">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="bf806-134">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 <span data-ttu-id="bf806-135">包含主題的清單，這些主題會示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件。</span><span class="sxs-lookup"><span data-stu-id="bf806-135">Contains a list of topics that demonstrate how to use the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
 [<span data-ttu-id="bf806-136">DataGridView 控制項</span><span class="sxs-lookup"><span data-stu-id="bf806-136">DataGridView Control</span></span>](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 <span data-ttu-id="bf806-137">提供主題的清單，這些主題會示範如何使用可繫結 datagrid 控制項。</span><span class="sxs-lookup"><span data-stu-id="bf806-137">Provides a list of topics that demonstrate how to use a bindable datagrid control.</span></span>  
  
 <span data-ttu-id="bf806-138">另請參閱[Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="bf806-138">Also see [Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).</span></span>
