---
title: "virtual (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "virtual_CSharpKeyword"
  - "virtual"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "virtual 關鍵字 [C#]"
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# virtual (C# 參考)
`virtual` 關鍵字的用途是修改方法、屬性、索引子 \(Indexer\) 或事件宣告，以及允許在衍生類別 \(Derived Class\) 中予以覆寫。  例如，這個方法可由任一繼承它的類別來覆寫：  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 虛擬成員的實作可以由衍生類別裡的[覆寫成員](../../../csharp/language-reference/keywords/override.md)來更改。  如需如何使用 `virtual` 關鍵字的詳細資訊，請參閱[使用 Override 和 New 關鍵字的進行版本控制](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) 和[了解使用 Override 和 New 關鍵字的時機](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。  
  
## 備註  
 當叫用虛擬方法時，會檢查物件的執行階段型別的覆寫成員。  會呼叫大多數衍生類別裡的覆寫成員，而且如果衍生類別都沒有覆寫成員，這可能是原始成員。  
  
 根據預設，方法是非虛擬的。  您不能覆寫非虛擬方法。  
  
 `virtual` 修飾詞 \(Modifier\) 不能與 `static`、`abstract, private` 或 `override` 等修飾詞一起使用。  下列範例說明虛擬屬性：  
  
 [!code-cs[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 除了宣告和引動過程語法的差異之外，虛擬屬性的行為就像抽象方法一樣。  
  
-   在靜態屬性上使用 `virtual` 修飾詞是錯誤的。  
  
-   衍生類別裡的虛擬繼承屬性可以藉著包含使用 `override` 修飾詞的屬性宣告來覆寫。  
  
## 範例  
 在此範例中，`Shape` 類別包含兩個座標 `x`、`y`，以及 `Area()` 虛擬方法。  不同圖案類別如 `Circle`、`Cylinder` 和 `Sphere` 繼承 `Shape` 類別，並為每一種圖形計算表面積。  每一個衍生類別有其自己的 `Area()` 覆寫實作。  
  
 請注意，繼承的類別`Circle`， `Sphere`，以及`Cylinder`所有使用初始化基底類別中，執行個體建構函式，下列宣告所示。  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 下列程式會計算並顯示適當的區域，每一個圖形，藉由叫用適當的實作的`Area()`方法中，這個方法相關聯的物件。  
  
 [!code-cs[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [多型](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)   
 [override](../../../csharp/language-reference/keywords/override.md)   
 [new](../../../csharp/language-reference/keywords/new.md)