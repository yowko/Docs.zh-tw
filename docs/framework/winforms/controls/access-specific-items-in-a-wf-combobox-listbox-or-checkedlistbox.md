---
title: "如何：在 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定的項目"
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
- ComboBox control [Windows Forms], accessing items
- ListBox control [Windows Forms], returning item information
- list boxes [Windows Forms], accessing items
- ListBox control [Windows Forms], accessing items
- combo boxes [Windows Forms], accessing items
- CheckedListBox control [Windows Forms], accessing items
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 400e367581ea773d88320e593aa525d812ea0238
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-specific-items-in-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="099ed-102">如何：在 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項中存取特定的項目</span><span class="sxs-lookup"><span data-stu-id="099ed-102">How to: Access Specific Items in a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="099ed-103">存取 Windows Form 下拉式方塊、 清單方塊中或核取的清單方塊中的特定項目是必要的工作。</span><span class="sxs-lookup"><span data-stu-id="099ed-103">Accessing specific items in a Windows Forms combo box, list box, or checked list box is an essential task.</span></span> <span data-ttu-id="099ed-104">它可讓您以程式設計方式判斷為何在清單中，在任何給定的位置。</span><span class="sxs-lookup"><span data-stu-id="099ed-104">It enables you to programmatically determine what is in a list, at any given position.</span></span>  
  
### <a name="to-access-a-specific-item"></a><span data-ttu-id="099ed-105">若要存取特定的項目</span><span class="sxs-lookup"><span data-stu-id="099ed-105">To access a specific item</span></span>  
  
1.  <span data-ttu-id="099ed-106">查詢`Items`集合中特定項目的索引：</span><span class="sxs-lookup"><span data-stu-id="099ed-106">Query the `Items` collection using the index of the specific item:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="099ed-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="099ed-107">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="099ed-108">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="099ed-108">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
