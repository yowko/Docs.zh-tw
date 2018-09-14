---
title: 如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料
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
ms.openlocfilehash: 932d30d356225d88d7ef149561cc4c5cc8ac4dd0
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592099"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料
排序和篩選功能，您可以公開<xref:System.Windows.Forms.BindingSource>透過控制<xref:System.Windows.Forms.BindingSource.Sort%2A>和<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性。 您可以套用簡單排序的基礎資料來源時<xref:System.ComponentModel.IBindingList>，您可以套用的篩選和進階排序的資料來源時<xref:System.ComponentModel.IBindingListView>。 <xref:System.Windows.Forms.BindingSource.Sort%2A>屬性需要標準[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]語法： 字串，表示資料來源中的資料行的名稱後面加上`ASC`或`DESC`來指出是否應該以遞增或遞減順序排序清單。 您可以設定進階排序，或使用逗號分隔符號隔開每個資料行的多重資料行排序。 <xref:System.Windows.Forms.BindingSource.Filter%2A>屬性會採用字串運算式。  
  
> [!NOTE]
>  在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
### <a name="to-filter-data-with-the-bindingsource"></a>若要篩選使用 BindingSource 的資料  
  
-   設定<xref:System.Windows.Forms.BindingSource.Filter%2A>屬性，以您想要的運算式。  
  
     在下列程式碼範例中，運算式會是資料行名稱，後面接著您要的資料行的值。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>使用 BindingSource 的資料進行排序  
  
1.  設定<xref:System.Windows.Forms.BindingSource.Sort%2A>屬性設為資料行名稱，您想要後面`ASC`或`DESC`表示遞增或遞減順序。  
  
2.  請以逗號分隔多個資料行。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會載入資料至 Northwind 範例資料庫的 Customers 資料表中<xref:System.Windows.Forms.DataGridView>控制項，並篩選並排序顯示的資料。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此範例中，貼上程式碼包含表單的表單<xref:System.Windows.Forms.BindingSource>名為`BindingSource1`並<xref:System.Windows.Forms.DataGridView>名為`dataGridView1`。 處理<xref:System.Windows.Forms.Form.Load>事件的形式和呼叫`InitializeSortedFilteredBindingSource`load 事件處理常式方法中。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [如何：安裝範例資料庫](https://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)
