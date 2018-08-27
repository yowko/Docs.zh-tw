---
title: 命名空間 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, namespaces
- namespaces [C#]
ms.assetid: b1c4ab46-3fad-4ffa-9deb-dd50a2d8c65a
ms.openlocfilehash: 60e4c6e98ca9e71d1a095a0c7ee1df6be6d13f4b
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934869"
---
# <a name="namespaces-c-programming-guide"></a>命名空間 (C# 程式設計手冊)
C# 程式設計大量使用命名空間的原因有兩個。 首先，.NET Framework 會使用命名空間組織其多種類別，如下所示：  
  
 [!code-csharp[csProgGuide#22](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_1.cs)]  
  
 `System` 是命名空間，而 `Console` 是該命名空間中的類別。 您可以使用 `using` 關鍵字，如此就不需要完整名稱，如下列範例所示：  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_2.cs)]  
  
 [!code-csharp[csProgGuide#25](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/index_3.cs)]  
  
 如需詳細資訊，請參閱 [using 陳述式](../../../csharp/language-reference/keywords/using-directive.md)。  
  
 其次，宣告您自己的命名空間，將有助於在較大型的程式設計專案中控制類別和方法名稱的範圍。 請使用 [namespace](../../../csharp/language-reference/keywords/namespace.md) 關鍵字宣告命名空間，如下列範例所示：  
  
 [!code-csharp[csProgGuideNamespaces#6](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/index_4.cs)]  
  
## <a name="namespaces-overview"></a>命名空間概觀  
 命名空間具有下列屬性：  
  
-   命名空間可組織大型程式碼專案。  
  
-   命名空間會使用 `.` 運算子分隔。  
  
-   `using directive` 讓您不需要指定每個類別的命名空間名稱。  
  
-   `global` 命名空間是「根」命名空間：`global::System` 一律會參考 .NET Framework 命名空間 `System`。  
  
## <a name="related-sections"></a>相關章節  
 如需命名空間的詳細資訊，請參閱下列主題：  
  
-   [使用命名空間](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
  
-   [如何：使用全域命名空間別名](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
-   [如何：使用 My 命名空間](../../../csharp/programming-guide/namespaces/how-to-use-the-my-namespace.md)  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [using 指示詞](../../../csharp/language-reference/keywords/using-directive.md)  
 [:: 運算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [.運算子](../../../csharp/language-reference/operators/member-access-operator.md)
