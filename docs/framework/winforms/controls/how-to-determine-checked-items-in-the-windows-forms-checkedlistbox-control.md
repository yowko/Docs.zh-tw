---
title: 確定選中清單方塊中檢查的專案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5d93a63e9c1c6aae91ecfe83590c59450a565afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182196"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>如何：判斷 Windows Form CheckedListBox 控制項中的已核取項目
在 Windows 表單<xref:System.Windows.Forms.CheckedListBox>控制項中顯示資料時，可以遍遍存儲在<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>屬性中的集合，或者使用<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法單一步驟清單以確定檢查哪些項。 該方法<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>以項索引號作為其參數，並返回`true`或`false`。 與您可能期望的相反，和<xref:System.Windows.Forms.ListBox.SelectedItems%2A><xref:System.Windows.Forms.ListBox.SelectedIndices%2A>屬性不確定哪些項被檢查;相反，屬性不會確定哪些項被檢查。它們確定突出顯示哪些項。  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>確定選中的"檢查清單"控制項中的已檢查項目  
  
1. 反覆運算集合，<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>從 0 開始，因為集合是零基的。 請注意，此方法將為您提供已檢查項目清單中的物料編號，而不是整個清單中的專案編號。 因此，如果未選中清單中的第一項，並且檢查了第二項，則下面的代碼將顯示"已檢查的專案 1 = MyListItem2"之類的文本。  
  
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
  
2. 單一步驟<xref:System.Windows.Forms.CheckedListBox.Items%2A>集合，從 0 開始，因為集合是零基的，並<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>調用每個項的方法。 請注意，此方法將為您提供整個清單中的專案編號，因此，如果未選中清單中的第一個專案，並且檢查了第二個專案，它將顯示類似"專案 2 = MyListItem2"的內容。  
  
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
  
## <a name="see-also"></a>另請參閱

- [用來列出選項的 Windows Form 控制項](windows-forms-controls-used-to-list-options.md)
