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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001594"
---
# <a name="how-to-enumerate-system-fonts"></a>HOW TO：列舉系統字型
## <a name="example"></a>範例  
 下列範例示範如何列舉系統字型集合中的字型。 每個字型系列名稱<xref:System.Windows.Media.FontFamily>內<xref:System.Windows.Media.Fonts.SystemFontFamilies%2A>做為項目加入至下拉式方塊。  
  
 [!code-csharp[TextOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 如果在相同的字型系列的多個版本位於相同的目錄，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]字型列舉型別傳回字型的最新版本。 如果版本資訊不會提供解決方式，就會傳回具有最新時間戳記的字型。 如果時間戳記資訊是對等項目，則會傳回依字母順序排列的順序中的第一個字型檔案。
