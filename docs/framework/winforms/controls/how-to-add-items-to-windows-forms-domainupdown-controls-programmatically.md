---
title: 以程式設計方式將項目新增至 DomainUpDown 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 2e9f51fa051bf9b62e95f289db97bffd83450036
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745588"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>如何：以程式設計的方式將項目加入至 Windows Form DomainUpDown 控制項
您可以在程式碼中將專案新增至 Windows Forms <xref:System.Windows.Forms.DomainUpDown> 控制項。 呼叫 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> 類別的 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> 或 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> 方法，將專案加入至控制項的 <xref:System.Windows.Forms.DomainUpDown.Items%2A> 屬性。 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> 方法會將專案新增至集合結尾，而 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> 方法會在指定的位置加入專案。  
  
### <a name="to-add-a-new-item"></a>若要加入新專案  
  
1. 使用 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> 方法，將專案加入至專案清單的結尾。  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     -或-  
  
2. 使用 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> 方法，將專案插入清單中指定的位置。  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [DomainUpDown 控制項](domainupdown-control-windows-forms.md)
- [DomainUpDown 控制項概觀](domainupdown-control-overview-windows-forms.md)
