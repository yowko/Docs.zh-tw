---
title: "如何：在十六進位字串和數字類型間轉換 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: bbc5a3aebfd0086388a4a5b020ad8679395cb74b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>如何：在十六進位字串和數字類型間轉換 (C# 程式設計手冊)
這些範例示範如何執行下列工作：  
  
-   取得[字串](../../../csharp/language-reference/keywords/string.md)中每個字元的十六進位值。  
  
-   取十六進位字串中對應每個值的 [char](../../../csharp/language-reference/keywords/char.md)。  
  
-   將十六進位 `string` 轉換成 [int](../../../csharp/language-reference/keywords/int.md)。  
  
-   將十六進位 `string` 轉換成 [float](../../../csharp/language-reference/keywords/float.md)。  
  
-   將 [byte](../../../csharp/language-reference/keywords/byte.md) 陣列轉換成十六進位 `string`。  
  
## <a name="example"></a>範例  
 本例以 `string` 輸出每個字元的十六進位值。 它會先將 `string` 剖析成字元陣列。 接著在每個字元上呼叫 <xref:System.Convert.ToInt32%28System.Char%29>，以取得其數值。 最後，在 `string` 中將數字格式化為十六進位表示法。  
  
 [!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a>範例  
 本例會剖析十六進位值的 `string`，並輸出對應至每個十六進位值的字元。 它會先呼叫 [Split(Char\[\])](xref:System.String.Split(System.Char[])) 方法，取得每個十六進位值，作為陣列中的個別 `string`。 接著呼叫 <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29>，以將十六進位值轉換為呈現為 [int](../../../csharp/language-reference/keywords/int.md) 的十進位值。 它會顯示兩種不同取得對應該字元程式碼字元的方式。 第一個技巧使用 <xref:System.Char.ConvertFromUtf32%28System.Int32%29>，傳回對應於整數引數作為 `string` 的字元。 第二個技巧將 `int` 明確轉換成 [char](../../../csharp/language-reference/keywords/char.md)。  
  
 [!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a>範例  
 這個範例示範另一種將十六進位 `string` 轉換為整數的方式，方法是呼叫 <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> 方法。  
  
 [!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 <xref:System.BitConverter?displayProperty=fullName> 類別和 <xref:System.Int32.Parse%2A?displayProperty=fullName> 方法，以將十六進位 `string` 轉換為 [float](../../../csharp/language-reference/keywords/float.md)。  
  
 [!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a>範例  
 下例示範如何使用 <xref:System.BitConverter?displayProperty=fullName> 類別，將 [byte](../../../csharp/language-reference/keywords/byte.md) 陣列轉換為十六進位的字串。  
  
 [!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)   
 [類型](../../../csharp/programming-guide/types/index.md)   
 [如何：判斷字串是否表示數值](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)

