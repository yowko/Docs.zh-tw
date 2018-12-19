---
title: 使用 Override 和 New 關鍵字進行版本控制 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: ddb34fd32d13224faed92bd8ba01933ca19c04a9
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241531"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>使用 Override 和 New 關鍵字進行版本控制 (C# 程式設計手冊)
C# 語言的設計，就是讓不同文件庫的[基底](../../../csharp/language-reference/keywords/base.md)和衍生類別的版本控制能夠發展兼具回溯相容性。 例如，這表示 C# 完全支援在基底[類別](../../../csharp/language-reference/keywords/class.md)中引入與衍生類別成員同名的新成員，不會導致非預期的行為。 這也表示，類別必須明確指出方法是打算覆寫繼承的方法，還是方法是一種新方法，會隱藏名稱相似的繼承方法。  
  
 在 C# 中，衍生類別可以包含與基底類別方法同名的方法。  
  
-   基底類別方法必須定義為 [virtual](../../../csharp/language-reference/keywords/virtual.md)。  
  
-   如果衍生類別中的方法前未加上 [new](../../../csharp/language-reference/keywords/new.md) 或 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字，編譯器就會發出警告，方法會表現為如同有 `new` 關鍵字。  
  
-   如果衍生類別中的方法前面加上 `new` 關鍵字，方法會定義為不受基底類別中的方法影響。  
  
-   如果衍生類別中的方法前面加上 `override` 關鍵字，衍生類別的物件會呼叫該方法，不會呼叫基底類別方法。  
  
-   您可以使用 `base` 關鍵字從衍生類別中呼叫基底類別方法。  
  
-   `override`、`virtual` 和 `new` 關鍵字也可以套用至屬性、索引子和事件。  
  
 C# 方法預設不是虛擬的。 如果方法宣告為虛擬，則繼承該方法的任何類別都可以實作自己的版本。 若要使方法成為虛擬的，基底類別的方法宣告中會使用 `virtual` 修飾詞。 然後，衍生類別可以使用 `override` 關鍵字覆寫基底虛擬方法，或使用 `new` 關鍵字隱藏基底類別中的虛擬方法。 如果不指定 `override` 關鍵字，也不指定 `new` 關鍵字，則編譯器會發出警告，且衍生類別中的方法會隱藏基底類別中的方法。  
  
 為在練習中示範此技巧，假設公司 A 建立了類別 `GraphicsClass`，為您的程式所用。 以下即為 `GraphicsClass`：  
  
 [!code-csharp[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 您的公司使用這個類別，而您用它衍生自己的類別，新增了新的方法︰  
  
 [!code-csharp[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 您的應用程式一直使用正常，直到公司 A 發行新版的 `GraphicsClass`，類似下列程式碼︰  
  
 [!code-csharp[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 新版的 `GraphicsClass` 現在包含一個名為 `DrawRectangle` 的方法。 一開始，一切如常。 新版本與舊版仍為二進位相容。 您部署的所有軟體仍繼續運作，即使這些電腦系統上安裝了新類別。 目前對方法 `DrawRectangle` 的任何呼叫仍繼續參考您衍生類別中的版本。  
  
 不過，一旦使用新版的 `GraphicsClass` 重新編譯應用程式，就會立刻收到編譯器警告 CS0108。 這個警告會通知您，您必須考慮希望 `DrawRectangle` 方法在應用程式中如何表現。  
  
 如果您希望自己的方法覆寫新的基底類別方法，請使用 `override` 關鍵字︰  
  
 [!code-csharp[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 `override` 關鍵字可以確保衍生自 `YourDerivedGraphicsClass` 的所有物件都會使用 `DrawRectangle` 的衍生類別版本。 衍生自 `YourDerivedGraphicsClass` 的物件仍然可以使用 base 關鍵字存取 `DrawRectangle` 的基底類別版本︰  
  
 [!code-csharp[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 如果您不希望自己的方法覆寫新的基底類別方法，請採納下列考量。 為避免混淆兩個方法，您可以重新命名您的方法。 這很耗時間又容易發生錯誤，並且在某些情況下不實際。 不過，如果您的專案相對較小，您可以使用 Visual Studio 的重構選項來重新命名方法。 如需詳細資訊，請參閱[重構類別和型別 (類別設計工具)](/visualstudio/ide/refactoring-classes-and-types-class-designer)。  
  
 或者，您也可以在衍生類別定義中使用關鍵字 `new`，避免出現警告：  
  
 [!code-csharp[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 使用 `new` 關鍵字會通知編譯器，您的定義要隱藏基底類別中包含的定義。 這是預設行為。  
  
## <a name="override-and-method-selection"></a>覆寫和方法選擇  
 在類別上命名方法時，如果有多個方法與呼叫相容，C# 編譯器會選取最好的方法呼叫，例如當有兩種方法同名時，並傳遞與參數相容的參數。 下列方法相容︰  
  
 [!code-csharp[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 在 `Derived` 的執行個體上呼叫 `DoWork` 時，C# 編譯器會先嘗試進行與 `DoWork` 版本相容的呼叫，此版本原是在 `Derived` 上宣告。 覆寫方法不視為在類別中宣告，它們是基底類別中所宣告方法的新實作。 只有當 C# 編譯器無法比對方法呼叫和 `Derived` 中的原始方法時，才會嘗試比對具有相同名稱和相容參數的覆寫方法呼叫。 例如：  
  
 [!code-csharp[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 因為變數 `val` 可以隱含方式轉換為 double，所以 C# 編譯器會呼叫 `DoWork(double)`，不是呼叫 `DoWork(int)`。 有兩種方式可避免這種情況。 首先，避免使用和虛擬方法相同的名稱宣告新方法。 第二，您可以將 `Derived` 執行個體轉換成 `Base`，讓 C# 編譯器搜尋基底類別方法清單，指示它呼叫虛擬方法。 因為方法是虛擬的，所以會在 `Derived` 呼叫 `DoWork(int)` 實作。 例如：  
  
 [!code-csharp[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 如需更多的 `new` 和 `override` 範例，請參閱[了解使用 Override 和 New 關鍵字的時機](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。  
  
## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
