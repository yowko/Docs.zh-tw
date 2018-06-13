---
title: protected (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a3115fe82b452f52ee75cf222302ece0fc67b330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269566"
---
# <a name="protected-c-reference"></a>protected (C# 參考)
`protected` 關鍵字是成員存取修飾詞。 

 > 此頁面涵蓋 `protected` 存取。 `protected` 關鍵字也是屬於 [`protected internal`](./protected-internal.md) 和 [`private protected`](./private-protected.md) 存取修飾詞。 

受保護的成員可在其類別內由衍生類別執行個體存取。 

如需 `protected` 和其他存取修飾詞的比較，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。 
  
## <a name="example"></a>範例  
 只有在存取是透過衍生類別類型進行時，才可以存取衍生類別中屬於基底類別的受保護成員。 例如，請考慮下列程式碼區段：  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 陳述式 `a.x = 10` 會產生錯誤，因為它是在靜態方法 Main 中發出，而不是在類別 B 的執行個體中發出。  
  
 結構成員不可以是受保護的成員，因為無法繼承結構。  
  
## <a name="example"></a>範例  
 在此範例中，`DerivedPoint` 類別衍生自 `Point`。 因此，您可以直接從衍生類別存取基底類別的受保護成員。  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 如果您將 `x` 和 `y` 的存取層級變更為 [private](../../../csharp/language-reference/keywords/private.md)，編譯器會發出錯誤訊息：  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [存取修飾詞](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [internal virtual 關鍵字的安全性考量](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))