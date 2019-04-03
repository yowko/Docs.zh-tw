---
title: Erase 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: bf3eb6476dc1485faeddab475f29e508175d3378
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840402"
---
# <a name="erase-statement-visual-basic"></a>Erase 陳述式 (Visual Basic)
用以釋放陣列變數，並解除配置其元素所使用的記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>組件  
 `arraylist`  
 必要項。 要清除的陣列變數的清單。 以逗號分隔多個變數。  
  
## <a name="remarks"></a>備註  
 `Erase`陳述式只可以出現在程序層級。 這表示您可以釋放程序內，但不是在類別或模組層級的陣列。  
  
 `Erase`陳述式相當於指派`Nothing`到每個陣列變數。  
  
## <a name="example"></a>範例  
 下列範例會使用`Erase`陳述式來清除這兩個陣列，並釋放其記憶體 (1000年和 100 個儲存體項目，分別)。 `ReDim`陳述式，然後將新的陣列執行個體指派給三維陣列。  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>另請參閱

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)
