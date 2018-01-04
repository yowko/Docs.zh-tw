---
title: "如何：判斷 Windows Form CheckedListBox 控制項中的已核取項目"
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
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63960740b2fc0cb2c96f9a853480f37857c7901b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>如何：判斷 Windows Form CheckedListBox 控制項中的已核取項目
呈現 Windows Form 中的資料時<xref:System.Windows.Forms.CheckedListBox>控制項，您可以請逐一查看集合中儲存<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>屬性或清單使用逐步執行<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法來判斷哪些項目會檢查。 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法會採用做為其引數的項目索引編號，並傳回`true`或`false`。 Fci 不如預期，<xref:System.Windows.Forms.ListBox.SelectedItems%2A>和<xref:System.Windows.Forms.ListBox.SelectedIndices%2A>屬性不會決定會檢查哪些項目，它們會判斷哪些項目會反白顯示。  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>若要判斷 CheckedListBox 控制項中的選取項目  
  
1.  逐一查看<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>集合，從 0 開始的因為集合是以零為起始。 請注意，這個方法會提供您的項目編號在清單中選取的項目，不是整個清單。 所以如果在清單中的第一個項目不會檢查第二個項目已選取，下列程式碼會顯示文字為 「 已檢查的項目 1 = MyListItem2"。  
  
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
       for(int x = 0; x <= checkedListBox1.CheckedItems.Count - 1 ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
    MessageBox.Show (s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x <= checkedListBox1->CheckedItems->Count - 1; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - 或 -  
  
2.  逐步執行<xref:System.Windows.Forms.CheckedListBox.Items%2A>集合，從 0 開始的因為集合是以零起始，並呼叫<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>每個項目的方法。 請注意，這個方法會提供您的項目編號在整體清單中，因此如果中的第一個項目不會檢查清單和檢查第二個項目，它會顯示類似 「 項目 2 = MyListItem2"。  
  
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
 [用來列出選項的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
