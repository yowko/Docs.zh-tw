---
title: Erase 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 7dec2a859f664ee8dcbb305082ec33aeacbaccb4
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583392"
---
# <a name="erase-statement-visual-basic"></a>Erase 陳述式 (Visual Basic)
用來釋放陣列變數，並解除配置其元素所使用的記憶體。  
  
## <a name="syntax"></a>語法  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>組件  
 `arraylist`  
 必要項。 要清除的陣列變數清單。 以逗號分隔多個變數。  
  
## <a name="remarks"></a>備註  
 @No__t_0 語句只能出現在程式層級。 這表示您可以在程式中釋放陣列，而不是在類別或模組層級。  
  
 @No__t_0 語句相當於將 `Nothing` 指派給每個陣列變數。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Erase` 語句來清除兩個數組，並釋放其記憶體（分別是1000和100儲存元素）。 接著 `ReDim` 語句會將新的陣列實例指派給三維陣列。  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>請參閱

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)
