---
title: HOW TO：在 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定項目
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
ms.openlocfilehash: fbdd9168fe286823db7cf066ae0f821b8db88ecb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324522"
---
# <a name="how-to-access-specific-items-in-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="3df05-102">HOW TO：在 Windows Forms 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定項目</span><span class="sxs-lookup"><span data-stu-id="3df05-102">How to: Access Specific Items in a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="3df05-103">存取 Windows Form 下拉式方塊、 清單方塊中或選取的清單方塊中的特定項目是必要的工作。</span><span class="sxs-lookup"><span data-stu-id="3df05-103">Accessing specific items in a Windows Forms combo box, list box, or checked list box is an essential task.</span></span> <span data-ttu-id="3df05-104">它可讓您以程式設計方式決定功能的清單中，在任何給定的位置。</span><span class="sxs-lookup"><span data-stu-id="3df05-104">It enables you to programmatically determine what is in a list, at any given position.</span></span>  
  
### <a name="to-access-a-specific-item"></a><span data-ttu-id="3df05-105">若要存取特定的項目</span><span class="sxs-lookup"><span data-stu-id="3df05-105">To access a specific item</span></span>  
  
1. <span data-ttu-id="3df05-106">查詢`Items`使用特定的項目索引的集合：</span><span class="sxs-lookup"><span data-stu-id="3df05-106">Query the `Items` collection using the index of the specific item:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3df05-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3df05-107">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="3df05-108">用來列出選項的 Windows Form 控制項</span><span class="sxs-lookup"><span data-stu-id="3df05-108">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)
