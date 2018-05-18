---
title: unsafe (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 367a080cf58514b3ffcc30c17d8fe7bb07e0e9ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="unsafe-c-reference"></a>unsafe (C# 參考)
`unsafe` 關鍵字表示任何與指標有關的作業都需要的不安全內容。 如需詳細資訊，請參閱[不安全的程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)。  
  
 您可以在類型或成員的宣告中使用 `unsafe` 修飾詞。 類型或成員的整個文字範圍因此視為不安全內容。 例如，下列是使用 `unsafe` 修飾詞所宣告的方法︰  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 不安全內容的範圍是從參數清單延伸到方法結尾，因此也可以在參數清單中使用指標︰  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 您也可以使用不安全區塊，以在這個區塊內使用不安全程式碼。 例如:   
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 若要編譯不安全的程式碼，您必須指定 [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項。 Common Language Runtime 不會驗證不安全的程式碼。  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [固定大小的緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
