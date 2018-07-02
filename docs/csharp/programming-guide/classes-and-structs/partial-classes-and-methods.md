---
title: 部分類別和方法 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- partial methods [C#]
- partial classes [C#]
- C# language, partial classes and methods
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
ms.openlocfilehash: aa0baf50b9e4aabf0bb5dfa229ecd245db391a8b
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314730"
---
# <a name="partial-classes-and-methods-c-programming-guide"></a>部分類別和方法 (C# 程式設計手冊)
有可能將 [class](../../../csharp/language-reference/keywords/class.md)、[struct](../../../csharp/language-reference/keywords/struct.md)、[interface](../../../csharp/language-reference/keywords/interface.md) 或方法的定義，分割到兩個以上的來源檔案。 每一個來源檔案都包含型別或方法定義的一個區段，而當編譯應用程式時，就會將所有區段結合起來。  
  
## <a name="partial-classes"></a>部分類別  
 有幾種情況需要分割類別定義︰  
  
-   處理大型專案時，將類別分散到不同的檔案可讓多位程式設計人員同時處理它。  
  
-   處理自動產生的來源時，程式碼可以加入類別，不必重新建立來源檔案。 Visual Studio 建立 Windows Forms、Webb 服務包裝函式程式碼等等時，會使用這種方法。 您可以建立使用這些類別的程式碼，不必修改 Visual Studio 建立的檔案。  
  
-   若要分割類別定義，請使用 [partial](../../../csharp/language-reference/keywords/partial-type.md) 關鍵字修飾詞，如下所示︰  
  
 [!code-csharp[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_1.cs)]  
  
 `partial` 關鍵字表示可在命名空間中定義類別、結構或介面的其他組件。 所有組件都必須使用 `partial` 關鍵字。 所有組件都必須可在編譯時間取得，以形成最後的型別。 所有組件必須有相同的存取範圍，例如 `public`、`private` 等等。  
  
 如果任何組件宣告為抽象的，則整個型別視為抽象的。 如果任何組件宣告為密封的，則整個型別視為密封的。 如果任何組件宣告基底型別，則整個型別會繼承該類別。  
  
 指定基底類別的所有組件必須一致，但省略基底類別的組件仍會繼承基底型別。 組件可以指定不同的基底介面，而最後的型別會實作部分宣告列出的所有介面。 在部分定義中宣告的任何類別、結構或介面成員都可供所有其他組件使用。 最後的型別是所有組件在編譯時期的組合。  
  
> [!NOTE]
>  `partial` 修飾詞不提供委派或列舉宣告使用。  
  
 下例會顯示可為部分的巢狀型別，即使巢狀型別所在的型別不是部分本身。  
  
 [!code-csharp[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_2.cs)]  
  
 在編譯時期會合併部分型別定義的屬性。 例如，請考慮下列宣告：  
  
 [!code-csharp[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_3.cs)]  
  
 它們與下列宣告相同：  
  
 [!code-csharp[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_4.cs)]  
  
 以下是合併自所有部分型別定義︰  
  
-   XML 註解  
  
-   介面  
  
-   泛型型別參數屬性  
  
-   類別屬性  
  
-   成員  
  
 例如，請考慮下列宣告：  
  
 [!code-csharp[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_5.cs)]  
  
 它們與下列宣告相同：  
  
 [!code-csharp[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_6.cs)]  
  
### <a name="restrictions"></a>限制  
 當您處理部分類別定義時要遵循數項規則︰  
  
-   表示同型別組件的所有部分型別定義都必須使用 `partial` 來修改。 例如，下列類別宣告會產生錯誤︰  
  
     [!code-csharp[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_7.cs)]  
  
-   `partial` 修飾詞只能緊貼在關鍵字 `class`、`struct` 或 `interface` 之前。  
  
-   部分型別定義中允許巢狀部分型別，如下例所示︰  
  
     [!code-csharp[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_8.cs)]  
  
-   表示同型別組件的所有部分型別定義都必須在相同的組件和相同的模組 (.exe 或 .dll 檔案) 中定義。 部分定義不能跨越多個模組。  
  
-   所有部分型別定義中的類別名稱和泛型型別參數必須相符。 泛型型別可以是部分的。 每個部分宣告都必須以相同的順序使用相同的參數名稱。  
  
-   下列部分型別定義中的關鍵字是選擇項目，但如果出現在一個部分型別定義中，即不能與同類型的另一個部分定義中指定的關鍵字衝突︰  
  
    -   [public](../../../csharp/language-reference/keywords/public.md)  
  
    -   [private](../../../csharp/language-reference/keywords/private.md)  
  
    -   [protected](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [internal](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   基底類別  
  
    -   [new](../../../csharp/language-reference/keywords/new.md) 修飾詞 (巢狀組件)  
  
    -   泛型條件約束  
  
         如需詳細資訊，請參閱[型別參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。  
  
## <a name="example-1"></a>範例 1  
  
### <a name="description"></a>描述  
 在下例中，類別的欄位和建構函式 `CoOrds`，已在一個部分類別定義中宣告，而成員 `PrintCoOrds`，則是在另一個部分類別定義中宣告。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_9.cs)]  
  
## <a name="example-2"></a>範例 2  
  
### <a name="description"></a>描述  
 下例範例示範您也可以開發部分結構和介面。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/partial-classes-and-methods_10.cs)]  
  
## <a name="partial-methods"></a>部分方法  
 部分類別或結構可包含部分方法。 類別的一個組件包含方法簽章。 選擇性實作可在相同組件或另一個組件中定義。 如未提供實作，則會在編譯時期移除方法和方法的所有呼叫。  
  
 部分方法可實作類別的一個組件，以定義類似事件的方法。 實作該類別的其他組件，則可決定是否實作該方法。 如未實作方法，則編譯器會移除方法簽章和方法的所有呼叫。 方法的呼叫，包括評估呼叫中的引數可能發生的任何結果，在執行階段沒有任何作用。 因此，部分類別中的任何程式碼都可以自由使用部分方法，即使不提供實作。 如已呼叫、但未實作方法，就不會產生任何編譯時期或執行階段錯誤。  
  
 將部分方法當成自訂產生的程式碼的方式特別有用。 它們允許保留方法名稱和簽章，如此一來，產生的程式碼就可以呼叫方法，但開發人員可以決定是否實作方法。 部分方法可讓程式碼產生器建立的程式碼和開發人員人工建立的程式碼一起運作，不需要執行階段成本，這一點更像部分類別。  
  
 部分方法宣告包含兩個部分︰定義和實作。 這些可能位在部分類別的不同組件或相同組件中。 如不實作任何宣告，則編譯器會最佳化定義宣告和方法的所有呼叫。  
  
```csharp  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   部分方法宣告必須以內容關鍵字 [partial](../../../csharp/language-reference/keywords/partial-type.md) 開頭，且此方法必須傳回 [void](../../../csharp/language-reference/keywords/void.md)。  
  
-   部分方法可以有 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) 或 [ref](../../../csharp/language-reference/keywords/ref.md)，但不能有 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數。  
  
-   部分方法為隱含的[私用](../../../csharp/language-reference/keywords/private.md)，因此它們不能為[虛擬](../../../csharp/language-reference/keywords/virtual.md)。  
  
-   部分方法不可以是 [extern](../../../csharp/language-reference/keywords/extern.md)，因為有主體會決定它們要定義或實作。  
  
-   部分方法可以有 [static](../../../csharp/language-reference/keywords/static.md) 和 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 修飾詞。  
  
-   部分方法可以為泛型。 條件約束放在定義部分方法宣告中，可選擇性地在實作宣告時重複。 參數和型別參數名稱在實作宣告中不必相同，但在定義宣告中要相同。  
  
-   您可以[委派](../../../csharp/language-reference/keywords/delegate.md)已定義且實作的部分方法，但不能委派只經定義的部分方法。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [結構](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [介面](../../../csharp/programming-guide/interfaces/index.md)  
 [partial (型別)](../../../csharp/language-reference/keywords/partial-type.md)
