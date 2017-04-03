---
title: "外部別名 (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- alias_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 16
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2bda6b652b56c50883700fe5a2a81189dbcb0d2d
ms.lasthandoff: 03/13/2017

---
# <a name="extern-alias-c-reference"></a>外部別名 (C# 參考)
您可能必須參考兩個具有相同完整類型名稱的組件版本。 例如，您可能必須在相同的應用程式中使用兩個或多個組件版本。 藉由使用外部組件別名，來自每個組件的命名空間可包裝在別名所命名的根層級命名空間內，這樣即可讓它們在相同的檔案中使用。  
  
> [!NOTE]
>  [extern](../../../csharp/language-reference/keywords/extern.md) 關鍵字也可作為方法修飾詞，用於宣告以 Unmanaged 程式碼撰寫的方法。  
  
 若要參考兩個具有相同完整類型名稱的組件，則必須在命令提示字元中指定別名，如下所示：  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 這會建立外部別名 `GridV1` 和 `GridV2`。 若要從程式內使用這些別名，請使用 `extern` 關鍵字參考別名。 例如:   
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 每個外部別名宣告會引進另一個與全域命名空間平行 (但不在其內) 的根層級命名空間。 因此，來自每個組件的類型可使用其完整名稱 (源自適當的命名空間別名) 來參考，而不會有模擬兩可的情況。  
  
 在上述範例中，`GridV1::Grid` 是來自 `grid.dll` 的方格控制項，而 `GridV2::Grid` 是來自 `grid20.dll` 的方格控制項。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [命名空間關鍵字](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [:: 運算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [/reference (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
