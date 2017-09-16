---
title: "如何：使用全域命名空間別名 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
caps.latest.revision: 23
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1252fc107d46b1d3a1cbef0a61708edc57253910
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a>如何：使用全域命名空間別名 (C# 程式設計手冊)
成員可能會被具有相同名稱的另一個實體隱藏時，能夠存取全域[命名空間](../../../csharp/language-reference/keywords/namespace.md)中的成員就很有用。  
  
 例如，在下列程式碼中，`Console` 會解析成 `TestApp.Console`，而非 <xref:System> 命名空間中的 `Console` 類型。  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-cs[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 使用 `System.Console` 仍會導致錯誤，因為 `TestApp.System` 類別隱藏了 `System` 命名空間：  
  
 [!code-cs[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 不過，您可以使用 `global::System.Console` 來暫時解決這個錯誤，如下所示：  
  
 [!code-cs[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 左邊的識別項是 `global` 時，搜尋正確的識別項會從全域命名空間開始。 例如，下列宣告將參考 `TestApp` 作為全域空間的成員。  
  
 [!code-cs[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 很明顯地，不建議您建立自己的命名空間 `System`，而您也不太可能會遇到任何發生這種狀況的程式碼。 不過，在較大型專案中，命名空間重複項很可能會以某種形式或其他形式出現。 在這些情況下，全域命名空間限定詞可確保您能夠指定根命名空間。  
  
## <a name="example"></a>範例  
 在此範例中，`System` 命名空間用來包含 `TestClass` 類別；因此，`global::System.Console` 必須用來參考 `System` 命名空間所隱藏的 `System.Console` 類別。 此外，`colAlias` 別名用來參考 `System.Collections` 命名空間；因此，<xref:System.Collections.Hashtable?displayProperty=fullName> 的執行個體會使用此別名而不是命名空間來建立。  
  
 [!code-cs[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
 **A 1**  
**B 2**  
**C 3**   
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [命名空間](../../../csharp/programming-guide/namespaces/index.md)   
 [.運算子](../../../csharp/language-reference/operators/member-access-operator.md)   
 [:: 運算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [extern](../../../csharp/language-reference/keywords/extern.md)

