---
title: 從 ComboBox、ListBox 或 CheckedListBox 控制項新增和移除專案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
ms.openlocfilehash: 3a83d98af42386b566b4af7bc11ff383dea8fd6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746300"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>如何：從 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目
專案可以用各種方式加入至 Windows Forms 下拉式方塊、清單方塊或已核取清單方塊，因為這些控制項可以系結至各種不同的資料來源。 不過，本主題將示範最簡單的方法，而且不需要資料系結。 顯示的專案通常是字串;不過，您可以使用任何物件。 控制項中顯示的文字是物件的 `ToString` 方法所傳回的值。  
  
### <a name="to-add-items"></a>若要加入專案  
  
1. 使用 `ObjectCollection` 類別的 `Add` 方法，將字串或物件新增至清單。 使用 `Items` 屬性來參考集合：  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - 或 -  
  
2. 使用 `Insert` 方法，將字串或物件插入清單中所需的點：  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - 或 -  
  
3. 將整個陣列指派給 `Items` 集合：  
  
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
  
### <a name="to-remove-an-item"></a>若要移除專案  
  
1. 呼叫 `Remove` 或 `RemoveAt` 方法來刪除專案。  
  
     `Remove` 有一個指定要移除之專案的引數。`RemoveAt` 移除具有指定之索引編號的專案。  
  
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
  
### <a name="to-remove-all-items"></a>移除所有專案  
  
1. 呼叫 `Clear` 方法，從集合中移除所有專案：  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [何時使用 Windows Forms ComboBox 取代 ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)
