---
title: 使用命名空間 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 06ebb9edfaf4753b98c3305a90b52e93ee7b4486
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796631"
---
# <a name="using-namespaces-c-programming-guide"></a>使用命名空間 (C# 程式設計手冊)

C# 程式內大量使用命名空間的原因有兩個。 首先，.NET Framework 類別會使用命名空間來組織其多種類別。 其次，宣告您自己的命名空間，有助於在較大型的程式設計專案中控制類別和方法名稱的範圍。  
  
## <a name="accessing-namespaces"></a>存取命名空間

 大部分 C# 應用程式的開頭為 `using` 指示詞區段。 本節列出應用程式經常使用的命名空間，並讓程式設計人員每次使用其內包含的方法時不需要指定完整名稱。  
  
 例如，包含下行：  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 在程式的開始，程式設計人員可以使用下列程式碼：  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 而非：  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>命名空間別名

 您也可以使用 [`using` 指示詞](../../language-reference/keywords/using-directive.md)來建立命名空間的別名。 使用[命名空間別名限定詞`::`](../../language-reference/operators/namespace-alias-qualifier.md)來存取別名命名空間的成員。 下列範例示範如何建立及使用命名空間別名：
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a>使用命名空間來控制範圍

 `namespace` 關鍵字用來宣告範圍。 在專案內建立範圍的能力有助於組織程式碼，並可讓您建立全域唯一類型。 在下列範例中，標題為 `SampleClass` 的類別定義於兩個命名空間中，而其中一個命名空間巢狀於另一個命名空間內。 [成員存取運算子 `.`](../../language-reference/operators/member-access-operators.md#member-access-operator-) 用來區分呼叫的方法。  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>完整名稱

 命名空間和類型具有指出邏輯階層之完整名稱所描述的唯一標題。 例如，`A.B` 陳述式表示 `A` 是命名空間或類型的名稱，而 `B` 巢狀於其內。  
  
 在下列範例中，有巢狀類別和命名空間。 完整名稱會表示為每個實體後面的註解。  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 在先前的程式碼區段中：  
  
- `N1` 命名空間是全域命名空間的成員。 其完整名稱是 `N1`。  
  
- `N2` 命名空間是 `N1` 的成員。 其完整名稱是 `N1.N2`。  
  
- `C1` 類別是 `N1` 的成員。 其完整名稱是 `N1.C1`。  
  
- 這個程式碼使用類別名稱 `C2` 兩次。 不過，完整名稱是唯一的。 第一個 `C2` 執行個體宣告於 `C1` 內；因此，其完整名稱是 `N1.C1.C2`。 第二個 `C2` 執行個體宣告於 `N2` 命名空間內；因此，其完整名稱是 `N1.N2.C2`。  
  
 使用先前的程式碼區段，即可將新的類別成員 `C3` 新增至命名空間 `N1.N2`，如下所示：  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 在一般情況下，使用 `::` 來參考命名空間別名，或使用 `global::` 參考全域命名空間，以及使用 `.` 來限定類型或成員。  
  
 搭配使用 `::` 與參考型別而非命名空間的別名是錯誤的。 例如：  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 請記住，`global` 這個單字不是預先定義別名，因此，`global.X` 沒有任何特殊意義。 只有在與 `::` 搭配使用時，才會取得特殊意義。  
  
 因為 `global::` 一律會參考全域命名空間，而不是別名，所以如果您定義名為 global 的別名，就會產生編譯器警告 CS0440。 例如，下行會產生警告：  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 搭配使用 `::` 與別名是不錯的想法，並且可避免非預期導入額外的類型。 例如，請考慮使用以下範例：  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 這會適用，但是如果後續引進名為 `Alias` 的類型，`Alias.` 會改為繫結至該類型。 使用 `Alias::Exception` 來確保將 `Alias` 視為命名空間別名，而非型別。  
  
 請參閱主題[如何：使用全域命名空間別名](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)，以取得 `global` 別名的詳細資訊。  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [命名空間](../../../csharp/programming-guide/namespaces/index.md)
- [. 運算子](../../../csharp/language-reference/operators/member-access-operators.md#member-access-operator-)
- [:: 運算子](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [外部別名](../../../csharp/language-reference/keywords/extern-alias.md)
