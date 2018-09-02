---
title: Visual Basic 中的 Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d03781209f0f9b021d540bd251c6c6025ad21422
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425207"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic 中的 Nothing 和字串
Visual Basic 執行階段和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]評估`Nothing`以不同的方式就是字串。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic 執行階段和.NET Framework  
 參考下列範例：  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 Visual Basic 執行階段通常會評估`Nothing`為空字串 ("")。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]則否，不過，並擲回例外狀況，每當嘗試執行字串作業`Nothing`。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
