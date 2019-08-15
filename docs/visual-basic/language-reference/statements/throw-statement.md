---
title: Throw 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 9680700267f17c8e316de351fead61f1dc4aded0
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68869015"
---
# <a name="throw-statement-visual-basic"></a>Throw 陳述式 (Visual Basic)

在程式中擲回例外狀況。

## <a name="syntax"></a>語法

```vb
Throw [ expression ]
```

## <a name="part"></a>組件

`expression`\
提供要擲回之例外狀況的相關資訊。 如果位於`Catch`語句中, 則為選擇性, 否則為必要項。

## <a name="remarks"></a>備註

語句會擲回例外狀況, 您可以處理結構化例外狀況處理常式`Try`代碼 (... `Throw``Catch`...) 或非結構化例外狀況處理`On Error GoTo`程式碼 ()。 `Finally` 您可以使用`Throw`語句來攔截程式碼內的錯誤, 因為 Visual Basic 會向上移動呼叫堆疊, 直到找到適當的例外狀況處理常式代碼為止。

沒有運算式的`Catch` `Catch`語句只能在語句中使用, 在此情況下, 語句會重新擲回目前正由語句處理的例外狀況。 `Throw`

語句會重設`expression`例外狀況的呼叫堆疊。 `Throw` 如果`expression`未提供, 則會將呼叫堆疊保持不變。 您可以透過<xref:System.Exception.StackTrace%2A>屬性存取例外狀況的呼叫堆疊。

## <a name="example"></a>範例

下列程式碼會使用`Throw`語句來擲回例外狀況:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>另請參閱

- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
