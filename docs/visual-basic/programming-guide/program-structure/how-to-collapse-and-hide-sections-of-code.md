---
title: "如何︰ 摺疊和隱藏程式碼區段 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
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
ms.openlocfilehash: 200a90b6983277d46b6e5c7b27ee4a90ecf88c40
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a>如何：摺疊和隱藏程式碼區段 (Visual Basic)
`#Region`指示詞可讓您摺疊和隱藏程式碼中的區段[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]檔案。 `#Region`指示詞可讓您使用時，指定一段程式碼，您可以展開或摺疊[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]程式碼編輯器。 選擇性地隱藏程式碼的功能，使您更容易管理且更方便閱讀。 如需詳細資訊，請參閱[大綱](https://docs.microsoft.com/visualstudio/ide/outlining)。  
  
 `#Region`指示詞支援程式碼區塊語意 （semantics），例如`#If...#End If`。 這表示無法在一個區塊開始與結束在另一個。開始和結束必須是同一個區塊中。 `#Region`指示詞不支援函式內。  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a>若要摺疊和隱藏程式碼區段  
  
-   將程式碼之間的區段`#Region`和`#End Region`陳述式，如下列範例所示︰  
  
     [!code-vb[VbVbalrConditionalComp #&6;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     `#Region`區塊可以重複使用程式碼檔案中; 因此，使用者可以定義自己的區塊的程序和，反而可摺疊的類別。 `#Region`區塊可以也巢狀內其他`#Region`區塊。  
  
    > [!NOTE]
    >  隱藏程式碼不會阻止它正在進行編譯，且不影響`#If...#End If`陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)   
 [#If......#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [大綱](https://docs.microsoft.com/visualstudio/ide/outlining)
