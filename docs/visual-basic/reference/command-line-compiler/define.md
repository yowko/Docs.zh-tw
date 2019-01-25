---
title: -定義 (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 3560ea14236bfa2fffbc309847e8ef9e4b821de9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739267"
---
# <a name="-define-visual-basic"></a>-定義 (Visual Basic)
定義條件式編譯器常數。  
  
## <a name="syntax"></a>語法  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`symbol`|必要項。 要定義的符號。|  
|`value`|選擇項。 要指派 `symbol` 的值。 如果`value`是一個字串，它必須以反斜線/引號的順序括住 (\\」) 而不是引號。 如果未指定值，則會認為是 True。|  
  
## <a name="remarks"></a>備註  
 `-define`選項的效果類似於使用`#Const`原始程式檔，除了定義的常數的前置處理器指示詞`-define`公開並套用至專案中的所有檔案。  
  
 您可以使用此選項建立的符號，搭配 `#If`...`Then`...`#Else` 指示詞，有條件地編譯原始程式檔。  
  
 `-d` 是 `-define` 的簡短形式。  
  
 您可以使用逗號分隔符號定義，以 `-define` 定義多個符號。  
  
|在 Visual Studio 整合式開發環境中設定 / 定義|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階**]。<br />4.修改中的值**自訂常數** 方塊中。|  
  
## <a name="example"></a>範例  
 下列程式碼會定義然後使用兩個條件式編譯器常數。  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
