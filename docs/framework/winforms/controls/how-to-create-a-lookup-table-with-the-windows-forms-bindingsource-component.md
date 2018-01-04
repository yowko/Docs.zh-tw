---
title: "如何：使用 Windows Forms BindingSource 元件建立查閱資料表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 324e4ed290b98d2268dd82fa55b81deaeb849770
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a>如何：使用 Windows Forms BindingSource 元件建立查閱資料表
查閱資料表是具有資料行的資料表，而此資料行會從相關資料表的記錄中顯示資料。 在下列程序中，會使用 <xref:System.Windows.Forms.ComboBox> 控制項顯示從父資料表到子資料表具有外部索引鍵關聯性的欄位。  
  
 為了協助您設想這兩個資料表與此種關聯性，以下是父資料表和子資料表的範例：  
  
 CustomersTable (父資料表)  
  
|CustomerID|CustomerName|  
|----------------|------------------|  
|712|Paul Koch|  
|713|Tamara Johnston|  
  
 OrdersTable (子資料表)  
  
|OrderID|OrderDate|CustomerID|  
|-------------|---------------|----------------|  
|903|2004 年 2 月 12 日|712|  
|904|2004 年 2 月 13 日|713|  
  
 在此案例中，有一個資料表 CustomersTable 儲存了您想要顯示及儲存的資訊。 但為了節省空間，資料表省去了可增加明確性的資料。 另一個資料表 OrdersTable 只包含看似相關的資訊，關於哪個客戶 ID 號碼對應至哪個訂單日期和訂單 ID。 沒有提到客戶的任何姓名。  
  
 [ComboBox 控制項](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)上設定了四個重要的屬性，以供建立查閱資料表。  
  
-   <xref:System.Windows.Forms.ComboBox.DataSource%2A> 屬性包含資料表的名稱。  
  
-   <xref:System.Windows.Forms.ListControl.DisplayMember%2A> 屬性包含該資料表中您想要為控制項文字 (客戶姓名) 顯示的資料行。  
  
-   <xref:System.Windows.Forms.ListControl.ValueMember%2A> 屬性包含該資料表中具有儲存之資訊 (父資料表中的 ID 編號) 的資料行。  
  
-   <xref:System.Windows.Forms.ListControl.SelectedValue%2A> 屬性提供子資料表的查閱值 (根據 <xref:System.Windows.Forms.ListControl.ValueMember%2A>)。  
  
 以下程序向您示範如何將表單配置為查閱資料表，並將資料繫結至其控制項。 為了成功完成此這些程序，您必須要有具有外部索引鍵關聯性之父資料表和子資料表的資料來源 (如上所述)。  
  
### <a name="to-create-the-user-interface"></a>若要建立使用者介面  
  
1.  從**工具箱**，拖曳<xref:System.Windows.Forms.ComboBox>控制項拖曳至表單。  
  
     此控制項會從父資料表顯示資料行。  
  
2.  拖曳其他控制項以從子資料表顯示詳細資料。 資料表中的資料格式會決定您要選擇哪些控制項。 如需詳細資訊，請參閱[依功能區分的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)。  
  
3.  將 <xref:System.Windows.Forms.BindingNavigator> 控制項拖曳至表單上，這可讓您巡覽子資料表中的資料。  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a>連接至資料並將資料繫節至控制項  
  
1.  選取 <xref:System.Windows.Forms.ComboBox>，然後按一下 [智慧工作提示] 圖像，以顯示 [智慧工作提示] 對話方塊。  
  
2.  選取 [使用資料繫結項目]。  
  
3.  按一下 [資料來源] 下拉式方塊旁邊的箭頭。 若之前已為專案或表單設定過資料來源，則會顯示；若無設定，請完成下列步驟 (此範例使用 Northwind 範例資料庫的 Customers 及 Orders 資料表，並在引用時使用括號)。  
  
    1.  按一下 [新增專案資料來源] 以連接至資料，並建立資料來源。  
  
    2.  在 [資料來源組態精靈] 歡迎頁面上，按 [下一步]。  
  
    3.  選取 [選擇資料來源類型] 頁面中的 [資料庫]。  
  
    4.  從 [選擇資料連接] 頁面中的可用連接清單，選取資料連接。 若您想要的資料連接無法使用，請選取 [新增連接] 以建立新資料連接。  
  
    5.  按一下 [是，將連接儲存為]，將連接字串儲存至應用程式組態檔。  
  
    6.  選取要帶入應用程式中的資料庫物件。 在此情況中，請選取具有外部索引鍵關聯性的父資料表和子資料表 (例如 Customers 和 Orders)。  
  
    7.  您可以視需要更換預設資料集名稱。  
  
    8.  按一下 [ **完成**]。  
  
4.  在 [顯示成員] 下拉式方塊中，選取要顯示在下拉式方塊中的資料行名稱 (例如 ContactName)。  
  
5.  在 [值成員] 下拉式方塊中，選取要在子資料表中執行查詢作業的資料行名稱 (例如 CustomerID)。  
  
6.  在 [選取的值] 下拉式方塊中，巡覽至 [專案資料來源]，以及您剛剛建立包含父資料表及子資料表的資料集。 選取與父資料表的值成員相同的子資料表屬性 (例如 Orders.CustomerID)。 將會建立適當的 <xref:System.Windows.Forms.BindingSource>、資料集和資料表配接器元件，並加入至表單中。  
  
7.  將 <xref:System.Windows.Forms.BindingNavigator> 控制項繫結至子資料表的 <xref:System.Windows.Forms.BindingSource> (例如 `OrdersBindingSource`)。  
  
8.  從子資料表的 <xref:System.Windows.Forms.ComboBox> (例如 <xref:System.Windows.Forms.BindingNavigator>)，將 <xref:System.Windows.Forms.BindingSource> 和 `OrdersBindingSource` 以外的控制項繫結至您想要顯示的詳細資料欄位。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [ComboBox 控制項](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)  
 [將控制項繫結至 Visual Studio 中的資料](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
