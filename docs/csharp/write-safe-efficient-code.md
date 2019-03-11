---
title: 撰寫安全且有效率的 C# 程式碼
description: 最近對 C# 語言的增強功能，可讓您撰寫可驗證的安全程式碼，獲得先前使用不安全程式碼時的效能。
ms.date: 10/23/2018
ms.custom: mvc
ms.openlocfilehash: d363e357d3749bb2014456c0064c4de7dd7f1acb
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57411563"
---
# <a name="write-safe-and-efficient-c-code"></a>撰寫安全且有效率的 C# 程式碼

C# 中的新功能可讓您撰寫可驗證的安全程式碼，取得更佳的效能。 若您小心套用這些技術，則需要不安全程式碼的案例將減少。 這些功能可讓使用實值型別參考作為方法引數和方法傳回值的過程變得更為容易。 當以安全的方式執行時，這些技術可最小化複製實值型別的次數。 透過使用實值型別，您可以最小化傳遞的配置數及記憶體回收數。

本文中的許多範例程式碼都使用了 C# 7.2 新增功能。 若要使用這些功能，您必須設定您的專案，以使用 C# 7.2 或更新版本。 如需設定語言版本的詳細資訊，請參閱[設定語言版本](language-reference/configure-language-version.md)。

本文聚焦於高效率資源管理的技術。 使用實值型別的一個優點是它們通常可避免堆積配置。 相對地，缺點則是它們是以實值複製。 這種兩難的情況使得最佳化針對大量資料進行運作的演算法，變得更加困難。 C# 7.2 中新的語言功能提供一項機制，可讓您使用實值型別參考來撰寫安全且有效率的程式碼。 若能善用這些功能，即可同時最小化配置及複製作業。 本文會探討這些新功能。

本文聚焦於下列資源管理技術：

