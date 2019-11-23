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
ms.openlocfilehash: fd0875f09bf3ba7211ede500aa0da45f8b7cd2c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344768"
---
# <a name="-define-visual-basic"></a>-define (Visual Basic)
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
|`symbol`|必要項。 要定義的符號。|  
|`value`|選擇項。 要指派 `symbol` 的值。 If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks. 如果未指定值，則會認為是 True。|  
  
## <a name="remarks"></a>備註  
 The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.  
  
 您可以使用此選項建立的符號，搭配 `#If`...`Then`...`#Else` 指示詞，有條件地編譯原始程式檔。  
  
 `-d` 是 `-define` 的簡短形式。  
  
 您可以使用逗號分隔符號定義，以 `-define` 定義多個符號。  
  
|在 Visual Studio 整合式開發環境中設定 / 定義|  
|---|  
|1.  Have a project selected in **Solution Explorer**. 在 [專案] 功能表上，按一下 [屬性]。 <br />2.  Click the **Compile** tab.<br />3.  Click **Advanced**.<br />4.  Modify the value in the **Custom Constants** box.|  
  
## <a name="example"></a>範例  
 下列程式碼會定義然後使用兩個條件式編譯器常數。  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a>請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [#If...Then...#Else 指示詞](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [#Const 指示詞](../../../visual-basic/language-reference/directives/const-directive.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
