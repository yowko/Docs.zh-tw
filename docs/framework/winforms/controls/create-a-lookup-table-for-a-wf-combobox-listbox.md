---
title: "如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f49a8fbd2cc8ffae94e4dcbbc4babf7c1137cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表
在 Windows Form 上以方便使用的格式來顯示資料，但以對程式更有意義的格式來存放資料，這樣的做法有時候相當實用。 例如，食品的訂單表單可能會在清單方塊中依名稱來顯示功能表項目。 但是，記錄訂單的資料表則會包含代表食品的唯一 ID 編號。 下表將顯示如何存放並顯示食品訂單表單資料的範例。  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|ItemID|Quantity|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|識別碼|名稱|  
|--------|----------|  
|12|馬鈴薯|  
|13|雞肉|  
  
 在此案例中，一個資料表中， **OrderDetailsTable**，儲存的實際的資訊，您可能會與顯示和儲存。 但為節省空間，它是以隱晦的方式來設計的。 另一個資料表， **ItemTable**，只包含與外觀相關的資訊有關哪個 ID 編號相當哪個食物名稱，與實質食品訂單相關的所有項目。  
  
 **ItemTable**連線到<xref:System.Windows.Forms.ComboBox>， <xref:System.Windows.Forms.ListBox>，或<xref:System.Windows.Forms.CheckedListBox>透過三個屬性的控制項。 `DataSource`屬性包含此資料表的名稱。 `DisplayMember`屬性包含您想要在控制項 （食品名稱） 中顯示該資料表的資料行。 `ValueMember`屬性包含該資料表中具有儲存的資訊 （ID 編號） 的資料行。  
  
 **OrderDetailsTable**由其繫結的集合，透過連接到控制項<xref:System.Windows.Forms.Control.DataBindings%2A>屬性。 當您將繫結物件加入集合時，便控制項屬性連接到資料來源中的特定資料成員 （ID 編號的資料行） ( **OrderDetailsTable**)。 當在控制項中進行選取時，這個資料表就是表單輸入儲存之處。  
  
### <a name="to-create-a-lookup-table"></a>若要建立查閱資料表  
  
1.  將 <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox> 或 <xref:System.Windows.Forms.CheckedListBox> 控制項加入表單。  
  
2.  連接到您的資料來源。  
  
3.  在兩個資料表之間建立資料關聯。 請參閱[DataRelation 物件簡介](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192)。  
  
4.  設定下列屬性。 您可以在程式碼或設計工具中設定這些屬性。  
  
    |屬性|設定|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|資料表，其中包含哪個 ID 編號對應於哪個項目的相關資訊。 在前述案例中，這是`ItemTable`。|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|想要在控制項中顯示的資料來源資料表之資料行。 在前述案例中，這是`"Name"`（程式碼中設定，請使用引號）。|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|包含儲存資訊的資料來源資料表之資料行。 在前述案例中，這是`"ID"`（程式碼中設定，請使用引號）。|  
  
5.  在程序中，呼叫 <xref:System.Windows.Forms.ControlBindingsCollection> 類別的 <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> 方法，藉此將控制項的 <xref:System.Windows.Forms.ListControl.SelectedValue%2A> 屬性繫結至記錄表單輸入的資料表。 您也這樣可以在程式碼，而不是在設計工具中存取控制項的<xref:System.Windows.Forms.Control.DataBindings%2A>屬性**屬性**視窗。 在前述案例中，這是`OrderDetailsTable`，與資料行是`"ItemID"`。  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>請參閱  
 [資料繫結和 Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [ListBox 控制項概觀](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [ComboBox 控制項概觀](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [CheckedListBox 控制項概觀](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [用來列出選項的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
