---
title: "如何：以程式設計的方式將項目加入至 Windows Form DomainUpDown 控制項"
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
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e540e394226f20c40915f4d9de31afcffdf6e35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a><span data-ttu-id="8ab40-102">如何：以程式設計的方式將項目加入至 Windows Form DomainUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="8ab40-102">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>
<span data-ttu-id="8ab40-103">您可以加入 Windows Form 中的項目<xref:System.Windows.Forms.DomainUpDown>程式碼中的控制項。</span><span class="sxs-lookup"><span data-stu-id="8ab40-103">You can add items to the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span> <span data-ttu-id="8ab40-104">呼叫<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>或<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>方法<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>類別，以將項目加入至控制項的<xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="8ab40-104">Call the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to add items to the control's <xref:System.Windows.Forms.DomainUpDown.Items%2A> property.</span></span> <span data-ttu-id="8ab40-105"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>方法將項目加入集合的結尾時<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>方法將項目中指定的位置。</span><span class="sxs-lookup"><span data-stu-id="8ab40-105">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method adds an item to the end of a collection, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method adds an item at a specified position.</span></span>  
  
### <a name="to-add-a-new-item"></a><span data-ttu-id="8ab40-106">若要加入新項目</span><span class="sxs-lookup"><span data-stu-id="8ab40-106">To add a new item</span></span>  
  
1.  <span data-ttu-id="8ab40-107">使用<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>方法將項目新增至的項目清單的結尾。</span><span class="sxs-lookup"><span data-stu-id="8ab40-107">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method to add an item to the end of the list of items.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     <span data-ttu-id="8ab40-108">-或-</span><span class="sxs-lookup"><span data-stu-id="8ab40-108">-or-</span></span>  
  
2.  <span data-ttu-id="8ab40-109">使用<xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>方法，以將項目插入位於指定位置的清單。</span><span class="sxs-lookup"><span data-stu-id="8ab40-109">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method to insert an item into the list at a specified position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8ab40-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="8ab40-110">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>  
 <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8ab40-111">DomainUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="8ab40-111">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [<span data-ttu-id="8ab40-112">DomainUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="8ab40-112">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)
