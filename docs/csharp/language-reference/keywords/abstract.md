---
title: "abstract (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords: abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd26583c42302d8ce9ba4dd22119713548111236
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="abstract-c-reference"></a>abstract (C# 參考)
`abstract` 修飾詞表示要修改的項目具有遺失或不完整的實作。 抽象修飾詞可以與類別、方法、屬性、索引子和事件搭配使用。 在類別宣告中使用 `abstract` 修飾詞，來表示某一類別只是要作為其他類別的基底類別。 標記為抽象或包括在抽象類別中的成員，必須由衍生自抽象類別的類別所實作。  
  
## <a name="example"></a>範例  
 在此範例中，`Square` 類別必須提供 `Area` 的實作，因為它繼承自 `ShapesClass`：  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 抽象類別具有下列功能：  
  
-   抽象類別無法具現化。  
  
-   抽象類別可能包含抽象方法和存取子。  
  
-   因為兩個修飾詞的意義相反，所以無法使用 [sealed](../../../csharp/language-reference/keywords/sealed.md) 修飾詞來修改抽象類別。 `sealed` 修飾詞可防止繼承類別，而 `abstract` 修飾詞需要繼承類別。  
  
-   衍生自抽象類別的非抽象類別必須包括所有繼承抽象方法和存取子的實際實作。  
  
 在方法或屬性宣告中使用 `abstract` 修飾詞，表示方法或屬性未包含實作。  
  
 抽象方法具有下列功能：  
  
-   抽象方法隱含為虛擬方法。  
  
-   只有在抽象類別中才允許抽象方法宣告。  
  
-   因為抽象方法宣告未提供實際實作，所以沒有方法主體；方法宣告的結尾就是分號，而且簽章後面沒有大括號 ({ })。 例如:   
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     覆寫方法 [override](../../../csharp/language-reference/keywords/override.md) 提供實作，而這個方法是非抽象類別的成員。  
  
-   在抽象方法宣告中使用 [static](../../../csharp/language-reference/keywords/static.md) 或 [virtual](../../../csharp/language-reference/keywords/virtual.md) 修飾詞是錯誤的。  
  
 抽象屬性的行為類似抽象方法，但宣告和引動過程語法的差異除外。  
  
-   在靜態屬性上使用 `abstract` 修飾詞是錯誤的。  
  
-   包括使用 [override](../../../csharp/language-reference/keywords/override.md) 修飾詞的屬性宣告，即可覆寫衍生類別中的抽象繼承屬性。  
  
 如需抽象類別的詳細資訊，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
 抽象類別必須提供所有介面成員的實作。  
  
 實作介面的抽象類別可能會將介面方法對應至抽象方法。 例如:   
  
 [!code-csharp[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## <a name="example"></a>範例  
 在此範例中，`DerivedClass` 類別衍生自抽象類別 `BaseClass`。 抽象類別包含抽象方法 `AbstractMethod` 和兩個抽象屬性：`X` 和 `Y`。  
  
 [!code-csharp[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 在上述範例中，如果您嘗試使用如下的陳述式來具現化抽象類別︰  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
您會收到錯誤，指出編譯器無法建立抽象類別 'BaseClass' 的執行個體。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)
