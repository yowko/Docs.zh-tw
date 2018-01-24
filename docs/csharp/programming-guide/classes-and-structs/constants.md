---
title: "常數 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 86c9371a6a82c4034b7bdf279e7b205cfcc84bea
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="constants-c-programming-guide"></a>常數 (C# 程式設計手冊)
常數是在編譯時期已知且不會在程式存留期變更的不可變值。 常數是使用 [const](../../../csharp/language-reference/keywords/const.md) 修飾詞所宣告。 有 C# 內建型別 (不含 <xref:System.Object?displayProperty=nameWithType>) 才能宣告為 `const`。 如需內建類型的清單，請參閱[內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)。 使用者定義型別 (包括類別、結構和陣列) 不能是 `const`。 使用 [readonly](../../../csharp/language-reference/keywords/readonly.md) 修飾詞來建立在執行階段一次初始化的類別、結構或陣列 (例如在建構函式中)，因而無法進行變更。  
  
 C# 不支援 `const` 方法、屬性或事件。  
  
 enum 類型可讓您定義整數內建類型的具名常數 (例如 `int`、`uint`、`long` 等等)。 如需詳細資訊，請參閱 [enum](../../../csharp/language-reference/keywords/enum.md)。  
  
 常數必須在宣告時進行初始化。 例如:   
  
 [!code-csharp[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 在此範例中，`months` 常數一律為 12，而且甚至類別本身也不能進行變更。 事實上，編譯器在 C# 原始程式碼中遇到常數識別碼 (例如　`months`) 時，會直接將常值替代為它所產生的中繼語言 (IL) 程式碼。 因為在執行階段沒有與常數相關聯的變數位址，所以無法以傳址方式傳遞 `const` 欄位，而且無法顯示為運算式中的左值。  
  
> [!NOTE]
>  當您參照其他程式碼中所定義的常數值 (例如 DLL) 時，請小心。 如果新版本的 DLL 定義常數的新值，則除非對新版本重新編譯新值，否則您的程式仍會保留舊常值。  
  
 可以同時宣告相同類型的多個常數，例如︰  
  
 [!code-csharp[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 如果用來初始化常數的運算式未建立循環參考，則可以參照另一個常數。 例如:   
  
 [!code-csharp[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 常數可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[protected internal](../../../csharp/language-reference/keywords/protected-internal.md) 或 [private protected](../../../csharp/language-reference/keywords/private-protected.md)。 這些存取修飾詞定義類別使用者如何存取常數。 如需詳細資訊，請參閱[存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 因為類型之所有執行個體的常數值都會相同，所以常數的存取方式就像它們是 [static](../../../csharp/language-reference/keywords/static.md) 欄位一樣。 您未使用 `static` 關鍵字來宣告它們。 不在定義常數之類別中的運算式必須使用類別名稱、句號以及存取常數的常數名稱。 例如:   
  
 [!code-csharp[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [型別](../../../csharp/programming-guide/types/index.md)  
 [readonly](../../../csharp/language-reference/keywords/readonly.md)  
 [Immutability in C# Part One: Kinds of Immutability](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability) (C# 中不變性第一部分：不變性類型)
