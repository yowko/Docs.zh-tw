---
title: Unsafe 程式碼和指標 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: b57a6f607dbdbc84c60889a5ce2b1e3c33d7f435
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331600"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Unsafe 程式碼和指標 (C# 程式設計手冊)
為了維護型別安全和安全性，C# 預設不支援指標算術。 不過，藉由使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字，即可定義能在其中使用指標的不安全內容。 如需指標的詳細資訊，請參閱[指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)主題。  
  
> [!NOTE]
>  在 Common Language Runtime (CLR) 中，不安全的程式碼是指無法驗證的程式碼。 C# 中不安全的程式碼不一定具有危險性，這不過是其安全性無法由 CLR 驗證的程式碼。 因此，CLR 只會執行完全受信任之組件中不安全的程式碼。 如果您使用不安全的程式碼，則有責任確保程式碼不會帶來安全性風險或造成指標錯誤。  
  
## <a name="unsafe-code-overview"></a>不安全的程式碼概觀  
 不安全的程式碼具有下列屬性：  
  
-   方法、類型和程式碼區塊可以定義為不安全。  
  
-   在某些情況下，不安全的程式碼可能會藉由移除陣列界限檢查，來提升應用程式的效能。  
  
-   當您呼叫需要指標的原生函式時，需要不安全的程式碼。  
  
-   使用不安全的程式碼會帶來安全性和穩定性風險。  
  
-   為了讓 C# 編譯不安全的程式碼，必須以 [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 來編譯應用程式。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊，請參閱:  
  
-   [指標型別](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [固定大小的緩衝區](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [如何：使用指標複製位元組陣列](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)
