---
title: "如何：列舉系統字型"
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
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ae03cbd8828f61011f8d806be32b5827d77b22a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enumerate-system-fonts"></a><span data-ttu-id="61cb4-102">如何：列舉系統字型</span><span class="sxs-lookup"><span data-stu-id="61cb4-102">How to: Enumerate System Fonts</span></span>
## <a name="example"></a><span data-ttu-id="61cb4-103">範例</span><span class="sxs-lookup"><span data-stu-id="61cb4-103">Example</span></span>  
 <span data-ttu-id="61cb4-104">下列範例會示範如何列舉系統字型集合中的字型。</span><span class="sxs-lookup"><span data-stu-id="61cb4-104">The following example shows how to enumerate the fonts in the system font collection.</span></span> <span data-ttu-id="61cb4-105">每個字型家族名稱<xref:System.Windows.Media.FontFamily>內<xref:System.Windows.Media.Fonts.SystemFontFamilies%2A>做為項目加入到下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="61cb4-105">The font family name of each <xref:System.Windows.Media.FontFamily> within <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> is added as an item to a combo box.</span></span>  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 <span data-ttu-id="61cb4-106">如果在相同的目錄中，位於多個版本的相同字型家族[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]字型的列舉會傳回最新版本的字型。</span><span class="sxs-lookup"><span data-stu-id="61cb4-106">If multiple versions of the same font family reside in the same directory, the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] font enumeration returns the most recent version of the font.</span></span> <span data-ttu-id="61cb4-107">如果版本資訊不提供解析，則會傳回最新時間戳記的字型。</span><span class="sxs-lookup"><span data-stu-id="61cb4-107">If the version information does not provide resolution, the font with latest timestamp is returned.</span></span> <span data-ttu-id="61cb4-108">如果時間戳記資訊是對等項目，則會傳回依字母順序的第一個字型檔案。</span><span class="sxs-lookup"><span data-stu-id="61cb4-108">If the timestamp information is equivalent, the font file that is first in alphabetical order is returned.</span></span>
