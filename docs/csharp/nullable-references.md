---
title: 可為 Null 的參考型別
description: '本文提供可為 null 的參考型別（在 c # 8.0 中新增）的總覽。 您會了解此功能如何為新及現有的專案，針對 Null 參考例外狀況提供安全。'
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: 9c253d02c287d7a113536ac148b352486d450cc2
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160876"
---
# <a name="nullable-reference-types"></a>可為 Null 的參考型別

C# 8.0 引進**可為 Null 的參考型別**及**不可為 Null 的參考型別**，可讓您針對參考型別變數的屬性撰寫相關重要陳述式：

- **參考不應該是 null**。 當變數不應該是 null 時，編譯器會強制執行規則，以確保能夠安全地取值這些變數，而不需要先檢查它是否為 null：
  - 變數必須初始化為非 Null 值。
  - 變數永遠不可指派 `null` 值。
- **參考可能為 Null**。 當變數可為 Null 時，編譯器會實施不同的規則，確保您已針對 Null 參考正確地進行檢查：
  - 只有在編譯器能保證該值並非為 Null 時，才能對該變數進行取值 (Dereference)。
  - 這些變數可使用預設的 `null` 值初始化，也可以在其他程式碼中指派 `null` 值。

這項新功能提供了在舊版 c # 中處理參考變數的優點，而無法從變數宣告判斷設計意圖。 編譯器不針對參考型別的 Null 參考例外狀況提供安全：

- **參考可為 Null**。 當參考型別初始化為 null，或稍後指派給 null 時，編譯器不會發出警告。 當這些變數是在沒有 null 檢查的情況下進行取值時，編譯器會發出警告。
- **參考已假設為並非 Null**。 編譯器不會在對參考型別進行取值 (Dereference) 時發出任何警告。 如果變數設定為可能為 null 的運算式，則編譯器會發出警告。

這些警告會在編譯時期發出。 編譯器不會在可為 null 的內容中新增任何 null 檢查或其他執行時間結構。 在執行時間，可為 null 的參考與不可為 null 的參考是相等的。

透過新增的可為 Null 參考型別，您可以更清楚地宣告您的意圖。 `null` 值是表示變數並非指向某個值的正確方式。 請不要使用這項功能來從您的程式碼中移除所有 `null` 值。 相反地，您應該對編譯器及其他閱讀您程式碼之開發人員宣告您的意圖。 藉由宣告您的意圖，編譯器會在您撰寫的程式碼與該意圖不一致時通知您。

**可為 Null 參考型別**的語法與[可為 Null 實值型別](language-reference/builtin-types/nullable-value-types.md)語法相同：將 `?` 附加至變數的型別。 例如，下列變數宣告代表可為 Null 字串變數，`name`：

```csharp
string? name;
```

未 `?` 附加至類型名稱的任何變數都是 **不可為 null 的參考型**別。 當您啟用這項功能時，其中包含現有程式碼中的所有參考型別變數。

編譯器會使用靜態分析來判斷可為 Null 參考是否已知並非為 Null。 若您在可為 Null 參考可能為 Null 時對其進行取值 (Dereference)，編譯器會警告您。 您可以在變數名稱後面使用 [容許運算子](language-reference/operators/null-forgiving.md)來覆寫此行為 `!` 。 例如，若您知道 `name` 變數並非為 Null，但編譯器卻發出警告，您可以撰寫下列程式碼來覆寫編譯器的分析：

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>型別的可 NULL 性

任何參考型別都可擁有四種「可 NULL 性」** 中的其中一種，其描述警告產生的時機：

- *不可為 null*： Null 無法指派給此類型的變數。 此型別的變數不需進行 Null 檢查即可進行取值 (Dereference)。
- *Nullable*： null 可以指派給這個型別的變數。 若沒有事先檢查是否為 `null` 即對此型別的變數進行取值 (Dereference)，即會產生警告。
- *無警示*：無警示是 C # 8.0 之前的狀態。 此型別的變數可進行取值或指派，且皆不會產生警告。
- *未知*：通常是因為類型參數的條件約束不會告訴編譯器，類型必須可 *為 null* 或 *不可為 null*。

