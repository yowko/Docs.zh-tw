---
title: '#Const 指示詞'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 91152771a4ef5ec74a7408511ccc2afe28dd442e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415462"
---
# <a name="const-directive"></a>#Const 指示詞

定義 Visual Basic 的條件式編譯器常數。  
  
## <a name="syntax"></a>語法  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>組件  

 `constname`  
 必要。 所定義之常數的名稱。  
  
 `expression`  
 必要。 常值、其他條件式編譯器常數，或包含除了以外的任何或所有算術或邏輯運算子的任何組合 `Is` 。  
  
## <a name="remarks"></a>備註  

 條件式編譯器常數一律為其出現所在檔案的私用。 您無法使用指示詞來建立公用編譯器常數 `#Const` ; 您只能在使用者介面或使用編譯器選項來建立它們 `/define` 。  
  
 您只能在中使用條件式編譯器常數和常值 `expression` 。 使用定義的標準常數 `Const` 會造成錯誤。 相反地，您可以使用以關鍵字定義的常數 `#Const` 來進行條件式編譯。 常數也可以是未定義的，在此情況下，它們的值為 `Nothing` 。  
  
## <a name="example"></a>範例  

 此範例使用 `#Const` 指示詞。  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- [-define （Visual Basic）](../../reference/command-line-compiler/define.md)
- [#If .。。Then ... #Else 指示詞](if-then-else-directives.md)
- [Const 陳述式](../statements/const-statement.md)
- [條件式編譯](../../programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else 陳述式](../statements/if-then-else-statement.md)
