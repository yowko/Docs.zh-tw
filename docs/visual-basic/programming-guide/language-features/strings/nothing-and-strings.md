---
title: Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 392de45b0ee1688224f3e8170b0144f1acdb0912
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360562"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic 中的 Nothing 和字串
Visual Basic 執行時間和 .NET Framework `Nothing` 會在字串中以不同的方式評估。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic 執行時間和 .NET Framework  
 請考慮下列範例：  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Visual Basic 執行時間通常會評估 `Nothing` 為空字串（""）。 不過，每當嘗試在上執行字串作業時，.NET Framework 都不會擲回例外狀況 `Nothing` 。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的字串簡介](introduction-to-strings.md)
