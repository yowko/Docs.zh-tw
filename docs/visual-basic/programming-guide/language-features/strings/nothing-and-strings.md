---
title: Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: dfc43748d0754f0a6a29763c42ab82d9937f89f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344300"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic 中的 Nothing 和字串
Visual Basic 執行時間和 .NET Framework 會在對字串進行不同的評估 `Nothing`。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic 執行時間和 .NET Framework  
 參考下列範例：  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Visual Basic 執行時間通常會將 `Nothing` 評估為空字串（""）。 不過，.NET Framework 在嘗試對 `Nothing`執行字串作業時，並不會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
