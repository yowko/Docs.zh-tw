---
title: Call 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: af0b62d6cfacbcf94f527e049e07e51bf496a6cf
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392754"
---
# <a name="call-statement-visual-basic"></a>Call 陳述式 (Visual Basic)

將控制權轉移至 `Function`、@no__t 1 或動態連結程式庫（DLL）程式。

## <a name="syntax"></a>語法

```vb
[ Call ] procedureName [ (argumentList) ]
```

## <a name="parts"></a>組件

|||
|---|---|
|`procedureName`|必要項。 要呼叫的程式名稱。|
|`argumentList`|選擇性。 變數或運算式的清單，代表呼叫時傳遞給程式的引數。 以逗號分隔多個引數。 如果您包含 `argumentList`，則必須將它括在括弧中。|
|||
  
## <a name="remarks"></a>備註

 當您呼叫程式時，可以使用 `Call` 關鍵字。 對於大部分的程序呼叫，您不需要使用此關鍵字。

 當被呼叫的運算式不是以識別碼開頭時，您通常會使用 `Call` 關鍵字。 不建議針對其他用途使用 `Call` 關鍵字。

 如果程式傳回值，則 @no__t 0 語句會將它捨棄。

## <a name="example"></a>範例

 下列程式碼顯示兩個範例，其中需要 `Call` 關鍵字來呼叫程式。 在這兩個範例中，被呼叫的運算式不是以識別碼開頭。

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a>另請參閱

- [Function 陳述式](function-statement.md)
- [Sub 陳述式](sub-statement.md)
- [Declare 陳述式](declare-statement.md)
- [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)
