---
title: 以零為起始與在 Visual Basic 中的其中一個基礎字串存取
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a6ceb10d4a3cb9463551d8c85375ddbbb607ffdc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830327"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>以零為起始與在 Visual Basic 中的其中一個基礎字串存取
本主題會比較如何 Visual Basic 和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]提供字串中字元的權限。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]一律提供之以零起始的存取權的字元在字串中，而 Visual Basic 提供的以零為起始與以一為基的存取，視函數而定。  
  
## <a name="one-based"></a>以一為  
 如需以一為基的 Visual Basic 函式的範例，請考慮`Mid`函式。 它會指出子字串將會開始，從位置 1 開始的字元位置的引數。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType>方法採用索引之字元的子字串開始，已在字串中從開始位置 0。 因此，如果您有一個字串"ABCDE"時，個別字元的編號搭配 id:1,2,3,4,5`Mid`函式，但搭配 0,1,2,3,4<xref:System.String.Substring%2A?displayProperty=nameWithType>方法。  
  
## <a name="zero-based"></a>以零為起始  
 如需以零為起始的 Visual Basic 函式的範例，請考慮`Split`函式。 它會將字串分割，並傳回陣列，包含子字串。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType>方法也會將字串分割，並傳回陣列，包含子字串。 因為`Split`函式與<xref:System.String.Split%2A>方法會傳回[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]它們必須是以零為起始的陣列、 物。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
