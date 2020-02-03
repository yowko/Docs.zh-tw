---
title: 使用 BindingSource 元件排序和篩選 ADO.NET 資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742970"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料
您可以透過 <xref:System.Windows.Forms.BindingSource.Sort%2A> 和 <xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性，公開 <xref:System.Windows.Forms.BindingSource> 控制的排序和篩選功能。 當基礎資料來源是 <xref:System.ComponentModel.IBindingList>時，您可以套用簡單排序，而且當資料來源為 <xref:System.ComponentModel.IBindingListView>時，您可以套用篩選和先進排序。 <xref:System.Windows.Forms.BindingSource.Sort%2A> 屬性需要標準 ADO.NET 語法：字串，代表資料來源中的資料行名稱，後面接著 `ASC` 或 `DESC`，以指出清單是否應該以遞增或遞減順序排序。 您可以使用逗號分隔字元來分隔每個資料行，以設定高階排序或多重資料行排序。 <xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性會接受字串運算式。  
  
> [!NOTE]
> 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
### <a name="to-filter-data-with-the-bindingsource"></a>使用 BindingSource 來篩選資料  
  
- 將 [<xref:System.Windows.Forms.BindingSource.Filter%2A>] 屬性設為您想要的運算式。  
  
     在下列程式碼範例中，運算式是資料行名稱，後面接著您想要用於資料行的值。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>使用 BindingSource 排序資料  
  
1. 將 [<xref:System.Windows.Forms.BindingSource.Sort%2A>] 屬性設為您想要的資料行名稱，後面接著 `ASC` 或 `DESC` 以指示遞增或遞減順序。  
  
2. 以逗號分隔多個資料行。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會將資料從 Northwind 範例資料庫的 Customers 資料表載入至 <xref:System.Windows.Forms.DataGridView> 控制項，並篩選並排序顯示的資料。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此範例，請將程式碼貼入包含名為 `BindingSource1` 之 <xref:System.Windows.Forms.BindingSource> 的表單中，以及名為 `dataGridView1`的 <xref:System.Windows.Forms.DataGridView>。 處理表單的 <xref:System.Windows.Forms.Form.Load> 事件，並在 load 事件處理常式方法中呼叫 `InitializeSortedFilteredBindingSource`。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [如何：安裝範例資料庫](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [BindingSource 元件](bindingsource-component.md)
