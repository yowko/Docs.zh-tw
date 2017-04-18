---
title: "DataGrid 控制項概觀 (Windows Form) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataGrid"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "資料集 [Windows Form] 繫結至 DataGrid 控制項"
  - "資料繫結 DataGrid 控制項"
  - "資料行 [Windows Form] DataGrid 控制項"
  - "資料來源繫結至 DataGrid 控制項"
  - "繫結至 DataGrid 控制項中的資料表 [Windows Form]"
  - "DataGrid 控制項 [Windows Form]，資料繫結"
  - "關於 DataGrid 控制項的 DataGrid 控制項 [Windows Form]"
  - "DataGrid 控制項中的父資料表"
  - "在 DataGrid 控制項中顯示的資料表 [Windows Form]"
  - "關於資料格的資料格"
  - "DataGrid 控制項的多個資料表"
  - "重新排序資料 [Windows Form]"
  - "瀏覽資料 [Windows Form]"
  - "繫結的控制項，DataGrid 控制項"
  - "資料繫結控制項 DataGrid"
  - "DataGrid 中的父資料表巡覽"
  - "子資料表，DataGrid 控制項"
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# DataGrid 控制項概觀 (Windows Form)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView>控制項取代，並將功能加入至<xref:System.Windows.Forms.DataGrid>控制; 不過， <xref:System.Windows.Forms.DataGrid>控制項是回溯相容性及未來使用，您可以選擇保留。 如需詳細資訊，請參閱[差異 Windows Form DataGridView 和 DataGrid 控制項之間](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows Form <xref:System.Windows.Forms.DataGrid>控制項會在一連串的資料列和資料行中顯示資料。 最簡單的案例是，以沒有包含關聯性的單一資料表，將格線繫結至資料來源。 在此案例中，資料會出現在簡單的資料列和資料行中，就像在試算表中一樣。 如需資料繫結至其他控制項的詳細資訊，請參閱[資料繫結和 Windows Form](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)。  
  
 如果<xref:System.Windows.Forms.DataGrid>繫結至資料與多個相關資料表，以及如果格線上啟用巡覽，格線會顯示展開器中每個資料列。 使用展開器可讓使用者從父資料表移到子資料表。 按一下節點會顯示子資料表，按一下上一頁按鈕，就會顯示原始的父資料表。 格線會以這種方式來顯示資料表之間的階層式關聯性。  
  
 下列螢幕擷取畫面顯示以多個資料表繫結至資料的 DataGrid。  
  
 ![繫結至具有多個資料表之資料的 DataGrid](../../../../docs/framework/winforms/controls/media/vbcontrol1.gif "vbControl1")  
繫結至具有多個資料表之資料的 DataGrid  
  
 <xref:System.Windows.Forms.DataGrid>可以提供使用者介面之間的巡覽相關的資料表，以及豐富的格式化和編輯功能、 資料集。  
  
 資料的顯示和操作是不同的功能：控制項會處理使用者介面，而資料更新是由 Windows Form 資料繫結架構和 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者來處理。 因此，繫結至相同的資料來源的多個控制項將保持同步。  
  
> [!NOTE]
>  如果您熟悉 Visual Basic 6.0 中的 DataGrid 控制項，您會發現一些顯著的差異，在 Windows form <xref:System.Windows.Forms.DataGrid>控制項。  
  
 當格線繫結至<xref:System.Data.DataSet>，資料行和資料列自動建立、 格式化，並填滿。 如需詳細資訊，請參閱 [Data Binding and Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)。 下列產生<xref:System.Windows.Forms.DataGrid>控制項，您可以新增、 刪除、 重新排列及格式化資料行和資料列，您的需求而定。  
  
