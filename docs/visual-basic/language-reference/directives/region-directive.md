---
title: '#區域指示詞 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: eaaf0f8279ec905767be3f364a88357f0d393bba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818864"
---
# <a name="region-directive"></a>#Region 指示詞
摺疊並隱藏 Visual Basic 檔案中的程式碼區段。  
  
## <a name="syntax"></a>語法  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`identifier_string`|必要項。 做為摺疊區域標題的字串。 區域預設會摺疊。|  
|`#End Region`|終止 `#Region` 區塊。|  
  
## <a name="remarks"></a>備註  
 使用 `#Region` 指示詞來指定程式碼區段，以在使用 Visual Studio 程式碼編輯器的大綱功能時展開或摺疊。 您可以將放，或*巢狀化*，其他區域來分組類似的區域內。  
  
## <a name="example"></a>範例  
 此範例使用 `#Region` 指示詞。  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>另請參閱

- [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [大綱](/visualstudio/ide/outlining)
- [如何：摺疊和隱藏程式碼區段](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
