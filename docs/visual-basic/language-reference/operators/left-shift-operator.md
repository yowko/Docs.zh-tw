---
title: << 運算子
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 77bf26d4e6bb068f9130deed5eb1ecbaee62afce
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866786"
---
# <a name="-operator-visual-basic"></a>\<\< 運算子 (Visual Basic) 

在位模式上執行算術左移位。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>組件  

 `result`  
 必要。 整數數值。 位元模式移位的結果。 資料型別與 `pattern` 的型別相同。  
  
 `pattern`  
 必要。 整數值運算式。 要移位的位元模式。 資料型別必須是整數類資料型別 (Integral Type) (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`)。  
  
 `amount`  
 必要。 數值運算式。 位元模式移位的位元數。 資料型別必須是 `Integer` 或擴展至 `Integer`。  
  
## <a name="remarks"></a>備註  

 算術移位不是迴圈的，這表示不會在另一端重新出現從結果的一端移出的位。 在算術左移位中，會捨棄超出結果資料類型範圍的位，而且右邊的位位置會設定為零。  
  
 為了防止超過結果所能保存的比對位數，Visual Basic 會以 `amount` 對應至資料類型的大小遮罩來遮罩的值 `pattern` 。 這些值的二進位和都是用於移位量。 大小遮罩如下所示：  
  
|的資料類型 `pattern`|大小遮罩 (decimal) |大小遮罩 (十六進位) |  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 如果 `amount` 是零，的值 `result` 就會與的值相同 `pattern` 。 如果 `amount` 是負數，則會被視為不帶正負號的值，並以適當的大小遮罩進行遮罩。  
  
 算術移位絕不會產生溢位例外狀況。  
  
> [!NOTE]
> 可以多載 `<<` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `<<` 運算子，在整數值上執行算術左移位。 結果一律具有與要移位的運算式相同的資料類型。  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 上述範例的結果如下所示：  
  
- `result1` 為 192 (0000 0000 1100 0000) 。  
  
- `result2` 為 3072 (0000 1100 0000 0000) 。  
  
- `result3` 是-32768 (1000 0000 0000 0000) 。  
  
- `result4` 為 384 (0000 0001 1000 0000) 。  
  
- `result5` 為 0 (將15個位置向左) 移位。  
  
 的移位數量 `result4` 會計算為17和15，等於1。  
  
## <a name="see-also"></a>另請參閱

- [位元移位運算子](bit-shift-operators.md)
- [指派運算子](assignment-operators.md)
- [<<= 運算子](left-shift-assignment-operator.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
