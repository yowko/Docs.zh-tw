---
title: 以零為起始的 vs。在 Visual Basic 中的其中一個基礎字串存取
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a0a42f72d94adf1c10865374017fa61e833df40f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649096"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>以零為起始的 vs。在 Visual Basic 中的其中一個基礎字串存取
本主題會比較方式 Visual Basic 和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]提供字串中字元的權限。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]一律存取以零為起始的字元在字串中，而 Visual Basic 提供的以零為起始和一個型的存取，根據函式。  
  
## <a name="one-based"></a>1 為基底  
 如需以一為 Visual Basic 函式的範例，請考慮`Mid`函式。 它會指出子字串開始，從位置 1 開始的字元位置的引數。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType>方法會採用字元的索引子字串開始，已在字串中開始位置 0。 因此，如果您有一個字串"ABCDE 」，個別字元的編號 1,2,3,4,5 搭配`Mid`函式，但搭配 0,1,2,3,4<xref:System.String.Substring%2A?displayProperty=nameWithType>方法。  
  
## <a name="zero-based"></a>以零為起始  
 如需以零為起始的 Visual Basic 函式的範例，請考慮`Split`函式。 它會將字串分割，並傳回包含之子字串的陣列。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType>方法也會將字串分割，並傳回包含之子字串的陣列。 因為`Split`函式和<xref:System.String.Split%2A>方法傳回[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]的陣列，它們必須是以零為起始。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
