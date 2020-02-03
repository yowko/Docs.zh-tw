---
title: 從 DomainUpDown 控制項中移除專案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: e52af5c5add4fda93e2b51c8afdb90c92e8d2f62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735764"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>如何：從 Windows Form DomainUpDown 控制項中移除項目
您可以藉由呼叫 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> 類別的 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> 或 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> 方法，從 Windows Forms <xref:System.Windows.Forms.DomainUpDown> 控制項中移除專案。 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> 方法會移除特定專案，而 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> 方法則會依其位置移除專案。  
  
### <a name="to-remove-an-item"></a>若要移除專案  
  
- 使用 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> 類別的 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> 方法，依名稱移除專案。  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     -或-  
  
- 使用 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> 方法，依其位置移除專案。  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [DomainUpDown 控制項](domainupdown-control-windows-forms.md)
- [DomainUpDown 控制項概觀](domainupdown-control-overview-windows-forms.md)
