---
title: Visual Basic 中的 Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: f5c1ea8cc0728b25e8e874963967aed504e466d7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591340"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic 中的 Nothing 和字串
Visual Basic 執行階段和.NET Framework 評估`Nothing`以不同的方式就是字串。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic 執行階段和.NET Framework  
 參考下列範例：  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Visual Basic 執行階段通常會評估`Nothing`為空字串 ("")。 .NET Framework 並不會不過，並擲回例外狀況，每當嘗試執行字串作業`Nothing`。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
