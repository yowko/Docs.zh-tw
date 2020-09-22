---
title: Erase 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 33d88b5ce71ceab8d4b4b59d356c53a804c360be
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873289"
---
# <a name="erase-statement-visual-basic"></a>Erase 陳述式 (Visual Basic)

用來釋放陣列變數，並解除配置用於其元素的記憶體。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>組件  

 `arraylist`  
 必要。 要清除的陣列變數清單。 以逗號分隔多個變數。  
  
## <a name="remarks"></a>備註  

 `Erase`語句只能出現在程式層級。 這表示您可以在程式中釋出陣列，而不是在類別或模組層級上釋放。  
  
 `Erase`語句相當於指派 `Nothing` 給每個陣列變數。  
  
## <a name="example"></a>範例  

 下列範例會使用 `Erase` 語句來清除兩個數組，並將其記憶體 (1000 和100的儲存元素分別) 。 然後，語句會將 `ReDim` 新的陣列實例指派給三維陣列。  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>另請參閱

- [什麼](../nothing.md)
- [ReDim 陳述式](redim-statement.md)
