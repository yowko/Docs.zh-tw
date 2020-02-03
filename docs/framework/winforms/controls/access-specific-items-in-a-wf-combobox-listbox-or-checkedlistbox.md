---
title: 存取 ComboBox、ListBox 或 CheckedListBox 控制項中的特定專案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ComboBox control [Windows Forms], accessing items
- ListBox control [Windows Forms], returning item information
- list boxes [Windows Forms], accessing items
- ListBox control [Windows Forms], accessing items
- combo boxes [Windows Forms], accessing items
- CheckedListBox control [Windows Forms], accessing items
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
ms.openlocfilehash: 67673ec7f136f1466d4fd091e691324c53e7de06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746331"
---
# <a name="how-to-access-specific-items-in-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="8fd9a-102">如何：在 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定的項目</span><span class="sxs-lookup"><span data-stu-id="8fd9a-102">How to: Access Specific Items in a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="8fd9a-103">存取 Windows Forms 下拉式方塊、清單方塊或 [已核取] 清單方塊中的特定專案是必要的工作。</span><span class="sxs-lookup"><span data-stu-id="8fd9a-103">Accessing specific items in a Windows Forms combo box, list box, or checked list box is an essential task.</span></span> <span data-ttu-id="8fd9a-104">它可讓您以程式設計方式判斷清單中任何指定位置的內容。</span><span class="sxs-lookup"><span data-stu-id="8fd9a-104">It enables you to programmatically determine what is in a list, at any given position.</span></span>  
  
### <a name="to-access-a-specific-item"></a><span data-ttu-id="8fd9a-105">存取特定專案</span><span class="sxs-lookup"><span data-stu-id="8fd9a-105">To access a specific item</span></span>  
  
1. <span data-ttu-id="8fd9a-106">使用特定專案的索引來查詢 `Items` 集合：</span><span class="sxs-lookup"><span data-stu-id="8fd9a-106">Query the `Items` collection using the index of the specific item:</span></span>  
  
    ```vb  
    Private Function GetItemText(i As Integer) As String  
       ' Return the text of the item using the index:  
       Return ComboBox1.Items(i).ToString  
    End Function  
    ```  
  
    ```csharp  
    private string GetItemText(int i)  
    {  
       // Return the text of the item using the index:  
       return (comboBox1.Items[i].ToString());  
    }  
    ```  
  
    ```cpp  
    private:  
       String^ GetItemText(int i)  
       {  
          // Return the text of the item using the index:  
          return (comboBox1->Items->Item[i]->ToString());  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8fd9a-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fd9a-107">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="8fd9a-108">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="8fd9a-108">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
