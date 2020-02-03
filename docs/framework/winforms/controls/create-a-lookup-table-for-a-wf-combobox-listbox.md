---
title: 為 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表
ms.date: 03/30/2017
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
ms.openlocfilehash: 4bbbc66a56c7ce269c2dabd593db88f96907d755
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737364"
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表
在 Windows Form 上以方便使用的格式來顯示資料，但以對程式更有意義的格式來存放資料，這樣的做法有時候相當實用。 例如，食品的訂單表單可能會在清單方塊中依名稱來顯示功能表項目。 但是，記錄訂單的資料表則會包含代表食品的唯一 ID 編號。 下表將顯示如何存放並顯示食品訂單表單資料的範例。  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|ItemID|數量|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|名稱|  
|--------|----------|  
|12|馬鈴薯|  
|13|雞肉|  
  
 在此案例中，一個資料表**OrderDetailsTable**會儲存您關心顯示和儲存的實際資訊。 但為節省空間，它是以隱晦的方式來設計的。 另一個資料表**ItemTable**只包含與外觀相關的資訊，其識別碼等於哪個食物名稱，而不是實際食物訂單的任何值。  
  
 **ItemTable**會透過三個屬性連接到 <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox>或 <xref:System.Windows.Forms.CheckedListBox> 控制項。 `DataSource` 屬性包含此資料表的名稱。 `DisplayMember` 屬性包含您想要在控制項中顯示之資料表的資料行（食物名稱）。 `ValueMember` 屬性包含該資料表的資料行，其中含有儲存的資訊（ID 編號）。  
  
 **OrderDetailsTable**是由其系結集合（透過 <xref:System.Windows.Forms.Control.DataBindings%2A> 屬性來存取）連接到控制項。 當您將系結物件新增至集合時，您會將控制項屬性連接至資料來源（ **OrderDetailsTable**）中的特定資料成員（識別碼數位資料行）。 當在控制項中進行選取時，這個資料表就是表單輸入儲存之處。  
  
### <a name="to-create-a-lookup-table"></a>若要建立查閱資料表  
  
1. 將 <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox> 或 <xref:System.Windows.Forms.CheckedListBox> 控制項加入表單。  
  
2. 連接到您的資料來源。  
  
3. 在兩個資料表之間建立資料關聯。 請參閱[DataRelation 物件簡介](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0k21zcyx(v=vs.120))。  
  
4. 設定下列屬性。 您可以在程式碼或設計工具中設定這些屬性。  
  
    |屬性|設定|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|資料表，其中包含哪個 ID 編號對應於哪個項目的相關資訊。 在先前的案例中，這是 `ItemTable`。|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|想要在控制項中顯示的資料來源資料表之資料行。 在先前的案例中，這是 `"Name"` （在程式碼中設定，請使用引號）。|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|包含儲存資訊的資料來源資料表之資料行。 在先前的案例中，這是 `"ID"` （在程式碼中設定，請使用引號）。|  
  
5. 在程序中，呼叫 <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> 類別的 <xref:System.Windows.Forms.ControlBindingsCollection> 方法，藉此將控制項的 <xref:System.Windows.Forms.ListControl.SelectedValue%2A> 屬性繫結至記錄表單輸入的資料表。 您也可以在設計工具中執行這項操作，而不是在程式碼中，存取 [**屬性**] 視窗中的控制項的 [<xref:System.Windows.Forms.Control.DataBindings%2A>] 屬性。 在前一個案例中，這是 `OrderDetailsTable`，而資料行是 `"ItemID"`。  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>另請參閱

- [資料繫結和 Windows Forms](../data-binding-and-windows-forms.md)
- [ListBox 控制項概觀](listbox-control-overview-windows-forms.md)
- [ComboBox 控制項概觀](combobox-control-overview-windows-forms.md)
- [CheckedListBox 控制項概觀](checkedlistbox-control-overview-windows-forms.md)
- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)
