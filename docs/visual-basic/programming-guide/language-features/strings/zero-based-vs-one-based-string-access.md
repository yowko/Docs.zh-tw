---
title: "以零為起始的 vs。在 Visual Basic 中的以一為字串存取 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6cd2cab888bf336151ed26968119431f4ffc75f4
ms.lasthandoff: 03/13/2017

---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>以零為起始的 vs。在 Visual Basic 中以一為字串存取
這個主題會比較如何[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]和[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]提供存取權的字串中的字元。 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]一律會提供以零為起始的字元在字串中，存取而[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供以零為起始及一為基礎的存取，根據的函式。  
  
## <a name="one-based"></a>以一為  
 如需範例的其中一個基礎[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]函式，請考慮`Mid`函式。 它會指出子字串開始，從位置 1 開始的字元位置的引數。 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Substring%2A?displayProperty=fullName>方法接受之字元的索引開始，將子字串在的字串中開始位置 0。</xref:System.String.Substring%2A?displayProperty=fullName> 因此，如果您有字串"ABCDE"，個別字元的編號搭配 1,2,3,4,5`Mid`函式，但搭配 0,1,2,3,4<xref:System.String.Substring%2A?displayProperty=fullName>方法。</xref:System.String.Substring%2A?displayProperty=fullName>  
  
## <a name="zero-based"></a>以零為起始  
 如需範例，以零為起始的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]函式，請考慮`Split`函式。 分隔字串，並傳回陣列，包含子字串。 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName>方法也會將字串分割，並傳回陣列，包含子字串。</xref:System.String.Split%2A?displayProperty=fullName> 因為`Split`函式和<xref:System.String.Split%2A>方法會傳回[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]的陣列，它們必須是以零為起始。</xref:System.String.Split%2A>  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:System.String.Substring%2A></xref:System.String.Substring%2A>   
 <xref:System.String.Split%2A></xref:System.String.Split%2A>   
 [在 Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
