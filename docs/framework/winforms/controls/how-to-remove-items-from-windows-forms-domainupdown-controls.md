---
title: HOW TO：從 Windows Forms DomainUpDown 控制項中移除項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: f56bc2b7b7b8a783ac298b220c83281f38da29da
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662344"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>HOW TO：從 Windows Forms DomainUpDown 控制項中移除項目
您可以移除 Windows Form 中的項目<xref:System.Windows.Forms.DomainUpDown>控制項，藉由呼叫<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>或是<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>方法<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>類別。 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>方法移除特定的項目，雖然<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>方法移除項目依其位置。  
  
### <a name="to-remove-an-item"></a>若要移除的項目  
  
- 使用<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>方法的<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>類別名稱中移除項目。  
  
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
  
- 使用<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>移除項目依其位置的方法。  
  
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
