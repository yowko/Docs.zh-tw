---
title: 以零為起始與在 Visual Basic 中的其中一個基礎字串存取
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: cc8f286de41d7e44225e889e73ff3c7b1fdbd881
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591743"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>以零為起始與在 Visual Basic 中的其中一個基礎字串存取
本主題會比較 Visual Basic 和.NET Framework 提供字串中字元的權限。 .NET Framework 一律會提供以零為起始的存取權的字元在字串中，而 Visual Basic 提供的以零為起始與以一為基的存取，視函數而定。  
  
## <a name="one-based"></a>以一為  
 如需以一為基的 Visual Basic 函式的範例，請考慮`Mid`函式。 它會指出子字串將會開始，從位置 1 開始的字元位置的引數。 .NET Framework<xref:System.String.Substring%2A?displayProperty=nameWithType>方法採用索引之字元的子字串開始，已在字串中從開始位置 0。 因此，如果您有一個字串"ABCDE"時，個別字元的編號搭配 id:1,2,3,4,5`Mid`函式，但搭配 0,1,2,3,4<xref:System.String.Substring%2A?displayProperty=nameWithType>方法。  
  
## <a name="zero-based"></a>以零為起始  
 如需以零為起始的 Visual Basic 函式的範例，請考慮`Split`函式。 它會將字串分割，並傳回陣列，包含子字串。 .NET Framework<xref:System.String.Split%2A?displayProperty=nameWithType>方法也會將字串分割，並傳回陣列，包含子字串。 因為`Split`函式和<xref:System.String.Split%2A>方法傳回.NET Framework 的陣列，它們必須是以零為起始。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
