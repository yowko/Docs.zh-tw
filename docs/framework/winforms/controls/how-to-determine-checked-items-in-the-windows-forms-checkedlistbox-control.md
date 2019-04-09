---
title: HOW TO：判斷 Windows Forms CheckedListBox 控制項中的已核取項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 0cfb34d058486c44ffb01e6c105134e3ca4c2175
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184674"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="4cc1e-102">HOW TO：判斷 Windows Forms CheckedListBox 控制項中的已核取項目</span><span class="sxs-lookup"><span data-stu-id="4cc1e-102">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="4cc1e-103">呈現 Windows Forms 中的資料時<xref:System.Windows.Forms.CheckedListBox>控制項，您可以請逐一查看集合中儲存<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>屬性或逐步執行清單使用<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法，以判斷選取的項目。</span><span class="sxs-lookup"><span data-stu-id="4cc1e-103">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="4cc1e-104"><xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法會將項目索引編號，做為其引數並傳回`true`或`false`。</span><span class="sxs-lookup"><span data-stu-id="4cc1e-104">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="4cc1e-105">相對於您預期，<xref:System.Windows.Forms.ListBox.SelectedItems%2A>和<xref:System.Windows.Forms.ListBox.SelectedIndices%2A>屬性不會決定選取哪一個項目，它們會判斷哪些項目會反白顯示。</span><span class="sxs-lookup"><span data-stu-id="4cc1e-105">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="4cc1e-106">若要判斷 CheckedListBox 控制項中選取的項目</span><span class="sxs-lookup"><span data-stu-id="4cc1e-106">To determine checked items in a CheckedListBox control</span></span>  
  
1.  <span data-ttu-id="4cc1e-107">逐一查看<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>開始 0，因為集合是以零為起始的集合。</span><span class="sxs-lookup"><span data-stu-id="4cc1e-107">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="4cc1e-108">請注意，這個方法會提供您的項目編號的清單中選取項目，不是整個清單。</span><span class="sxs-lookup"><span data-stu-id="4cc1e-108">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="4cc1e-109">所以如果在清單中的第一個項目不會檢查第二個項目已選取，下列程式碼會顯示類似的文字 」 已檢查的項目 1 = MyListItem2"。</span><span class="sxs-lookup"><span data-stu-id="4cc1e-109">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
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
  
     - <span data-ttu-id="4cc1e-110">或 -</span><span class="sxs-lookup"><span data-stu-id="4cc1e-110">or -</span></span>  
  
2.  <span data-ttu-id="4cc1e-111">您可以逐步<xref:System.Windows.Forms.CheckedListBox.Items%2A>集合，從 0 開始因為集合是以零起始，並呼叫<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>方法，每個項目。</span><span class="sxs-lookup"><span data-stu-id="4cc1e-111">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="4cc1e-112">請注意，這個方法會提供您的項目編號在整體的清單中，因此如果中的第一個項目不會檢查清單和第二個項目已選取，它會顯示類似 「 項目 2 = MyListItem2"。</span><span class="sxs-lookup"><span data-stu-id="4cc1e-112">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4cc1e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cc1e-113">See also</span></span>

- [<span data-ttu-id="4cc1e-114">用來列出選項的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="4cc1e-114">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
