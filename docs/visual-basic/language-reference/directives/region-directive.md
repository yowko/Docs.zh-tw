---
title: '#Region 指示詞'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83ceac7d73eff23e16c5f6efb1c4eb8a2210ee2c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
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
|`identifier_string`|必要。 做為摺疊區域標題的字串。 區域預設會摺疊。|  
|`#End Region`|終止 `#Region` 區塊。|  
  
## <a name="remarks"></a>備註  
 使用 `#Region` 指示詞來指定程式碼區段，以在使用 Visual Studio 程式碼編輯器的大綱功能時展開或摺疊。 您可以放置，或*巢狀*，以類似的區域群組在一起的其他區域內。  
  
## <a name="example"></a>範例  
 此範例使用 `#Region` 指示詞。  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [大綱](/visualstudio/ide/outlining)  
 [操作說明：摺疊和隱藏程式碼區段](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
