---
title: "如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ADO.NET [Windows Form]"
  - "BindingSource 元件 [Windows Form], 排序及篩選資料"
  - "資料 [Windows Form], 篩選"
  - "資料 [Windows Form], 排序"
  - "資料排序, ADO.NET"
  - "篩選 [Windows Form], ADO.NET"
  - "排序資料"
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：使用 Windows Form BindingSource 元件排序和篩選 ADO.NET 資料
您可以透過 <xref:System.Windows.Forms.BindingSource.Sort%2A> 和 <xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性，公開 \(Expose\) <xref:System.Windows.Forms.BindingSource> 控制項的排序和篩選功能。  當基礎資料來源是 <xref:System.ComponentModel.IBindingList> 時可套用簡單排序，當基礎資料來源是 <xref:System.ComponentModel.IBindingListView> 時則可套用篩選和進階排序。  <xref:System.Windows.Forms.BindingSource.Sort%2A> 屬性需要使用標準 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 語法，也就是在代表資料來源中資料行名稱的字串之後跟隨著 `ASC` 或 `DESC`，以便指出清單應該依遞增或遞減順序來排序。  可以利用逗號來分隔每個資料行，藉此設定進階排序或多重資料行排序。  <xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性可接受字串運算式。  
  
> [!NOTE]
>  在連接字串內儲存機密資訊 \(例如密碼\) 會影響應用程式的安全性。  使用 Windows 驗證 \(也稱為整合式安全性\) 是控制資料庫存取的更安全方式。  如需詳細資訊，請參閱[保護連接資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
### 若要使用 BindingSource 來篩選資料  
  
-   將 <xref:System.Windows.Forms.BindingSource.Filter%2A> 屬性設定為您要的運算式。  
  
     在下列程式碼範例中，運算式為資料行名稱之後跟隨著您要的資料行值。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### 若要使用 BindingSource 來排序資料  
  
1.  將 <xref:System.Windows.Forms.BindingSource.Sort%2A> 屬性設定為您要的資料行名稱，之後跟隨著 `ASC` 或 `DESC`，以便指出是遞增順序或遞減順序。  
  
2.  以逗號分隔多重資料行。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## 範例  
 下列程式碼範例會將 Northwind 範例資料庫的 Customers 資料表中的資料載入 <xref:System.Windows.Forms.DataGridView> 控制項，然後再篩選並排序所顯示的資料。  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## 編譯程式碼  
 若要執行這個範例，請將程式碼貼至表單，且該表單包含名為 `BindingSource1` 的 <xref:System.Windows.Forms.BindingSource> 以及名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView>。  處理表單的 <xref:System.Windows.Forms.Form.Load> 事件，並且在載入事件處理常式方法中呼叫 `InitializeSortedFilteredBindingSource`。  
  
## 請參閱  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>   
 <xref:System.Windows.Forms.BindingSource.Filter%2A>   
 [如何：安裝範例資料庫](../Topic/How%20to:%20Install%20Sample%20Databases.md)   
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)