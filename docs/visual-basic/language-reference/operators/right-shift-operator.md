---
title: '>> 運算子'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 00f43bc9bae6d550ed175906777ac273fc8e9a23
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873338"
---
# <a name="-operator-visual-basic"></a>>> 運算子 (Visual Basic) 

在位模式上執行算術右移位。  
  
## <a name="syntax"></a>Syntax  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>組件  

 `result`  
 必要。 整數數值。 位元模式移位的結果。 資料型別與 `pattern` 的型別相同。  
  
 `pattern`  
 必要。 整數值運算式。 要移位的位元模式。 資料型別必須是整數類資料型別 (Integral Type) (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`)。  
  
 `amount`  
 必要。 數值運算式。 位元模式移位的位元數。 資料型別必須是 `Integer` 或擴展至 `Integer`。  
  
## <a name="remarks"></a>備註  

 算術移位不是迴圈的，這表示不會在另一端重新出現從結果的一端移出的位。 在算術右移位中，會捨棄超出最右邊位位置的位，並將最左邊的 (符號) 位傳播到左側空出的位位置。 這表示，如果的 `pattern` 值為負值，空出的位置會設定為1，否則會設為零。  
  
 請注意，資料類型 `Byte` 、 `UShort` 、 `UInteger` 和未 `ULong` 簽署，因此沒有要傳播的符號位。 如果 `pattern` 是任何不帶正負號的類型，空出的位置一律會設定為零。  
  
 為了防止超過結果所能保存的位數，Visual Basic 會以 `amount` 對應至資料類型的大小遮罩來遮罩的值 `pattern` 。 這些值的二進位和都是用於移位量。 大小遮罩如下所示：  
  
|的資料類型 `pattern`|大小遮罩 (decimal) |大小遮罩 (十六進位) |  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 如果 `amount` 是零，的值 `result` 就會與的值相同 `pattern` 。 如果 `amount` 是負數，則會被視為不帶正負號的值，並以適當的大小遮罩進行遮罩。  
  
 算術移位絕不會產生溢位例外狀況。  
  
## <a name="overloading"></a>多載化  

 可以多載 `>>` 運算子*overloaded*，這表示當運算元具有該類別或結構的型別時，類別或結構可以重新定義其行為。 如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其重新定義的行為。 如需詳細資訊，請參閱 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>範例  

 下列範例會使用 `>>` 運算子，在整數值上執行算術右移位。 結果一律具有與要移位的運算式相同的資料類型。  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 上述範例的結果如下所示：  
  
- `result1` 為 2560 (0000 1010 0000 0000) 。  
  
- `result2` 為 160 (0000 0000 1010 0000) 。  
  
- `result3` 是 2 (0000 0000 0000 0010) 。  
  
- `result4` 為 640 (0000 0010 1000 0000) 。  
  
- `result5` 為 0 (將15個位置向右) 移位。  
  
 的移位數量 `result4` 會計算為18和15，等於2。  
  
 下列範例顯示負數值的算術移位。  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 上述範例的結果如下所示：  
  
- `negresult1` 是-512 (1111 1110 0000 0000) 。  
  
- `negresult2` 為-1 (會將符號位傳播) 。  
  
## <a name="see-also"></a>另請參閱

- [位元移位運算子](bit-shift-operators.md)
- [指派運算子](assignment-operators.md)
- [>>= 運算子](right-shift-assignment-operator.md)
- [Visual Basic 中的運算子優先順序](operator-precedence.md)
- [依功能列出運算子](operators-listed-by-functionality.md)
- [Visual Basic 的算術運算子](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
