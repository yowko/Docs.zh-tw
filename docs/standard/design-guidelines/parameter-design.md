---
title: 參數設計
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 707ae48be3f45d82ed3819f943dc5ba3743172f3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828799"
---
# <a name="parameter-design"></a>參數設計

本節提供有關參數設計的廣泛指導方針，包括具有檢查引數之指導方針的章節。 此外，您應該參考 [具名引數](naming-parameters.md)中所述的指導方針。

 ✔️會使用提供成員所需功能的最不衍生參數類型。

 例如，假設您想要設計一個列舉集合的方法，並將每個專案列印到主控台。 例如，這種方法應該採用做 <xref:System.Collections.IEnumerable> 為參數，而不是 <xref:System.Collections.ArrayList> 或 <xref:System.Collections.IList> 。

 ❌ 請勿使用保留的參數。

 如果在未來的版本中需要更多的成員輸入，可以加入新的多載。

 ❌ 沒有公開公開的方法，這些方法會採用指標、指標陣列或多維陣列作為參數。

 指標和多維陣列相當難以正確使用。 在幾乎所有情況下，Api 都可以重新設計，以避免將這些類型視為參數。

 ✔️請將所有參數都放在所有的傳 `out` 值和 `ref` 參數之後 (排除參數陣列) ，即使這會導致多載之間的參數順序不一致 (看到 [成員](member-overloading.md) 多載) 。

 這些 `out` 參數可以視為額外的傳回值，並將它們群組在一起，讓方法簽章更容易理解。

 覆寫成員或實介面成員時，✔️在具名引數中是一致的。

 這會更妥善地傳達方法之間的關聯性。

### <a name="choosing-between-enum-and-boolean-parameters"></a>選擇列舉和布林值參數  
 如果成員另有兩個或多個布林值參數，✔️請使用列舉。

 ❌ 除非您絕對確定永遠不需要兩個以上的值，否則請勿使用布林值。

 列舉可讓您有一些空間可讓您在未來加入值，但您應該留意到 [列舉設計](enum.md)中所述，將值新增至列舉的所有含意。

 ✔️考慮將布林值用於真正是雙狀態值的函式參數，而且只是用來初始化布林值屬性。

### <a name="validating-arguments"></a>驗證引數
 ✔️確實會驗證傳遞給公用、受保護或明確執行之成員的引數。 <xref:System.ArgumentException?displayProperty=nameWithType>如果驗證失敗，則擲回或其中一個子類別。

 請注意，實際的驗證不一定要在公用或受保護成員本身發生。 它可能會在某個私用或內部常式的較低層級發生。 主要點是公開給終端使用者的整個介面區會檢查引數。

 <xref:System.ArgumentNullException>如果傳遞了 null 引數，而且該成員不支援 null 引數，✔️會擲回。

 ✔️驗證列舉參數。

 請勿假設列舉引數會在列舉所定義的範圍內。 CLR 允許將任何整數值轉換為列舉值，即使值未在列舉中定義。

 ❌ 請勿用於 <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> 列舉範圍檢查。

 ✔️請注意，可變動的引數在驗證之後可能已變更。

 如果成員具有安全性敏感性，建議您建立複本，然後驗證並處理引數。

### <a name="parameter-passing"></a>參數傳遞
 從架構設計工具的觀點來看，有三個主要的參數群組：傳值參數、 `ref` 參數和 `out` 參數。

 當引數透過傳值參數傳遞時，該成員會收到傳入的實際引數複本。 如果引數是實值型別，則會將引數的複本放在堆疊上。 如果引數是參考型別，則會在堆疊上放置參考的複本。 最熱門 CLR 語言（例如 c #、VB.NET 和 c + +）預設為以傳值方式傳遞參數。

 當引數透過參數傳遞時 `ref` ，該成員會收到傳入的實際引數參考。 如果引數是實值型別，則會將引數的參考放置在堆疊上。 如果引數是參考型別，則參考的參考會放在堆疊上。 `Ref` 參數可以用來允許成員修改呼叫端所傳遞的引數。

 `Out` 參數類似于 `ref` 參數，但有一些小差異。 此參數一開始視為未指派，且在指派一些值之前無法在成員主體中讀取。 此外，必須在成員傳回之前，將某個值指派給參數。

 ❌ 請避免使用 `out` 或 `ref` 參數。

 使用 `out` 或 `ref` 參數需要使用指標的經驗、瞭解實值型別和參考型別有何不同，以及處理具有多個傳回值的方法。 此外，和參數之間的差異 `out` 並 `ref` 不大易懂。 設計一般物件的架構架構設計人員不應預期使用者使用 `out` 或 `ref` 參數。

 ❌ 請勿以傳址方式傳遞參考型別。

 規則有一些有限的例外狀況，例如可用來交換參考的方法。