- 宣告 [`readonly struct`](language-reference/keywords/readonly.md#readonly-struct-example) 來表達型別為**固定**，並可讓編譯器在使用 [`in`](language-reference/keywords/in-parameter-modifier.md) 參數時儲存複本。
- 當傳回值為大於 <xref:System.IntPtr.Size?displayProperty=nameWithType> 的 `struct`，且儲存體存留期大於傳回值的方法時，使用 [`ref readonly`](language-reference/keywords/ref.md#reference-return-values) 傳回。
- 當 `readonly struct` 的大小大於 <xref:System.IntPtr.Size?displayProperty=nameWithType> 時，基於效能原因，您應將它作為 `in` 參數傳遞。
- 除非已使用 `readonly` 修飾詞宣告，否則請永遠不要將 `struct` 作為 `in` 參數傳遞，因為這可能會對效能產生負面影響，並引發難以理解的行為。
- 使用 [`ref struct`](language-reference/keywords/ref.md#ref-struct-types) 或 `readonly ref struct` (例如 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601>) 來將記憶體作為位元組序列使用。

這些技術會強迫您考慮在**參考**及**實值**這兩個競爭目標之間取得平衡。 [參考型別](programming-guide/types/index.md#reference-types)的變數會保留記憶體位置的參考。 [實值型別](programming-guide/types/index.md#value-types)的變數則會直接包含其值。 這些差異凸顯管理記憶體資源時關鍵的不同點。 **實值型別**通常會在傳遞至方法，或是從方法傳回時複製。 此行為包含在呼叫實值型別成員時，複製 `this` 的值。 複製成本與型別的大小相關。 **參考型別**則配置在受控堆積上。 每個新物件都需要新的配置，且之後都必須進行回收。 這些作業都需要時間。 參考會在參考型別作為方法的引數或從方法傳回時複製。

本文使用下列 3D 點結構的範例概念來解釋這些建議：

```csharp
public struct Point3D
{
    public double X;
    public double Y;
    public double Z;
}
```

不同範例會使用此概念不同的實作。

## <a name="declare-readonly-structs-for-immutable-value-types"></a>宣告固定實值型別的唯讀結構

使用 `readonly` 修飾詞宣告 `struct`，通知編譯器您的意圖是要建立固定型別。 編譯器會實行包含下列規則的設計決策：

- 所有欄位成員都必須是 `readonly`
- 所有屬性都必須是唯讀屬性，包含自動實作的屬性。

這兩項規則便足以確保沒有任何 `readonly struct` 的成員會修改該結構狀態。 `struct` 是固定的。 `Point3D` 結構可定義為固定結構，如下列範例所示：

```csharp
readonly public struct ReadonlyPoint3D
{
    public ReadonlyPoint3D(double x, double y, double z)
    {
        this.X = x;
        this.Y = y;
        this.Z = z;
    }

    public double X { get; }
    public double Y { get; }
    public double Z { get; }
}
```

每當您的設計意圖是要建立固定實值型別時，請遵循此建議。 任何效能上的改善都會帶來效益。 `readonly struct` 明確表達您的設計意圖。

## <a name="use-ref-readonly-return-statements-for-large-structures-when-possible"></a>在可能的情況下，針對大型結構使用 `ref readonly return` 陳述式

當所傳回值不屬於傳回方法的區域時，您可以以參考的型式傳回值。 以參考的型式傳回，表示只會複製參考，而非結構。 在下列範例中，`Origin` 屬性無法使用 `ref` 傳回，因為傳回的值是區域變數：

```csharp
public Point3D Origin => new Point3D(0,0,0);
```

但是，下列屬性定義則可以參考的型式傳回，因為傳回值是靜態成員：

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    // Dangerous! returning a mutable reference to internal storage
    public ref Point3D Origin => ref origin;

    // other members removed for space
}
```

您不希望呼叫者修改原點，因此您應以 `readonly ref` 的方式傳回值：

```csharp
public struct Point3D
{
    private static Point3D origin = new Point3D(0,0,0);

    public static ref readonly Point3D Origin => ref origin;

    // other members removed for space
}
```

傳回 `ref readonly` 可讓您避免複製較大的結構，並保留您內部資料成員的不變性。

在呼叫位置，呼叫者會選擇使用 `Origin` 屬性作為 `readonly ref` 或作為值：

[!code-csharp[AssignRefReadonly](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

在上述程式碼中的第一項指派，會建立 `Origin` 常數的複本，並指派該複本。 第二項指派則會指派參考。 請注意，`readonly` 修飾詞必須是變數宣告的一部分。 其參考項目無法修改。 如果嘗試修改，會導致編譯時期錯誤。

`readonly` 修飾詞在 `originReference` 的宣告上是必要的。

編譯器會強制呼叫者不可修改該參考。 若嘗試直接指派到值，則會產生編譯時間錯誤。 但是，編譯器無法得知是否有任何成員方法修改結構的狀態。
為確保物件未經修改，編譯器會建立複本，並使用該複本呼叫成員參考。 任何修改皆僅會修改防禦複本。

## <a name="apply-the-in-modifier-to-readonly-struct-parameters-larger-than-systemintptrsize"></a>將 `in` 修飾詞套用到大於 `System.IntPtr.Size` 的 `readonly struct` 參數

`in` 關鍵字會補充現有的 `ref` 和 `out` 關鍵字，以參考型式傳遞引數。 `in` 關鍵字會指定以參考型式傳遞引數，但呼叫的方法不會修改值。

該新增功能提供完整的詞彙能表達您的設計目的。
當您未在下列方法簽章中指定下列任一修飾詞時，會在傳遞至呼叫的方法時，複製實值型別。 每個修飾詞都會指定以參考型式來傳遞變數以避免複製。 每個修飾詞皆表示不同之目的：

- `out`：此方法會設定用來作為此參數的引數值。
- `ref`：此方法可設定用來作為此參數的引數值。
- `in`：此方法不會修改用來作為此參數的引數值。

當您新增 `in` 修飾詞來利用參考傳遞引數時，即表明您的設計目的是利用參考傳遞引數，來避免不必要的複製。 您不打算修改用來作為該引數的物件。

這種做法常常會改善大於 <xref:System.IntPtr.Size?displayProperty=nameWithType> 唯讀實值型別的效能。 針對簡單型別 (`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、`double`、`decimal` 及 `bool` 和 `enum` 型別)，任何潛在的效能增益都非常小。 事實上，針對小於 <xref:System.IntPtr.Size?displayProperty=nameWithType> 的型別使用以參考傳遞可能會降低效能。

下列程式碼示範計算 3D 空間中不同兩點間距離的方法。

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

引數為雙結構，每個結構皆包含三個雙精度浮點數。 一個雙精度浮點數是 8 個位元組，因此每個引數是 24 個位元組。 藉由指定 `in` 修飾詞，您會傳遞一個 4 位元組或 8 位元組參考至那些引數，取決於電腦的架構。 大小的差異很小，但是當您的應用程式使用許多不同值在緊密迴圈中呼叫此方法時，差異便會加大。

`in` 修飾詞也可於其他方面補足 `out` 和 `ref`。 您無法針對差異僅為是否出現 `in`、`out` 或 `ref` 的方法來建立其多載。 這些新規則沿用一直以來為 `out` 和 `ref` 參數所定義的相同行為。 與 `out` 和 `ref` 修飾詞相似，實值型別並非 Boxed，因為已套用了 `in` 修飾詞。

`in` 修飾詞可套用至任何使用下列參數的成員：方法、委派、Lambda、區域函式、索引子、運算子。

`in` 參數另一項功能是您可以使用常值或常數來作為 `in` 參數的引數。 此外，不同於 `ref` 或 `out` 參數，您也不需要在呼叫位置套用 `in` 修飾詞。 下列程式碼示範兩種呼叫 `CalculateDistance` 方法的範例。 第一種使用兩個利用參考傳遞的區域變數。 第二種則包含建立為方法呼叫之一部份的暫存變數。

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#UseInArgument "Specifying an In argument")]

編譯器強制 `in` 引數唯讀性質的方式有數種。  首先，呼叫的方法不可直接指派到 `in` 參數。 當該值為 `struct` 類型時，該方法不可直接指派到 `in` 參數的任何欄位。 此外，您也無法使用 `ref` 或 `out` 修飾詞，將 `in` 參數傳遞至任何方法。
這些規則適用於所有 `in` 參數的欄位，提供的欄位為 `struct` 類型，且參數也為 `struct` 類型。 實際上，這些規則適用於成員存取的多個層級，提供所有成員存取層級的類型為 `structs`。
編譯器會強制 `struct` 類型作為 `in` 引數傳遞，且其 `struct` 成員在作為引數對其他方法使用時為唯讀變數。

使用 `in` 參數可避免製作複本可能產生的效能成本。 這不會變更任何方法呼叫的語意。 因此，您不需要在呼叫位置指定 `in` 修飾詞。 在呼叫位置忽略 `in` 修飾詞，會告知編譯器可以基於下列理由製作引數的複本：

- 從引數型別至參數型別存在隱含轉換，但沒有識別轉換。
- 引數為運算式，但不具有已知的儲存體變數。
- 存在受 `in` 存在與否影響的多載。 在此情況下，傳值多載是最佳相符項目。

當您更新現有的程式碼以使用唯讀參考引數時，這些規則相當實用。 在呼叫的方法中，您可呼叫所有使用傳值參數的執行個體方法。 在那些執行個體中，會建立 `in` 參數的複本。 因為編譯器可為任何 `in` 參數建立暫存變數，所以您也可以為任何 `in` 參數指定預設值。 下列程式碼會將原點 (點 0,0) 指定為第二個點的預設值：

[!code-csharp[InArgumentDefault](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

若要強制編譯器以參考型式來傳遞唯讀引數，請在呼叫位置於引數上指定 `in` 修飾詞，如下列程式碼所示：

[!code-csharp[UseInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ExplicitInArgument "Specifying an In argument")]

此行為能在可提升效能時，使在大型程式碼基底中採用 `in` 參數一段時間更加輕鬆。 您必須先將 `in` 修飾詞新增至方法簽章。 隨後便可在呼叫位置新增 `in` 修飾詞並建立 `readonly struct` 型別，避免編譯器在更多位置建立 `in` 參數的防禦性複本。

參考型別或數值也可使用 `in` 參數指定。 但這兩種用法的優點皆不彰顯 (若有的話)。

## <a name="never-use-mutable-structs-as-in-in-argument"></a>請永遠不要像在 `in` 引數中一樣使用可變動的結構

以上所述的技術解釋了如何透過傳回參考及以參考型式傳遞值來避免複製。 這些技術在引數型別宣告為 `readonly struct` 型別時的效果最佳。 否則，編譯器必須在許多情況中建立**防禦性複本**，強制實施任何引數的唯讀性。 請考慮下列範例，該範例會計算原點至 3D 點的距離：

[!code-csharp[InArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#InArgument "Specifying an in argument")]

`Point3D` 結構「不是」唯讀結構。 此方法的主體中有六個不同屬性存取呼叫。 在第一次檢查中，您可能會認為這些存取都是安全的。 畢竟，`get` 存取子應該不會修改物件的狀態。 但是沒有任何語言規則強制該行為。 它只是一個常見的慣例。 任何型別都可實作修改內部狀態的 `get` 存取子。 若沒有任何語言保證，編譯器必須先建立引數的暫時複本，再呼叫任何成員。 暫存位置會在堆疊上建立，引數的值則會複製到暫存位置，而該值則會針對每個成員存取，作為 `this` 引數複製到堆疊。 在許多情況下，當引數型別並非 `readonly struct` 時，這些複本會危害效能，使得以值型式傳遞的速度高於以唯讀參考型式傳遞。

相反的，若距離計算使用固定結構 (`ReadonlyPoint3D`)，便不需要暫存物件：

[!code-csharp[readonlyInArgument](../../samples/csharp/safe-efficient-code/ref-readonly-struct/Program.cs#ReadOnlyInArgument "Specifying a readonly in argument")]

編譯器會在您呼叫 `readonly struct` 的成員時，產生更有效率的程式碼：`this` 參考 (而非接收器的複本) 一律都是以參考型式傳遞至成員方法的 `in` 參數。 當您使用 `readonly struct` 作為 `in` 引數時，這項最佳化可避免進行複製。

您可以在我們於 GitHub 上的[範例存放庫](https://github.com/dotnet/samples/tree/master/csharp/safe-efficient-code/benchmark)中，查看使用 [Benchmark.net](https://www.nuget.org/packages/BenchmarkDotNet/) 示範效能差異的範例程式。 它會比較以值型式和以參考型式傳遞可變動結構，以及以值型式和以參考型式傳遞固定結構的差異。 使用固定結構並以參考型式傳遞的速度最快。

## <a name="use-ref-struct-types-to-work-with-blocks-or-memory-on-a-single-stack-frame"></a>使用 `ref struct` 型別來使用單一堆疊框架上的區塊或記憶體

另一項相關語言功能是可宣告實值型別必須限制在單一堆疊框架的能力。 此限制可讓編譯器進行幾項最佳化。 此功能的主要動機是 <xref:System.Span%601> 及相關的結構。 您可以透過使用新的及已更新 .NET API，利用 <xref:System.Span%601> 型別以透過這些增強功能來改善效能。

當您使用以 [`stackalloc`](language-reference/keywords/stackalloc.md) 建立的記憶體，或使用來自 Interop API 的記憶體時，可能會有類似需求。 您可依照那些需求定義自己的 `ref struct` 類型。

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` 類型

宣告結構為 `readonly ref` 會結合 `ref struct` 與 `readonly struct` 宣告的優點與限制。 唯讀範圍所使用的記憶體會限制在單一堆疊框架，且唯讀範圍使用的記憶體無法修改。

## <a name="conclusions"></a>結論

使用實值型別可將配置作業的次數降至最低：

- 實值型別儲存體是為區域變數和方法引數配置的堆疊。
- 作為其他物件成員的實值型別，其儲存體會作為該物件的一部分進行配置，而非個別配置。
- 實值型別傳回值的儲存體是所配置堆疊。

在相同情況下，與參考型別的對比是：

- 參考型別儲存體是為區域變數和方法引數配置的堆積。 參考會儲存在堆疊上。
- 作為其他物件成員的參考型別，其儲存體會在堆積上個別配置。 包含該型別的物件會儲存參考。
- 參考型別傳回值的儲存體是所配置堆積。 該儲存體的參考會儲存在堆疊上。

最小化配置也包含了取捨。 您會在 `struct` 的大小大於參考的大小時複製更多記憶體。 參考通常是 64 位元或 32 位元，取決於目標電腦的 CPU。

這些取捨通常只會對效能造成極小的影響。 但是，針對大型結構或較大的集合，對效能產生的影響便會增加。 在緊密迴圈或程式的最忙碌路徑中，影響可能會很大。

這些 C# 語言的增強功能專為注重效能的演算法設計，對於這些演算法來說，最小化記憶體配置在達到所需效能的過程中扮演了重要角色。 您會發現到您不常在您撰寫的程式碼中使用這些功能。 但是，您已透過 .NET 採用了這些增強功能。 隨著愈來愈多的 API 利用這些功能，您會發現自己的應用程式效能有所改善。

## <a name="see-also"></a>另請參閱

- [ref 關鍵字](language-reference/keywords/ref.md)
- [ref 傳回值和 ref 區域變數](programming-guide/classes-and-structs/ref-returns.md)