變數宣告中型別的可 NULL 性會由宣告該變數的「可為 Null 內容」** 控制。

## <a name="nullable-contexts"></a>可為 Null 內容

可為 Null 內容可讓您對編譯器解譯參考型別變數的方式進行細部控制。 任何指定原始程式列的 **可為 null 注釋內容** 為啟用或停用。 您可以將 C # 8.0 編譯器視為在停用的可為 null 內容中編譯您的所有程式碼：任何參考型別都可以是 null。 也可以啟用或停用 **可為 null 的警告內容** 。 可為 Null 警告內容會指定編譯器使用其流程分析所產生的警告。

您可以使用 .csproj 檔案中的元素，為專案設定可為 null 的注釋內容和可為 null 的警告內容 `Nullable` 。 *.csproj* 此項目會設定編譯器解譯型別可 NULL 性的方式及所產生警告。 有效的設定如下：

- `enable`：可為 null 注釋內容已 **啟用**。 可為 Null 警告內容為**啟用**。
  - 參考型別變數 (例如 `string`) 不可為 Null。  啟用所有可 NULL 性警告。
- `warnings`：可為 null 注釋內容已 **停用**。 可為 Null 警告內容為**啟用**。
  - 參考型別變數為遺忘式。 啟用所有可 NULL 性警告。
- `annotations`：可為 null 注釋內容已 **啟用**。 可為 Null 警告內容為**停用**。
  - 例如，參考型別的變數不可以是 null。 停用所有可 NULL 性警告。
- `disable`：可為 null 注釋內容已 **停用**。 可為 Null 警告內容為**停用**。
  - 參考型別變數為遺忘式，與先前版本的 C# 相似。 停用所有可 NULL 性警告。

**範例**：

```xml
<Nullable>enable</Nullable>
```

您也可以使用指示詞，在您專案中的任何位置設定相同內容：

- `#nullable enable`：將可為 null 注釋內容和可為 null 的警告內容設定為 **已啟用**。
- `#nullable disable`：將可為 null 注釋內容和可為 null 警告內容設定為 **停用**。
- `#nullable restore`：將可為 null 注釋內容和可為 null 警告內容還原至專案設定。
- `#nullable disable warnings`：將可為 null 的警告內容設定為 **停用**。
- `#nullable enable warnings`：將可為 null 的警告內容設定為 **已啟用**。
- `#nullable restore warnings`：將可為 null 警告內容還原至專案設定。
- `#nullable disable annotations`：將可為 null 注釋內容設定為 **停用**。
- `#nullable enable annotations`：將可為 null 注釋內容設定為 **已啟用**。
- `#nullable restore annotations`：將批註警告內容還原至專案設定。

預設會 **停用**可為 null 的注釋和警告內容，包括新的專案。 這表示您現有的程式碼在沒有變更的情況下進行編譯，而不會產生任何新的警告。

這些選項提供兩種不同的策略來 [更新現有的程式碼基](nullable-migration-strategies.md) 底，以使用可為 null 的參考型別。

## <a name="nullable-annotation-context"></a>可為 Null 註釋內容

編譯器會在停用的可為 Null 註釋內容中使用下列規則：

- 您無法在停用的內容中宣告可為 Null 參考。
- 您可以為所有參考變數指派 null 值。
- 當對參考型別的變數進行取值 (Dereference) 時，不會產生任何警告。
- Null 容許運算子不可用於停用內容中。

行為與先前版本的 C# 相同。

編譯器會在啟用的可為 Null 註釋內容中使用下列規則：

- 參考型別的任何變數都是**不可為 Null 參考**。
- 任何不可為 Null 參考都可安全地進行取值 (Dereference)。
- 任何可為 Null 參考型別 (在變數宣告中的型別後方標註 `?`) 都可為 Null。 靜態分析會判斷值在取值時是否已知為非 null。 若否，則編譯器會警告您。
- 您可以使用 Null 容許運算子來宣告可為 Null 參考並非為 Null。

