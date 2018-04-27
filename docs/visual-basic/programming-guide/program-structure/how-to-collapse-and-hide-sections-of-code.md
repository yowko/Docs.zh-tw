---
title: 如何：摺疊和隱藏程式碼區段 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4497c9586182cca9e2be97dc39e5ccb242725d25
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>如何：摺疊和隱藏程式碼區段 (Visual Basic)
`#Region`指示詞可讓您可以摺疊並隱藏 Visual Basic 檔案中的程式碼區段。 `#Region`指示詞可讓您使用 Visual Studio 程式碼編輯器時，指定一段程式碼，您可以展開或摺疊。 選擇性地隱藏程式碼的功能可讓您的檔案，更容易管理而且更容易閱讀。 如需詳細資訊，請參閱[大綱](/visualstudio/ide/outlining)。  
  
 `#Region` 指示詞會支援這類程式碼區塊語意`#If...#End If`。 這表示無法在單一區塊中開始與結束在另一個。開始和結束必須在相同的區塊。 `#Region` 指示詞不支援在函式內。  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>若要摺疊和隱藏程式碼區段  
  
-   將程式碼之間的區段`#Region`和`#End Region`陳述式，如下列範例所示：  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     `#Region`區塊可以重複使用程式碼檔案中; 因此，使用者可以定義自己的程序和，接著可摺疊類別的區塊。 `#Region` 區塊也可以巢狀內其他`#Region`區塊。  
  
    > [!NOTE]
    >  隱藏程式碼不會阻止它正在進行編譯，且不影響`#If...#End If`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)  
 [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [大綱](/visualstudio/ide/outlining)
