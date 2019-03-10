---
title: HOW TO：移除 Windows Form DomainUpDown 控制項中的項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: 58c93f478414d24c2fdda0f9662936a8b520e381
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708960"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="26d1e-102">HOW TO：移除 Windows Form DomainUpDown 控制項中的項目</span><span class="sxs-lookup"><span data-stu-id="26d1e-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="26d1e-103">您可以移除 Windows Form 中的項目<xref:System.Windows.Forms.DomainUpDown>控制項，藉由呼叫<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>或是<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>方法<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="26d1e-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="26d1e-104"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>方法移除特定的項目，雖然<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>方法移除項目依其位置。</span><span class="sxs-lookup"><span data-stu-id="26d1e-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="26d1e-105">若要移除的項目</span><span class="sxs-lookup"><span data-stu-id="26d1e-105">To remove an item</span></span>  
  
-   <span data-ttu-id="26d1e-106">使用<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>方法的<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>類別名稱中移除項目。</span><span class="sxs-lookup"><span data-stu-id="26d1e-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="26d1e-107">-或-</span><span class="sxs-lookup"><span data-stu-id="26d1e-107">-or-</span></span>  
  
-   <span data-ttu-id="26d1e-108">使用<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>移除項目依其位置的方法。</span><span class="sxs-lookup"><span data-stu-id="26d1e-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="26d1e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26d1e-109">See also</span></span>
- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [<span data-ttu-id="26d1e-110">DomainUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="26d1e-110">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="26d1e-111">DomainUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="26d1e-111">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)
