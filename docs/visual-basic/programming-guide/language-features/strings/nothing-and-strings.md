---
title: Nothing 和字串
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d4c7ee6d13334617a80abb845af52bf388a12797
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072518"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic 中的 Nothing 和字串

Visual Basic 執行時間和 .NET Framework `Nothing` 會以不同的方式評估字串。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic 執行時間和 .NET Framework  

 請考慮下列範例：  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Visual Basic 執行時間通常會評估 `Nothing` 為空字串 ( "" ) 。 但是，當嘗試在上執行字串作業時，.NET Framework 不會擲回例外狀況 `Nothing` 。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 中的字串簡介](introduction-to-strings.md)