### <a name="members-with-variable-number-of-parameters"></a>具有可變參數數目的成員
 可採用可變數目引數的成員會藉由提供陣列參數來表示。 例如， <xref:System.String> 提供下列方法：

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 然後，使用者可以呼叫方法，如下所示 <xref:System.String.Format%2A?displayProperty=nameWithType> ：

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 將 c # params 關鍵字加入至陣列參數，會將參數變更為所謂的 params 陣列參數，並提供建立暫存陣列的快捷方式。

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 這麼做可讓使用者藉由直接在引數清單中傳遞陣列元素來呼叫方法。

 `String.Format("File {0} not found in {1}",filename,directory);`

 請注意，您只能將 params 關鍵字加入至參數清單中的最後一個參數。

 如果您希望終端使用者傳遞具有少量專案的陣列，✔️可考慮將 params 關鍵字加入至陣列參數。 如果預期會在常見的案例中傳遞大量元素，則使用者可能不會以內嵌方式傳遞這些元素，因此不需要 params 關鍵字。

 ❌ 如果呼叫端幾乎一律具有已在陣列中的輸入，請避免使用 params 陣列。

 例如，具有位元組陣列參數的成員幾乎不會藉由傳遞個別位元組來呼叫。 基於這個理由，.NET Framework 中的位元組陣列參數不使用 params 關鍵字。

 ❌ 如果接受 params 陣列參數的成員修改陣列，請不要使用 params 陣列。

 因為許多編譯器會將成員的引數轉換成呼叫位置上的暫存陣列，所以陣列可能是暫時的物件，因此對陣列所做的任何修改都將遺失。

 ✔️請考慮在簡單多載中使用 params 關鍵字，即使更複雜的多載無法使用它也是一樣。

 如果使用者在一個多載中有參數陣列的值，即使它不在所有多載中，也會詢問您。

 ✔️請嘗試排序參數，讓它可以使用 params 關鍵字。

 ✔️考慮提供特殊的多載和程式碼路徑，以便在極具效能效益的 Api 中使用少量引數的呼叫。

 這可以避免在使用少量引數呼叫 API 時建立陣列物件。 藉由採用單一形式的陣列參數並加入數值尾碼，形成參數的名稱。

 只有當您要在整個程式碼路徑中使用特殊案例，而不只是建立陣列並呼叫更一般的方法時，才應該這樣做。

 ✔️請注意，null 可以做為 params 陣列引數傳遞。

 在處理之前，您應該先驗證陣列是否為非 null。

 ❌ 請勿使用 `varargs` 方法，也稱為省略號。

 某些 CLR 語言（例如 c + +）支援傳遞變數參數清單（稱為方法）的替代慣例 `varargs` 。 慣例不應用於架構，因為它不符合 CLS 標準。

### <a name="pointer-parameters"></a>指標參數
 一般而言，指標不應該出現在設計完善之 managed 程式碼架構的公用介面區中。 大部分的情況下，都應該封裝指標。 不過，在某些情況下，基於互通性原因需要指標，而在這種情況下使用指標是適當的。

 因為指標不符合 CLS 規範，所以✔️確實提供任何採用指標引數之成員的替代方法。

 ❌ 避免對指標引數進行昂貴的引數檢查。

 當您設計具有指標的成員時，✔️會遵循一般指標相關慣例。

 例如，不需要傳遞開始索引，因為可以使用簡單的指標算術來完成相同的結果。

 *部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [成員設計方針](member.md)
- [架構設計指導方針](index.md)
