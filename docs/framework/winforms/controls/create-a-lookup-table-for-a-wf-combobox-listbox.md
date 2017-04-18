---
title: "如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表 | Microsoft Docs"
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
  - "CheckedListBox 控制項 [Windows Form], 建立查閱資料表"
  - "下拉式方塊, 查閱資料表"
  - "ComboBox 控制項 [Windows Form], 查閱資料表"
  - "清單方塊, 查閱資料表"
  - "ListBox 控制項 [Windows Form], 建立查閱資料表"
  - "ListBox 控制項 [Windows Form], 查閱資料表"
  - "查閱資料表"
  - "查閱資料表, 為控制項建立"
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 如何：為 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項建立查閱資料表
在 Windows Form 上以方便使用的格式來顯示資料，但以對程式更有意義的格式來存放資料，這樣的做法有時候相當實用。  例如，食品的訂單表單可能會在清單方塊中依名稱來顯示功能表項目。  但是，記錄訂單的資料表則會包含代表食品的唯一 ID 編號。  下表將顯示如何存放並顯示食品訂單表單資料的範例。  
  
### OrderDetailsTable  
  
|OrderID|ItemID|Quantity|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### ItemTable  
  
|ID|名稱|  
|--------|--------|  
|12|馬鈴薯|  
|13|雞肉|  
  
 在這個案例中，其中一個資料表 OrderDetailsTable 會儲存與顯示和儲存有關的實質資訊。  但為節省空間，它是以隱晦的方式來設計的。  另一個資料表 ItemTable 則只包含與外觀相關的資訊，也就是哪個 ID 編號等於哪個食物名稱，這與實質食品訂單毫無關係。  
  
 ItemTable 可透過三個屬性連接至 <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox> 或 <xref:System.Windows.Forms.CheckedListBox> 控制項。   `DataSource`  屬性包含這個資料表的名稱。   `DisplayMember` 屬性包含要顯示在控制項 \(食品名稱\) 中的該資料表的資料行。   `ValueMember`  屬性包含該資料表中具有儲存資訊 \(ID 編號\) 的資料行。  
  
 OrderDetailsTable 是由它的繫結集合 \(透過 <xref:System.Windows.Forms.Control.DataBindings%2A> 屬性存取\) 連接到控制項。  當您將繫結物件加入集合時，便是將控制項屬性連接到資料來源 \(OrderDetailsTable\) 中的特定資料成員 \(ID 編號的資料行\)。  當在控制項中進行選取時，這個資料表就是表單輸入儲存之處。  
  
### 若要建立查閱資料表  
  
1.  將 <xref:System.Windows.Forms.ComboBox>、<xref:System.Windows.Forms.ListBox> 或 <xref:System.Windows.Forms.CheckedListBox> 控制項加入表單。  
  
2.  連接到您的資料來源。  
  
3.  在兩個資料表之間建立資料關聯。  請參閱 [DataRelation 物件簡介](../Topic/Introduction%20to%20DataRelation%20Objects.md)。  
  
4.  設定下列屬性。  您可以在程式碼或設計工具中設定這些屬性。  
  
    |屬性|設定值|  
    |--------|---------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|資料表，其中包含哪個 ID 編號對應於哪個項目的相關資訊。  在前一個案例中就是  `ItemTable`。|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|想要在控制項中顯示的資料來源資料表之資料行。  在前一個案例中就是  `"Name"`  \(在程式碼中設定時需要使用引號\)。|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|包含儲存資訊的資料來源資料表之資料行。  在前一個案例中就是  `"ID"`  \(在程式碼中設定時需要使用引號\)。|  
  
5.  在程序中，呼叫 <xref:System.Windows.Forms.ControlBindingsCollection> 類別的 <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> 方法，藉此將控制項的 <xref:System.Windows.Forms.ListControl.SelectedValue%2A> 屬性繫結至記錄表單輸入的資料表。  您也可以在 \[屬性\] 視窗中存取控制項的 <xref:System.Windows.Forms.Control.DataBindings%2A> 屬性，即可在設計工具中執行這項工作，而不是在程式碼中。  在前一個案例中就是  `OrderDetailsTable`，且資料行是  `"ItemID"`。  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
  
    ```  
  
## 請參閱  
 [資料繫結和 Windows Form](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)   
 [ListBox 控制項概觀](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)   
 [ComboBox 控制項概觀](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)   
 [CheckedListBox 控制項概觀](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)   
 [用來列出選項的 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)