---
title: HOW TO：判斷 Windows Form CheckedListBox 控制項中選取的項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 2936a64338f47107b11b5f6eb85c5e94707bf926
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707959"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>HOW TO：判斷 Windows Form CheckedListBox 控制項中選取的項目
呈現 Windows Forms 中的資料時<xref:System.Windows.Forms.CheckedListBox>控制項，您可以請逐一查看集合中儲存<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>屬性或逐步執行清單使用<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法，以判斷選取的項目。 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法會將項目索引編號，做為其引數並傳回`true`或`false`。 相對於您預期，<xref:System.Windows.Forms.ListBox.SelectedItems%2A>和<xref:System.Windows.Forms.ListBox.SelectedIndices%2A>屬性不會決定選取哪一個項目，它們會判斷哪些項目會反白顯示。  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>若要判斷 CheckedListBox 控制項中選取的項目  
  
1.  逐一查看<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>開始 0，因為集合是以零為起始的集合。 請注意，這個方法會提供您的項目編號的清單中選取項目，不是整個清單。 所以如果在清單中的第一個項目不會檢查第二個項目已選取，下列程式碼會顯示類似的文字 」 已檢查的項目 1 = MyListItem2"。  
  
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
  
2.  您可以逐步<xref:System.Windows.Forms.CheckedListBox.Items%2A>集合，從 0 開始因為集合是以零起始，並呼叫<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法，每個項目。 請注意，這個方法會提供您的項目編號在整體的清單中，因此如果中的第一個項目不會檢查清單和第二個項目已選取，它會顯示類似 「 項目 2 = MyListItem2"。  
  
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
- [用來列出選項的 Windows Forms 控制項](windows-forms-controls-used-to-list-options.md)
