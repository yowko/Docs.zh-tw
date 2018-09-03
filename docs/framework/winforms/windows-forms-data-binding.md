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
# <a name="windows-forms-data-binding"></a>Windows Form 資料繫結
在 Windows Form 中的資料繫結會提供方法，讓您在表單上的控制項顯示及變更來自資料來源的資訊。 您不只可以繫結至傳統的資料來源，也能繫結至幾乎任何包含資料的結構。  
  
## <a name="in-this-section"></a>本節內容  
 [資料繫結和 Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 提供在 Windows Form 中的資料繫結概觀。  
  
 [Windows Forms 支援的資料來源](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 描述可以搭配 Windows Form 使用的資料來源。  
  
 [與資料繫結相關的介面](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 描述數個與 Windows Form 資料繫結搭配使用的介面。  
  
 [操作說明：巡覽 Windows Forms 中的資料](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)  
 示範如何瀏覽資料來源中的項目。  
  
 [Windows Forms 資料繫結中的變更告知](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 說明不同類型的 Windows Form 資料繫結變更通知。  
  
 [操作說明：實作 INotifyPropertyChanged 介面](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md)  
 示範如何實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。 介面會與繫結的控制項溝通商務物件的屬性變更  
  
 [操作說明：套用 PropertyNameChanged 模式](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 示範如何套用*PropertyName*模式的 Windows Forms 使用者控制項的屬性。  
  
 [操作說明：實作 ITypedList 介面](../../../docs/framework/winforms/how-to-implement-the-itypedlist-interface.md)  
 示範如何藉由實作 <xref:System.ComponentModel.ITypedList> 介面，讓您探索可繫結清單的結構描述。  
  
 [操作說明：實作 IListSource 介面](../../../docs/framework/winforms/how-to-implement-the-ilistsource-interface.md)  
 示範如何實作 <xref:System.ComponentModel.IListSource> 介面來建立可繫結的類別，它不會實作 <xref:System.Collections.IList>，而是從另一個位置提供清單。  
  
 [操作說明：確保繫結至相同資料來源的多個控制項都能保持同步](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 示範如何處理 <xref:System.Windows.Forms.BindingSource.BindingComplete> 事件以確保繫結至資料來源的所有控制項都能保持同步。  
  
 [操作說明：確認子資料表中選取的資料列保持在正確位置](../../../docs/framework/winforms/ensure-the-selected-row-in-a-child-table-correct.md)  
 示範在變更父資料表的欄位時，如何確定子資料表的所選取資料列不會變更。  
  
 另請參閱[介面與相關的資料繫結](https://msdn.microsoft.com/library/41e17s4b\(v=vs.110\))，[如何： 在 Windows Form 中的 瀏覽資料](https://msdn.microsoft.com/library/b63ha24w\(v=vs.110\))， [How to： 建立簡單繫結控制項在 Windows Form 上](https://msdn.microsoft.com/library/sw223a62\(v=vs.110\))。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Windows.Forms.Binding?displayProperty=nameWithType>  
 描述代表可繫結元件和資料來源之間繫結的類別。  
  
 <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType>  
 描述封裝資料來源以便繫結至控制項的類別。  
  
## <a name="related-sections"></a>相關章節  
 [BindingSource 元件](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 包含主題的清單，這些主題會示範如何使用 <xref:System.Windows.Forms.BindingSource> 元件。  
  
 [DataGridView 控制項](../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 提供主題的清單，這些主題會示範如何使用可繫結 datagrid 控制項。  
  
 另請參閱[Accessing Data in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)。
