---
title: "如何：從 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "CheckedListBox 控制項 [Windows Form], 加入和移除項目"
  - "下拉式方塊, 加入項目"
  - "下拉式方塊, 移除項目"
  - "ComboBox 控制項 [Windows Form], 加入和移除項目"
  - "清單方塊, 加入項目"
  - "清單方塊, 移除項目"
  - "ListBox 控制項 [Windows Form], 加入和移除項目"
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：從 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目
由於 Windows Form 下拉式方塊、清單方塊或選取的清單方塊可繫結至不同的資料來源，因此您可以使用多種方法將項目加入至這些控制項。  不過，本主題將示範最簡單的方法並且不需進行資料繫結 \(Data Binding\)。  顯示的項目通常是字串；不過，您也可使用任何物件。  顯示在控制項中的文字為物件的 `ToString`  方法所傳回的值。  
  
### 若要加入項目  
  
1.  使用 `ObjectCollection` 類別的 `Add` 方法，將字串或物件加入清單。  藉由使用 `Items`  屬性來參考集合：  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     \-或\-  
  
2.  使用 `Insert`  方法，在清單中的目標點上插入字串或物件：  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     \-或\-  
  
3.  將整個陣列指派給 `Items`  集合：  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### 若要移除項目  
  
1.  呼叫`Remove` 或`RemoveAt` 方法來刪除項目。  
  
     `Remove` 有引數可指定要移除的項目。`RemoveAt` 會移除具有指定索引編號的項目。  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### 若要移除所有的項目  
  
1.  呼叫 `Clear` 方法，從集合移除所有項目：  
  
    ```vb  
    ListBox1.Items.Clear()  
  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## 請參閱  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms.CheckedListBox>   
 [如何：排序 Windows Form 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [何時使用 Windows Form ComboBox 取代 ListBox](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)   
 [用來列出選項的 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)