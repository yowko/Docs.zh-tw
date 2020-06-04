---
title: Erase 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 31aeaf822bc9c1de59a5c5f68406c6521216ae0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404715"
---
# <a name="erase-statement-visual-basic"></a>Erase 陳述式 (Visual Basic)
用來釋放陣列變數，並解除配置其元素所使用的記憶體。  
  
## <a name="syntax"></a>語法  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>組件  
 `arraylist`  
 必要。 要清除的陣列變數清單。 以逗號分隔多個變數。  
  
## <a name="remarks"></a>備註  
 `Erase`語句只能出現在程式層級。 這表示您可以在程式中釋放陣列，而不是在類別或模組層級。  
  
 `Erase`語句相當於指派 `Nothing` 給每個陣列變數。  
  
## <a name="example"></a>範例  
 下列範例會使用 `Erase` 語句來清除兩個數組，並釋放其記憶體（分別是1000和100儲存元素）。 然後，語句會將 `ReDim` 新的陣列實例指派給三維陣列。  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>另請參閱

- [Nothing](../nothing.md)
- [ReDim 陳述式](redim-statement.md)