## <a name="binding-data-to-the-control"></a>將資料繫結至控制項  
 如<xref:System.Windows.Forms.DataGrid>控制項運作，它應該繫結至資料來源使用<xref:System.Windows.Forms.DataGrid.DataSource%2A>和<xref:System.Windows.Forms.DataGrid.DataMember%2A>在設計階段屬性或<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>方法在執行階段。 此繫結指向<xref:System.Windows.Forms.DataGrid>具現化的資料來源物件，例如<xref:System.Data.DataSet>或<xref:System.Data.DataTable>)。 <xref:System.Windows.Forms.DataGrid>控制項顯示的資料執行的動作結果。 大部分資料特定動作，不會透過執行<xref:System.Windows.Forms.DataGrid> ，而是透過資料來源。  
  
 如果透過任何機制，更新繫結資料集中<xref:System.Windows.Forms.DataGrid>控制項會反映那些變更。 如果資料格及其資料表樣式和資料行樣式`ReadOnly`屬性設定為`false`，可透過更新資料集中<xref:System.Windows.Forms.DataGrid>控制項。  
  
 可以顯示一個資料表<xref:System.Windows.Forms.DataGrid>一次。 如果資料表之間有定義父子式關聯性，使用者可以選取要顯示在資料表相關的資料表之間移動<xref:System.Windows.Forms.DataGrid>控制項。 如需有關繫結資訊<xref:System.Windows.Forms.DataGrid> ，來控制對[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]資料來源在設計階段或執行的階段，請參閱[How to︰ 將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
 有效資料來源<xref:System.Windows.Forms.DataGrid>包括︰  
  
-   <xref:System.Data.DataTable>類別  
  
-   <xref:System.Data.DataView>類別  
  
-   <xref:System.Data.DataSet>類別  
  
-   <xref:System.Data.DataViewManager>類別  
  
 如果您的來源是資料集，資料集可能是表單中的物件，或是由 XML Web 服務傳遞至表單的物件。 您可以繫結至具類型資料集或不具類型的資料集。  
  
 您也可以繫結<xref:System.Windows.Forms.DataGrid>如果控制權傳輸至其他結構的結構，例如陣列中的項目中的物件公開公用屬性。 格線會將項目的所有公用屬性顯示在結構中。 例如，如果您將繫結<xref:System.Windows.Forms.DataGrid>控制項陣列的客戶物件，此格線會顯示這些客戶物件的所有公用屬性。 在某些案例中，這表示雖然您可以繫結至結構，但是所產生的繫結結構可能沒有實際的應用程式。 例如，您可以繫結至整數陣列，但是因為 `Integer` 資料類型不支援公用屬性，所以格線無法顯示任何資料。  
  
 如果下列結構的項目公開公用屬性，您就可以繫結至這些結構：  
  
-   實作的元件， <xref:System.Collections.IList>介面。 這包括一維陣列。  
  
-   實作的元件， <xref:System.ComponentModel.IListSource>介面。  
  
-   實作的元件， <xref:System.ComponentModel.IBindingList>介面。  
  
 如需可能資料來源的詳細資訊，請參閱[支援的 Windows Form 資料來源](../../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)。  
  
## <a name="grid-display"></a>格線顯示  
 一種常見用法<xref:System.Windows.Forms.DataGrid>控制項是顯示單一資料表的資料集中的資料。 不過，此控制項也可以用來顯示多個資料表，包括相關的資料表。 格線的顯示方式會根據資料來源自動調整。 下表顯示各種組態的顯示內容。  
  
|資料集的內容|顯示的內容|  
|--------------------------|-----------------------|  
|單一資料表。|資料表會顯示在格線中。|  
|多個資料表。|格線可以顯示樹狀檢視，讓使用者能夠巡覽，以尋找他們想要顯示的資料表。|  
|多個相關的資料表。|格線可以顯示用來選取資料表的樹狀檢視，或者您可以指定格線顯示父資料表。 父資料表中的記錄可讓使用者巡覽至相關的子資料列。|  
  
> [!NOTE]
>  資料集內的資料表會使用相關聯<xref:System.Data.DataRelation>。  另請參閱[集中 HYPERLINK"http://msdn.microsoft.com/library/dbwcse3d (v = vs.110) 」 的關聯性](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.110\))或[集中的關聯性](http://msdn.microsoft.com/library/dbwcse3d\(v=vs.120\))。  
  
 當<xref:System.Windows.Forms.DataGrid>控制項顯示資料表和<xref:System.Windows.Forms.DataGrid.AllowSorting%2A>屬性設定為`true`，只要按一下欄標題重新排序資料。 使用者也可以加入資料列以及編輯儲存格。  
  
 一組資料表之間的關聯性，會以巡覽的父/子結構向使用者顯示。 父資料表是資料的最高層級，而子資料表是從父資料表中的個別清單衍生的那些資料表。 包含子資料表的每個父資料列中，都會顯示展開器。 按一下展開器，就會產生類似網頁的子資料表連結清單。 當使用者選取連結時，就會顯示子資料表。 按一下顯示/隱藏父資料列圖示 (![顯示/隱藏父資料列圖示](../../../../docs/framework/winforms/controls/media/vbicon.png "vbIcon")) 將會隱藏父資料表的相關資訊，則會重新顯示，如果使用者先前已隱藏它。 使用者可以按一下上一頁按鈕，以回到先前檢視的資料表。  
  
## <a name="columns-and-rows"></a>資料行和資料列  
 <xref:System.Windows.Forms.DataGrid>組成的集合<xref:System.Windows.Forms.DataGridTableStyle>物件中所包含的<xref:System.Windows.Forms.DataGrid>控制項的<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性。 資料表樣式可能包含一系列<xref:System.Windows.Forms.DataGridColumnStyle>物件中所包含的<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性<xref:System.Windows.Forms.DataGridTableStyle>... 您可以編輯<xref:System.Windows.Forms.DataGrid.TableStyles%2A>和<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性使用透過存取的集合編輯器**屬性**視窗。  
  
 任何<xref:System.Windows.Forms.DataGridTableStyle>聯<xref:System.Windows.Forms.DataGrid>可以透過存取控制<xref:System.Windows.Forms.GridTableStylesCollection>。 <xref:System.Windows.Forms.GridTableStylesCollection>可以與設計工具中編輯<xref:System.Windows.Forms.DataGridTableStyle>集合編輯器 中，或以程式設計方式透過<xref:System.Windows.Forms.DataGrid>控制項的<xref:System.Windows.Forms.DataGrid.TableStyles%2A>屬性。  
  
 ![DataGrid 控制項中所包含的物件](../../../../docs/framework/winforms/controls/media/vbcolumns1.png "vbColumns1")  
下圖顯示 DataGrid 控制項中所包含的物件。  
  
 資料表樣式和資料行樣式與同步處理<xref:System.Data.DataTable>物件和<xref:System.Data.DataColumn>物件藉由設定其`MappingName`屬性設為適當<xref:System.Data.DataTable.TableName%2A>和<xref:System.Data.DataColumn.ColumnName%2A>屬性。 當<xref:System.Windows.Forms.DataGridTableStyle> ，沒有任何資料行樣式加入至<xref:System.Windows.Forms.DataGrid>控制項繫結至有效的資料來源，和<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>該資料表樣式的屬性設定為有效<xref:System.Data.DataTable.TableName%2A>屬性、 集合<xref:System.Windows.Forms.DataGridColumnStyle>為該資料表樣式建立的物件。 每個<xref:System.Data.DataColumn>中找到<xref:System.Data.DataTable.Columns%2A>集合<xref:System.Data.DataTable>，對應<xref:System.Windows.Forms.DataGridColumnStyle>加入至<xref:System.Windows.Forms.GridColumnStylesCollection>。 <xref:System.Windows.Forms.GridColumnStylesCollection>存取透過<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性<xref:System.Windows.Forms.DataGridTableStyle>。 加入或刪除從格線使用資料行<xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A>或<xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A>方法<xref:System.Windows.Forms.GridColumnStylesCollection>。 如需詳細資訊，請參閱[How to︰ 將資料表和資料行加入 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)和[How to︰ 刪除或隱藏 Windows Form DataGrid 控制項中的資料行](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)。  
  
 資料行類型的集合可以用擴充<xref:System.Windows.Forms.DataGridColumnStyle>類別具有豐富格式化和編輯功能。 所有的資料行型別繼承自<xref:System.Windows.Forms.DataGridColumnStyle>基底類別。 建立的類別取決於<xref:System.Data.DataColumn.DataType%2A>屬性<xref:System.Data.DataColumn>從中<xref:System.Web.UI.WebControls.DataGridColumn>為基礎。 例如， <xref:System.Data.DataColumn>具有其<xref:System.Data.DataColumn.DataType%2A>屬性設定為<xref:System.Boolean>相關聯<xref:System.Windows.Forms.DataGridBoolColumn>。 下表針對每個資料行類型進行說明。  
  
|資料行型別|說明|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|接受並顯示資料為格式化或未格式化的字串。 編輯功能是相同的編輯在簡單資料<xref:System.Windows.Forms.TextBox>。 繼承自<xref:System.Windows.Forms.DataGridColumnStyle>。|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|接受並顯示 `true`、`false` 和 null 值。 繼承自<xref:System.Windows.Forms.DataGridColumnStyle>。|  
  
 按兩下資料行的右邊緣會調整資料行的大小，以顯示其完整的標題和最寬項目。  
  
## <a name="table-styles-and-column-styles"></a>資料表樣式和資料行樣式  
 一旦您已建立的預設格式<xref:System.Windows.Forms.DataGrid>控制項，您可以自訂某些資料表顯示資料格內時要使用的色彩。  
  
 這藉由建立的執行個體<xref:System.Windows.Forms.DataGridTableStyle>類別。 資料表樣式會指定特定的資料表，不同的預設格式設定的格式<xref:System.Windows.Forms.DataGrid>控制項本身。 每個資料表一次只能有一個為其定義的資料表樣式。  
  
 有時候，您會希望特定資料行的外觀，不同於特定資料表的其餘資料行。 您可以使用，以建立一組自訂的資料行樣式<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>屬性。  
  
 資料行樣式與資料集中的資料行相關，就像資料表樣式與資料表相關。 就像每個資料表一次只能有一個為其定義的資料表樣式，因此，在特定資料表樣式中，每個資料行也只能有一個為其定義的資料行樣式。 此關聯性中的資料行定義<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>屬性。  
  
 如果您已經建立資料表樣式，但未加入資料行樣式，在執行階段建立表單和格線時，[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 將會加入預設資料行樣式。 不過，如果您已經建立資料表樣式，並加入任何資料行樣式，[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 將不會建立任何資料行樣式。 此外，您也需要定義資料行樣式，並為它們指派對應名稱，使您想要資料行出現在格線中。  
  
 因為您藉由指派資料行樣式給資料行，指定將哪些資料行內含在資料格中，但沒有任何資料行樣式已指派給資料行，所以您包含資料集中未顯示在格線內的資料行。 不過，因為資料行內含在資料集中，所以您可以用程式設計方式來編輯未顯示的資料。  
  
> [!NOTE]
>  一般而言，要先建立資料行樣式，並將其加入資料行樣式集合中，然後再將資料表樣式加入資料表樣式集合中。 當您將空的資料表樣式加入集合中時，會自動為您產生資料行樣式。 因此，將會擲回例外狀況如果您嘗試加入具有重複的新資料行樣式<xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A>資料行樣式集合中的值。  
>   
>  有時候，您會想要在許多資料行之間，只調整一個資料行；例如，資料集包含 50 個資料行，而您只想要其中 49 個。 在此情況下，將所有 50 個資料行匯入，再以程式設計方式移除其中一個，會比以程式設計方式，將 49 個您想要的資料行一一加入容易。  
  
## <a name="formatting"></a>格式化  
 格式設定套用至<xref:System.Windows.Forms.DataGrid>控制項包括框線樣式、 格線樣式、 字型、 標題屬性、 資料對齊和資料列之間更改背景色彩。 如需詳細資訊，請參閱[如何︰ 格式化 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)。  
  
## <a name="events"></a>事件  
 除了一般控制項事件例如<xref:System.Windows.Forms.Control.MouseDown>， <xref:System.Windows.Forms.Control.Enter>，和<xref:System.Windows.Forms.DataGrid.Scroll>、 <xref:System.Windows.Forms.DataGrid>控制項支援在格線內編輯和巡覽的相關事件。 <xref:System.Windows.Forms.DataGrid.CurrentCell%2A>屬性會決定選取哪一個儲存格。 <xref:System.Windows.Forms.DataGrid.CurrentCellChanged>使用者瀏覽至新的儲存格時，會引發事件。 當使用者巡覽至新的資料表，可透過父子式關聯性，<xref:System.Windows.Forms.DataGrid.Navigate>就會引發事件。 <xref:System.Windows.Forms.DataGrid.BackButtonClick>當使用者按一下 [上一頁] 按鈕，當使用者在檢視子資料表中，會引發事件和<xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick>按一下顯示/隱藏父資料列圖示時，會引發事件。  
  
## <a name="see-also"></a>另請參閱  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [如何︰ 將 Windows Form DataGrid 控制項繫結至資料來源](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)   
 [如何︰ 將資料表和資料行加入 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)   
 [如何︰ 刪除或隱藏資料行，在 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)   
 [如何︰ 格式化 Windows Form DataGrid 控制項](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)