在啟用的可為 Null 註釋內容中，`?` 字元會附加至宣告**可為 Null 參考型別**的參考型別。 **Null 容許運算子** `!` 可以附加至運算式，以宣告運算式不是 null。

## <a name="nullable-warning-context"></a>可為 Null 警告內容

可為 Null 警告內容與可為 Null 註釋內容不同。 即使停用新的註釋，仍可啟用警告。 編譯器會使用靜態分析來判斷任何參考的 **Null 狀態**。 當並未「停用」*****可為 Null 警告內容*時，Null 狀態不是**並非為 Null**，就是**可能為 Null**。 若您在編譯器已判斷其**可能為 Null** 時對參考進行取值 (Dereference)，則編譯器會警告您。 除非編譯器可判斷下列兩個狀況的其中一種狀況，否則參考的狀態就會是**可能為 Null**：

1. 變數已確定指派為並非 Null 的值。
1. 變數或運算式已在取值 (Dereference) 之前針對 Null 進行檢查。

當您對可為 null 的警告內容中 **可能為 null** 的變數或運算式進行取值時，編譯器會產生警告。 此外，當在啟用的可為 null 注釋內容中，將不可為 null 的參考型別指派給 **可能為 null** 變數或運算式時，編譯器會產生警告。

## <a name="attributes-describe-apis"></a>屬性描述 Api

您可以將屬性新增至 Api，以提供編譯器有關引數或傳回值何時可以或不能是 null 的詳細資訊。 您可以在本文中以涵蓋 [可為 null 屬性](language-reference/attributes/nullable-analysis.md)的語言參考，深入瞭解這些屬性。 這些屬性會在目前和即將發行的版本中新增至 .NET 程式庫。 最常使用的 Api 會先更新。

## <a name="known-pitfalls"></a>已知陷阱

包含參考型別的陣列和結構是可為 null 的參考型別功能的已知陷阱。

### <a name="structs"></a>結構

包含不可為 null 的參考型別的結構，可讓您 `default` 不需要任何警告即可指派。 請考慮下列範例：

```csharp
using System;

#nullable enable

public struct Student
{
    public string FirstName;
    public string? MiddleName;
    public string LastName;
}

public static class Program
{
    public static void PrintStudent(Student student)
    {
        Console.WriteLine($"First name: {student.FirstName.ToUpper()}");
        Console.WriteLine($"Middle name: {student.MiddleName.ToUpper()}");
        Console.WriteLine($"Last name: {student.LastName.ToUpper()}");
    }

    public static void Main() => PrintStudent(default);
}
```

在上述範例中，在 `PrintStudent(default)` 不可為 null 的參考型別和為 null 時，不會出現警告 `FirstName` `LastName` 。

另一個更常見的情況是當您處理泛型結構時。 請考慮下列範例：

```csharp
#nullable enable

public struct Foo<T>
{
    public T Bar { get; set; }
}

public static class Program
{
    public static void Main()
    {
        string s = default(Foo<string>).Bar;
    }
}
```

在上述範例中，屬性 `Bar` 會 `null` 在執行時間，而且會指派給不可為 null 的字串，而不會出現任何警告。

### <a name="arrays"></a>陣列

陣列也是可為 null 的參考型別的已知缺陷。 請看看下列未產生任何警告的範例：

```csharp
using System;

#nullable enable

public static class Program
{
    public static void Main()
    {
        string[] values = new string[10];
        string s = values[0];
        Console.WriteLine(s.ToUpper());
    }
}
```

在上述範例中，陣列的宣告會顯示為不可為 null 的字串，而其元素全部初始化為 null。 然後，會將 `s` null 值指派給變數， (陣列) 的第一個元素。 最後，變數 `s` 會被取值，導致執行時間例外狀況。

## <a name="see-also"></a>另請參閱

- [草稿可為 null 的參考型別規格](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [可為 Null 參考教學課程簡介](tutorials/nullable-reference-types.md)
- [將現有的程式碼基底遷移至可為 Null 參考](tutorials/upgrade-to-nullable-references.md)
- [-可為 null (c # 編譯器選項) ](language-reference/compiler-options/nullable-compiler-option.md)
