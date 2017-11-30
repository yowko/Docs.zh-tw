---
title: "如何：從 Windows Form DomainUpDown 控制項中移除項目"
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
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cab9bf4445c7322c1b4824f26c0821de8c58657
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="725dc-102">如何：從 Windows Form DomainUpDown 控制項中移除項目</span><span class="sxs-lookup"><span data-stu-id="725dc-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="725dc-103">您可以移除 Windows Form 中的項目<xref:System.Windows.Forms.DomainUpDown>藉由呼叫控制項<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>或<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>方法<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="725dc-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="725dc-104"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>方法移除特定的項目，雖然<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>方法中移除項目依其位置。</span><span class="sxs-lookup"><span data-stu-id="725dc-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="725dc-105">若要移除項目</span><span class="sxs-lookup"><span data-stu-id="725dc-105">To remove an item</span></span>  
  
-   <span data-ttu-id="725dc-106">使用<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A>方法<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>類別依名稱移除項目。</span><span class="sxs-lookup"><span data-stu-id="725dc-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="725dc-107">-或-</span><span class="sxs-lookup"><span data-stu-id="725dc-107">-or-</span></span>  
  
-   <span data-ttu-id="725dc-108">使用<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>方法，以移除項目依其位置。</span><span class="sxs-lookup"><span data-stu-id="725dc-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="725dc-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="725dc-109">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="725dc-110">DomainUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="725dc-110">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [<span data-ttu-id="725dc-111">DomainUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="725dc-111">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
