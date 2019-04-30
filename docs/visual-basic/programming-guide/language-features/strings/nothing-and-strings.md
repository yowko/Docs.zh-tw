---
title: Visual Basic 中的 Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 5fbcf86261892e3eb8e43ee8eaa3728cd8e42ced
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032275"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic 中的 Nothing 和字串
Visual Basic 執行階段和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]評估`Nothing`以不同的方式就是字串。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic 執行階段和.NET Framework  
 參考下列範例：  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Visual Basic 執行階段通常會評估`Nothing`為空字串 ("")。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]則否，不過，並擲回例外狀況，每當嘗試執行字串作業`Nothing`。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
