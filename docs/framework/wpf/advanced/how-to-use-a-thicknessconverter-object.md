---
title: "如何：使用 ThicknessConverter 物件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c2445eba7556822c8265337ec97c2f0a9f1d5042
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-a-thicknessconverter-object"></a><span data-ttu-id="bfa25-102">如何：使用 ThicknessConverter 物件</span><span class="sxs-lookup"><span data-stu-id="bfa25-102">How to: Use a ThicknessConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="bfa25-103">範例</span><span class="sxs-lookup"><span data-stu-id="bfa25-103">Example</span></span>  
 <span data-ttu-id="bfa25-104">這個範例示範如何建立的執行個體<xref:System.Windows.ThicknessConverter>並用它來變更框線的粗細。</span><span class="sxs-lookup"><span data-stu-id="bfa25-104">This example shows how to create an instance of <xref:System.Windows.ThicknessConverter> and use it to change the thickness of a border.</span></span>  
  
 <span data-ttu-id="bfa25-105">此範例會定義自訂的方法呼叫`changeThickness`; 此方法會先將轉換的內容<xref:System.Windows.Controls.ListBoxItem>定義在個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案，以執行個體<xref:System.Windows.Thickness>，並稍後將轉換成內容<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="bfa25-105">The example defines a custom method called `changeThickness`; this method first converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Windows.Thickness>, and later converts the content into a <xref:System.String>.</span></span> <span data-ttu-id="bfa25-106">這個方法會傳遞<xref:System.Windows.Controls.ListBoxItem>至<xref:System.Windows.ThicknessConverter>物件，然後將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Windows.Thickness>。</span><span class="sxs-lookup"><span data-stu-id="bfa25-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.ThicknessConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.Thickness>.</span></span> <span data-ttu-id="bfa25-107">此值接著會傳遞做為值回<xref:System.Windows.Controls.Border.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="bfa25-107">This value is then passed back as the value of the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of the <xref:System.Windows.Controls.Border>.</span></span>  
  
 <span data-ttu-id="bfa25-108">此範例不會執行。</span><span class="sxs-lookup"><span data-stu-id="bfa25-108">This example does not run.</span></span>  
  
 [!code-csharp[ThicknessConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bfa25-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="bfa25-109">See Also</span></span>  
 <xref:System.Windows.Thickness>  
 <xref:System.Windows.ThicknessConverter>  
 <xref:System.Windows.Controls.Border>  
 [<span data-ttu-id="bfa25-110">如何： 變更 Margin 屬性</span><span class="sxs-lookup"><span data-stu-id="bfa25-110">How to: Change the Margin Property</span></span>](http://msdn.microsoft.com/library/8a313efd-5f99-4097-b4c1-8fa49d8379a2)  
 [<span data-ttu-id="bfa25-111">如何： 將 ListBoxItem 轉換成新的資料類型</span><span class="sxs-lookup"><span data-stu-id="bfa25-111">How to: Convert a ListBoxItem to a new Data Type</span></span>](http://msdn.microsoft.com/library/7a080b88-184e-4b27-bb61-d42bafba9727)  
 [<span data-ttu-id="bfa25-112">面板概觀</span><span class="sxs-lookup"><span data-stu-id="bfa25-112">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
