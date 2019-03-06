---
title: HOW TO：取得 ListBoxItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox controls [WPF], getting a ListBoxItem
- ListBoxItem [WPF]
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
ms.openlocfilehash: 27a435feb4a941c77af221ab25bd63ea98b16e92
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360494"
---
# <a name="how-to-get-a-listboxitem"></a><span data-ttu-id="d0b01-102">HOW TO：取得 ListBoxItem</span><span class="sxs-lookup"><span data-stu-id="d0b01-102">How to: Get a ListBoxItem</span></span>
<span data-ttu-id="d0b01-103">若要取得特定<xref:System.Windows.Controls.ListBoxItem>中的特定索引處<xref:System.Windows.Controls.ListBox>，您可以使用<xref:System.Windows.Controls.ItemContainerGenerator>。</span><span class="sxs-lookup"><span data-stu-id="d0b01-103">If you need to get a specific <xref:System.Windows.Controls.ListBoxItem> at a particular index in a <xref:System.Windows.Controls.ListBox>, you can use an <xref:System.Windows.Controls.ItemContainerGenerator>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0b01-104">範例</span><span class="sxs-lookup"><span data-stu-id="d0b01-104">Example</span></span>  
 <span data-ttu-id="d0b01-105">下列範例所示<xref:System.Windows.Controls.ListBox>和其項目。</span><span class="sxs-lookup"><span data-stu-id="d0b01-105">The following example shows a <xref:System.Windows.Controls.ListBox> and its items.</span></span>  
  
 [!code-xaml[ListBoxItems#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="d0b01-106">下列範例示範如何藉由指定的索引中的項目擷取的項目<xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A>屬性<xref:System.Windows.Controls.ItemContainerGenerator>。</span><span class="sxs-lookup"><span data-stu-id="d0b01-106">The following example shows how to retrieve the item by specifying the index of the item in the <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> property of the <xref:System.Windows.Controls.ItemContainerGenerator>.</span></span>  
  
 [!code-csharp[ListBoxItems#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="d0b01-107">擷取清單方塊項目之後，您就可以顯示項目的內容，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d0b01-107">After you have retrieved the list box item, you can display the contents of the item, as shown in the following example.</span></span>  
  
 [!code-csharp[ListBoxItems#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]
