---
title: "如何：將 ListBox 繫結至資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4701fe99231e115eb8cb14f7c1e5e003928bc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="b8c44-102">如何：將 ListBox 繫結至資料</span><span class="sxs-lookup"><span data-stu-id="b8c44-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="b8c44-103">應用程式開發人員可以建立<xref:System.Windows.Controls.ListBox>不使用指定的每個內容控制項<xref:System.Windows.Controls.ListBoxItem>分開。</span><span class="sxs-lookup"><span data-stu-id="b8c44-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="b8c44-104">您可以使用資料繫結至資料繫結至個別的項目。</span><span class="sxs-lookup"><span data-stu-id="b8c44-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="b8c44-105">下列範例示範如何建立<xref:System.Windows.Controls.ListBox>，填入<xref:System.Windows.Controls.ListBoxItem>所呼叫的資料來源的資料繫結項目*色彩*。</span><span class="sxs-lookup"><span data-stu-id="b8c44-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="b8c44-106">在此情況下不需要使用<xref:System.Windows.Controls.ListBoxItem>標籤來指定每個項目的內容。</span><span class="sxs-lookup"><span data-stu-id="b8c44-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8c44-107">範例</span><span class="sxs-lookup"><span data-stu-id="b8c44-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b8c44-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8c44-108">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [<span data-ttu-id="b8c44-109">控制項</span><span class="sxs-lookup"><span data-stu-id="b8c44-109">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
