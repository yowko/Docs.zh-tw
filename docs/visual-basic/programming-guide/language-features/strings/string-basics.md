---
title: Visual Basic 中的字串基礎
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7262fded93b02c011484919f0504bb7225d8d2af
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965981"
---
# <a name="string-basics-in-visual-basic"></a>Visual Basic 中的字串基礎

  `String` 資料類型代表一系列字元 (每個依序代表 `Char` 資料類型的一個執行個體)。 本主題介紹 Visual Basic 中的字串的基本概念。  
  
## <a name="string-variables"></a>字串變數  
 可將代表字元數列的常值指派給字串的執行個體。 例如:   
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 
  `String` 變數也可以接受評估為字串的任何運算式。 範例如下所示：  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 指派給 `String` 變數的任何常值必須括在引號 ("") 內。 這表示無法以引號表示字串內的引號。 例如，下列程式碼會導致編譯器錯誤：  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 此程式碼會造成錯誤，因為編譯器會終止第二個引號後的字串，並將字串的其餘部分解譯為程式碼。 若要解決此問題，Visual Basic 會解譯為字串中的一個引號常值字串中的兩個引號。 下列範例示範在字串中包含引號的正確方式：  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 在上述範例中，`Look` 文字前面的兩個引號會成為字串中的一個引號。 一行結尾處的三個引號表示字串和字串結束字元的一個引號。  
  
 字串常值可以包含多行：  
  
```vb  
Dim x = "hello  
world"  
```  
  
 產生的字串包含用於字串常值 (vbcr、vbcrlf 等) 的新行字元序列。  您不再需要使用舊的因應措施：  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>字串中的字元  
 字串可以視為 `Char` 值序列，且 `String` 類型具有內建函式，可讓您在字串上執行許多操作 (類似於陣列所允許的操作)。 如 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 中的所有陣列，這些都是以零起始的陣列。 您可以透過 `Chars` 屬性參考字串中的特殊字元 ，讓您能夠依字元在字串中的出現位置存取該字元。 例如:   
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 在上述範例中，字串的 `Chars` 屬性會傳回字串中的第四個字元，也就是 `D`，並將其指派給 `myChar`。 您也可以透過 `Length` 屬性取得特定字串的長度。 如果您需要在字串上執行多個陣列類型操作，您可以使用字串的 `ToCharArray` 函式將它轉換為 `Char` 執行個體陣列。 例如:   
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 變數 `myArray` 現在包含 `Char` 值的陣列，每個都代表 `myString` 的一個字元。  
  
## <a name="the-immutability-of-strings"></a>字串的不變性  
 字串是*不可變*，其值無法變更一次這表示它已建立。 不過，這不會讓您將多個值指派給一個字串變數。 參考下列範例：  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 在這裡會建立字串變數、指定值，然後變更其值。  
  
 更具體來說，在第一行中，會建立類型 `String` 的執行個體並提供值 `This string is immutable`。 在此範例的第二行，建立新執行個體並指定值 `Or is it?`，且字串變數會捨棄其對第一個執行個體的參考，並儲存新執行個體的參考。  
  
 不同於其他內建資料類型，`String` 是參考類型。 將參考類型的變數做為引數傳遞給函式或副程式時，會傳遞儲存資料的記憶體位址的參考，而不是字串的實際值。 因此在前一個範例中，變數的名稱維持不變，但是它指向 `String` 類別的全新和不同的執行個體，其中包含新值。  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [String 資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Char 資料類型](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [基本字串作業](../../../../standard/base-types/basic-string-operations.md)
