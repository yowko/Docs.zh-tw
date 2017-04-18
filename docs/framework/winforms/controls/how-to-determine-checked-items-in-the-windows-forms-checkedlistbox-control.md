---
title: "如何：判斷 Windows Form CheckedListBox 控制項中的已核取項目 | Microsoft Docs"
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
  - "核取方塊, 判斷核取狀態"
  - "CheckedListBox 控制項 [Windows Form], 判斷核取狀態"
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 如何：判斷 Windows Form CheckedListBox 控制項中的已核取項目
當使用 Windows Form <xref:System.Windows.Forms.CheckedListBox> 控制項顯示資料時，您可以逐一查看儲存在 <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> 屬性中的集合，或使用 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> 方法來逐步執行清單，以決定核取了哪些項目。  <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> 方法會將項目索引編號當做它的引數，並傳回 `true` 或 `false`。  <xref:System.Windows.Forms.ListBox.SelectedItems%2A> 和 <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> 屬性不會決定要核取哪些項目 \(這與您預期的可能相反\)，它們只會決定要反白顯示的項目。  
  
### 若要在 CheckedListBox 控制項中決定核取的項目  
  
1.  因為集合是以零起始，所以從 0 開始逐一查看 <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> 集合。  請注意，這個方法會提供您核取項目清單 \(而不是整個清單\) 的項目編號。  所以，如果清單中的第一個項目沒有被選取而第二個項目有被選取，則下列的程式碼會顯示類似 "Checked Item 1 \= MyListItem2" 的文字。  
  
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
  
     \-或\-  
  
2.  因為 <xref:System.Windows.Forms.CheckedListBox.Items%2A> 集合是以零起始的，所以從 0 開始逐步執行該集合，並呼叫每個項目的 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> 方法。  請注意，這個方法會提供您整個清單中的項目編號，所以如果還沒有檢查清單中的第一個項目就檢查第二個項目，就會顯示像是 "Item 2 \= MyListItem2" 的訊息。  
  
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
  
## 請參閱  
 [用來列出選項的 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)