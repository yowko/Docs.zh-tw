---
title: HOW TO：列舉系統字型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
ms.openlocfilehash: c7e81b5d1b70ba911a0b505219f7977e019038cf
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352434"
---
# <a name="how-to-enumerate-system-fonts"></a><span data-ttu-id="ecd2c-102">HOW TO：列舉系統字型</span><span class="sxs-lookup"><span data-stu-id="ecd2c-102">How to: Enumerate System Fonts</span></span>
## <a name="example"></a><span data-ttu-id="ecd2c-103">範例</span><span class="sxs-lookup"><span data-stu-id="ecd2c-103">Example</span></span>  
 <span data-ttu-id="ecd2c-104">下列範例示範如何列舉系統字型集合中的字型。</span><span class="sxs-lookup"><span data-stu-id="ecd2c-104">The following example shows how to enumerate the fonts in the system font collection.</span></span> <span data-ttu-id="ecd2c-105">每個字型系列名稱<xref:System.Windows.Media.FontFamily>內<xref:System.Windows.Media.Fonts.SystemFontFamilies%2A>做為項目加入至下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="ecd2c-105">The font family name of each <xref:System.Windows.Media.FontFamily> within <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> is added as an item to a combo box.</span></span>  
  
 [!code-csharp[TextOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 <span data-ttu-id="ecd2c-106">如果在相同的字型系列的多個版本位於相同的目錄，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]字型列舉型別傳回字型的最新版本。</span><span class="sxs-lookup"><span data-stu-id="ecd2c-106">If multiple versions of the same font family reside in the same directory, the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] font enumeration returns the most recent version of the font.</span></span> <span data-ttu-id="ecd2c-107">如果版本資訊不會提供解決方式，就會傳回具有最新時間戳記的字型。</span><span class="sxs-lookup"><span data-stu-id="ecd2c-107">If the version information does not provide resolution, the font with latest timestamp is returned.</span></span> <span data-ttu-id="ecd2c-108">如果時間戳記資訊是對等項目，則會傳回依字母順序排列的順序中的第一個字型檔案。</span><span class="sxs-lookup"><span data-stu-id="ecd2c-108">If the timestamp information is equivalent, the font file that is first in alphabetical order is returned.</span></span>
