---
title: "如何：從 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目"
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
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: faf0422db9915806442ab96759d63e15ff98b813
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="92970-102">如何：從 Windows Form 的 ComboBox、ListBox 或 CheckedListBox 控制項加入或移除項目</span><span class="sxs-lookup"><span data-stu-id="92970-102">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="92970-103">可以加入至 Windows Form 下拉式方塊、 清單方塊中，或檢查清單方塊中的各種不同的方式，因為這些控制項可以繫結至各種資料來源項目。</span><span class="sxs-lookup"><span data-stu-id="92970-103">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="92970-104">不過，本主題會示範最簡單的方法，並需要沒有資料繫結。</span><span class="sxs-lookup"><span data-stu-id="92970-104">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="92970-105">顯示的項目通常是字串。不過，您可以使用任何物件。</span><span class="sxs-lookup"><span data-stu-id="92970-105">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="92970-106">顯示在控制項中的文字是由物件所傳回的值`ToString`方法。</span><span class="sxs-lookup"><span data-stu-id="92970-106">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="92970-107">若要加入的項目</span><span class="sxs-lookup"><span data-stu-id="92970-107">To add items</span></span>  
  
1.  <span data-ttu-id="92970-108">使用將字串或物件加入至清單`Add`方法`ObjectCollection`類別。</span><span class="sxs-lookup"><span data-stu-id="92970-108">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="92970-109">使用參考集合`Items`屬性：</span><span class="sxs-lookup"><span data-stu-id="92970-109">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="92970-110">或 -</span><span class="sxs-lookup"><span data-stu-id="92970-110">or -</span></span>  
  
2.  <span data-ttu-id="92970-111">插入的字串或物件在清單中所需的時間點`Insert`方法：</span><span class="sxs-lookup"><span data-stu-id="92970-111">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="92970-112">或 -</span><span class="sxs-lookup"><span data-stu-id="92970-112">or -</span></span>  
  
3.  <span data-ttu-id="92970-113">指派至整個陣列`Items`集合：</span><span class="sxs-lookup"><span data-stu-id="92970-113">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="92970-114">若要移除項目</span><span class="sxs-lookup"><span data-stu-id="92970-114">To remove an item</span></span>  
  
1.  <span data-ttu-id="92970-115">呼叫`Remove`或`RemoveAt`方法，以刪除項目。</span><span class="sxs-lookup"><span data-stu-id="92970-115">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="92970-116">`Remove`有一個引數，指定要移除的項目。`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="92970-116">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="92970-117">移除具有指定的索引編號的項目。</span><span class="sxs-lookup"><span data-stu-id="92970-117">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="92970-118">若要移除所有項目</span><span class="sxs-lookup"><span data-stu-id="92970-118">To remove all items</span></span>  
  
1.  <span data-ttu-id="92970-119">呼叫`Clear`方法，以從集合中移除所有項目：</span><span class="sxs-lookup"><span data-stu-id="92970-119">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="92970-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="92970-120">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="92970-121">操作說明：排序 Windows Forms 中 ComboBox、ListBox 或 CheckedListBox 控制項的內容</span><span class="sxs-lookup"><span data-stu-id="92970-121">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="92970-122">何時使用 Windows Forms ComboBox 取代 ListBox</span><span class="sxs-lookup"><span data-stu-id="92970-122">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="92970-123">用來列出選項的 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="92970-123">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
