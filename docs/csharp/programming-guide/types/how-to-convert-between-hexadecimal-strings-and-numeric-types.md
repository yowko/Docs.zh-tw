---
title: '如何在十六進位字串和數位類型之間轉換-c # 程式設計指南'
description: 瞭解如何在十六進位字串和數位類型之間轉換。 請參閱程式碼範例，並檢視其他可用的資源。
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 18021156af879f324993beca04531c8a822725db
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513233"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>如何在十六進位字串和數位類型之間轉換 (c # 程式設計手冊) 

這些範例示範如何執行下列工作：  
  
- 取得[字串](../../language-reference/builtin-types/reference-types.md)中每個字元的十六進位值。  
  
- 取十六進位字串中對應每個值的 [char](../../language-reference/builtin-types/char.md)。  
  
- 將十六進位 `string` 轉換成 [int](../../language-reference/builtin-types/integral-numeric-types.md)。  
  
- 將十六進位 `string` 轉換成 [float](../../language-reference/builtin-types/floating-point-numeric-types.md)。  
  
- 將 [byte](../../language-reference/builtin-types/integral-numeric-types.md) 陣列轉換成十六進位 `string`。  
  
## <a name="example"></a>範例  

 本例以 `string` 輸出每個字元的十六進位值。 它會先將 `string` 剖析成字元陣列。 接著在每個字元上呼叫 <xref:System.Convert.ToInt32%28System.Char%29>，以取得其數值。 最後，在 `string` 中將數字格式化為十六進位表示法。  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>範例  

 本例會剖析十六進位值的 `string`，並輸出對應至每個十六進位值的字元。 首先，它會呼叫[Split (Char \[ \]) ](xref:System.String.Split(System.Char[]))方法，以取得每個十六進位值做為陣列中的個別值 `string` 。 然後，它會呼叫 <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> ，將十六進位值轉換成以 [int](../../language-reference/builtin-types/integral-numeric-types.md)表示的十進位值。它會顯示兩種不同的方式來取得對應至該字元碼的字元。 第一個技巧使用 <xref:System.Char.ConvertFromUtf32%28System.Int32%29>，傳回對應於整數引數作為 `string` 的字元。 第二個技巧將 `int` 明確轉換成 [char](../../language-reference/builtin-types/char.md)。  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>範例  

 這個範例示範另一種將十六進位 `string` 轉換為整數的方式，方法是呼叫 <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> 方法。  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>範例  

 下列範例示範如何使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別和 <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> 方法，以將十六進位 `string` 轉換為 [float](../../language-reference/builtin-types/floating-point-numeric-types.md)。  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>範例  

 下例示範如何使用 <xref:System.BitConverter?displayProperty=nameWithType> 類別，將 [byte](../../language-reference/builtin-types/integral-numeric-types.md) 陣列轉換為十六進位的字串。  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>請參閱

- [標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md) \(部分機器翻譯\)
- [類型](./index.md)
- [如何判斷字串是否表示數值](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
