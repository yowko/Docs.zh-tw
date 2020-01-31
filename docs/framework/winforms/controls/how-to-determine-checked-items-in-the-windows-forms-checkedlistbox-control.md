---
title: 判斷 CheckedListBox 控制項中的已核取專案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5854f7e6be759daeb604458ea8554d3c98ed39c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743248"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>如何：判斷 Windows Form CheckedListBox 控制項中的已核取項目
在 Windows Forms <xref:System.Windows.Forms.CheckedListBox> 控制項中呈現資料時，您可以逐一查看儲存在 <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> 屬性中的集合，或使用 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> 方法來逐步執行清單，以判斷要檢查哪些專案。 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> 方法會接受專案索引編號做為其引數，並傳回 `true` 或 `false`。 與您預期的相反，<xref:System.Windows.Forms.ListBox.SelectedItems%2A> 和 <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> 屬性不會決定要檢查哪些專案;它們會決定要反白顯示哪些專案。  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>若要判斷 CheckedListBox 控制項中的已核取專案  
  
1. 逐一查看 <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> 的集合，從0開始，因為集合是以零為基底。 請注意，這個方法會提供已核取專案清單中的專案編號，而不是整體清單。 因此，如果未核取清單中的第一個專案，而第二個專案已核取，則下列程式碼會顯示像是「已檢查的專案 1 = MyListItem2」的文字。  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - 或 -  
  
2. 逐步執行 <xref:System.Windows.Forms.CheckedListBox.Items%2A> 集合，從0開始，因為集合是以零為基底，並針對每個專案呼叫 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> 方法。 請注意，這個方法會提供您 [整體] 清單中的專案編號，因此，如果未核取清單中的第一個專案，而第二個專案已核取，則會顯示類似 "Item 2 = MyListItem2" 的內容。  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a>請參閱

- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)
