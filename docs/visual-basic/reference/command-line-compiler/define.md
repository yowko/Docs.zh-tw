---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: cb56e727479fd249cb0d7e5e7c3c50d5b68b3a72
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072011"
---
# <a name="-define-visual-basic"></a>-定義 (Visual Basic) 

定義條件式編譯器常數。  
  
## <a name="syntax"></a>語法  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

或

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`symbol`|必要。 要定義的符號。|  
|`value`|選擇性。 要指派 `symbol` 的值。 如果 `value` 是字串，則必須以反斜線/引號順序括住 (\\ ") 而非引號。 如果未指定值，則會認為是 True。|  
  
## <a name="remarks"></a>備註  

 此 `-define` 選項的效果類似于 `#Const` 在原始程式檔中使用預處理器指示詞，不同之處在于使用定義的常數 `-define` 是公用的，而且會套用至專案中的所有檔案。  
  
 您可以使用此選項建立的符號，搭配 `#If`...`Then`...`#Else` 指示詞，有條件地編譯原始程式檔。  
  
 `-d` 是 `-define` 的簡短形式。  
  
 您可以使用逗號分隔符號定義，以 `-define` 定義多個符號。  
  
|在 Visual Studio 整合式開發環境中設定-定義|  
|---|  
|1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。 <br />2. 按一下 [ **編譯** ] 索引標籤。<br />3. 按一下 [ **Advanced**]。<br />4. 修改 [ **自訂常數** ] 方塊中的值。|  
  
## <a name="example"></a>範例  

 下列程式碼會定義然後使用兩個條件式編譯器常數。  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [#If .。。Then ... #Else 指示詞](../../language-reference/directives/if-then-else-directives.md)
- [#Const 指示詞](../../language-reference/directives/const-directive.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
