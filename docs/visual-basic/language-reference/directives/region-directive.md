---
title: "#Region 指示詞 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
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
ms.openlocfilehash: 1c429602a7eee27944f58256992879d25d533d34
ms.lasthandoff: 03/13/2017

---
# <a name="region-directive"></a>#Region 指示詞
摺疊並隱藏 Visual Basic 檔案中的程式碼區段。  
  
## <a name="syntax"></a>語法  
  
```  
  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`identifier_string`|必要項。 做為摺疊區域標題的字串。 區域預設會摺疊。|  
|`#End Region`|終止 `#Region` 區塊。|  
  
## <a name="remarks"></a>備註  
 使用 `#Region` 指示詞來指定程式碼區段，以在使用 Visual Studio 程式碼編輯器的大綱功能時展開或摺疊。 您可以放置，或*巢狀*，其他區域來分組類似的區域內。  
  
## <a name="example"></a>範例  
 此範例使用 `#Region` 指示詞。  
  
 [!code-vb[VbVbalrConditionalComp #&4;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [#If......#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [大綱](https://docs.microsoft.com/visualstudio/ide/outlining)   
 [如何：摺疊和隱藏程式碼區段](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
