---
title: C# 7.3 的新功能
description: C# 7.3 新功能的概觀
ms.date: 05/16/2018
ms.openlocfilehash: 1d1aca2564c26315cf8b3af60a863ea3c70fd385
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827094"
---
# <a name="whats-new-in-c-73"></a>C# 7.3 的新功能

C# 7.3 版有兩個主要的佈景主題。 其中一個佈景主題提供了使安全的程式碼具有與不安全的程式碼一樣高效能的功能。 第二個佈景主題提供現有功能的累加增強功能。 此外，此版本中加入了新的編譯器選項。

下列新功能針對安全的程式碼支援較佳效能的佈景主題：

- 您可以在不釘選的情況下存取固定的欄位。
- 您可以重新指派 `ref` 區域變數。
- 您可以在 `stackalloc` 陣列上使用初始設定式。
- 您可以搭配支援模式的任何型別使用 `fixed` 陳述式。
- 您可以使用其他的泛型限制式。

已在現有功能中提供下列增強功能：

- 您可以使用 Tuple 型別測試 `==` 和 `!=`。
- 您可以在更多位置使用運算式變數。
- 您可以將屬性附加至自動實作屬性的支援欄位。
- 已改善當引數依 `in` 不同時的方法解析。
- 多載解析現在會有較少模稜兩可的情況。

新的編譯器選項：

- `-publicsign`，用來啟用組件的開放原始碼軟體 (OSS) 簽署。
- `-pathmap`，用來提供來源目錄的對應。

這篇文章的其餘部分提供詳細資料和連結，讓您深入了解每個增強功能。

## <a name="enabling-more-performant-safe-code"></a>啟用更多高效能的安全的程式碼

您應該能夠安全地撰寫與不安全的程式碼一樣高效能的 C# 程式碼。 安全的程式碼可避免一些錯誤類別，例如緩衝區溢位、偏離的指標和其他記憶體存取錯誤。 這些新功能擴充了可驗證安全的程式碼的功能。 儘可能使用安全的建構來撰寫更多的程式碼。 這些功能都讓這變得更容易。

### <a name="indexing-fixed-fields-does-not-require-pinning"></a>索引 `fixed` 欄位不需要釘選

請考量此建構：

```csharp
unsafe struct S
{
    public fixed int myFixedField[10];
}
```

在舊版的 C# 中，您需要釘選變數，才能存取屬於 `myFixedField` 的其中一個整數。 現在，下列程式碼會在安全的內容中編譯：

```csharp
class C
{
    static S s = new S();

    unsafe public void M()
    {
        int p = s.myFixedField[5];
    }
}
```

變數 `p` 會存取 `myFixedField` 中的一個元素。 您不需要宣告個別的 `int*` 變數。 請注意，您仍然需要 `unsafe` 內容。 在舊版的 C# 中，您需要宣告第二個固定指標：

```csharp
class C
{
    static S s = new S();

    public void M()
    {
        fixed (int* ptr = s.myFixedField)
        {
            int p = ptr[5];
        }
    }
}
```

如需詳細資訊，請參閱有關 [`fixed` 陳述式](../language-reference/keywords/fixed-statement.md)的文章。

### <a name="ref-local-variables-may-be-reassigned"></a>`ref` 區域變數可能會重新指派

現在，`ref` 區域變數可能會在初始化之後被重新指派，以參照不同的執行個體。 下列程式碼現在會編譯：

```csharp
ref VeryLargeStruct refLocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

如需詳細資訊，請參閱有關 [`ref` 傳回和 `ref` 區域變數](../programming-guide/classes-and-structs/ref-returns.md)的文章。

### <a name="stackalloc-arrays-support-initializers"></a>`stackalloc` 陣列支援初始設定式

您可以在初始化陣列時，指定陣列中元素的值：

```csharp
var arr = new int[3] {1, 2, 3};
var arr2 = new int[] {1, 2, 3};
```

現在，相同的語法可以套用至使用 `stackalloc` 宣告的陣列：

```csharp
int* pArr = stackalloc int[3] {1, 2, 3};
int* pArr2 = stackalloc int[] {1, 2, 3};
Span<int> arr = stackalloc [] {1, 2, 3};
```

如需詳細資訊，請參閱語言參考中的 [`stackalloc` 陳述式](../language-reference/keywords/stackalloc.md)一文。

### <a name="more-types-support-the-fixed-statement"></a>更多型別支援 `fixed` 陳述式

`fixed` 陳述式支援一組有限的型別。 從 C# 7.3 開始，包含傳回 `ref T` 或 `ref readonly T` 之 `GetPinnableReference()` 方法的任何型別都可能是 `fixed`。 新增此功能表示 `fixed` 可以與 <xref:System.Span%601?displayProperty=nameWithType> 和相關型別一起使用。

如需詳細資訊，請參閱語言參考中的 [`fixed` 陳述式](../language-reference/keywords/fixed-statement.md)一文。

### <a name="enhanced-generic-constraints"></a>增強泛型限制式

您現在可以指定型別 <xref:System.Enum?displayProperty=nameWithType> 或 <xref:System.Delegate?displayProperty=nameWithType> 作為型別參數的基底類別限制式。

您也可以使用新的 `unmanaged` 限制式指定型別參數必須是**非受控型別**。 **非受控型別**是非參考型別的型別，而且未包含任何巢狀層級的參考型別。

如需詳細資訊，請參閱有關 [`where` 泛型限制式](../language-reference/keywords/where-generic-type-constraint.md)和[型別參數的限制式](../programming-guide/generics/constraints-on-type-parameters.md)的文章。

## <a name="make-existing-features-better"></a>讓現有的功能變得更好

第二個佈景主題提供了語言功能的改進。 撰寫 C# 時，這些功能可以提高生產力。

### <a name="tuples-support--and-"></a>Tuple 支援 `==` 和 `!=`

C# Tuple 型別現在支援 `==` 和 `!=`。 如需詳細資訊，請參閱 [Tuple](../tuples.md) 文章中涵蓋[相等](../tuples.md#equality-and-tuples)的一節。

### <a name="attach-attributes-to-the-backing-fields-for-auto-implemented-properties"></a>將屬性附加至自動實作屬性的支援欄位

現在支援此語法：

```csharp
[field: SomeThingAboutFieldAttribute]
public int SomeProperty { get; set; }
```

屬性 `SomeThingAboutFieldAttribute` 套用至編譯器針對 `SomeProperty` 產生的支援欄位。 如需詳細資訊，請參閱 C# 程式設計指南中的[屬性](../programming-guide/concepts/attributes/index.md)。

### <a name="in-method-overload-resolution-tiebreaker"></a>`in` 方法多載解析 tiebreaker

當加入 `in` 引數修飾詞時，這兩種方法會造成模稜兩可：

```csharp
static void M(S arg);
static void M(in S arg);
```

現在，by 值 (上述範例中的第一個) 多載會優於 by 唯讀參考版本。 若要呼叫具有唯讀參考引數的版本，您呼叫方法時必須包含 `in` 修飾詞。

> [!NOTE]
> 這已實作為錯誤 (Bug) 修正。 即使將語言版本設定為 "7.2"，這也不再模棱兩可。

如需詳細資訊，請參閱有關 [`in` 參數修飾詞](../language-reference/keywords/in-parameter-modifier.md)的文章。

### <a name="extend-expression-variables-in-initializers"></a>在初始設定式中擴充運算式變數

加入 C# 7.0 中以允許 `out` 變數宣告的語法已經擴充，以包含欄位初始設定式、屬性初始設定式、建構函式初始設定式和查詢子句。 它讓您能執行如下列範例的程式碼：

```csharp
public class B
{
   public B(int i, out int j)
   {
      j = i;
   }
}

public class D : B
{
   public D(int i) : B(i, out var j)
   {
      Console.WriteLine($"The value of 'j' is {j}");
   }
}
```

### <a name="improved-overload-candidates"></a>改進的多載候選項目

在每個版本中，多載解析規則都會更新，以解決模稜兩可的方法引動過程具有「明確」選項的情況。 此版本新增三個新的規則，以協助編譯器挑選明確的選項：

1. 當方法群組同時包含執行個體和靜態成員時，如果在沒有執行個體接收者或內容的情況下叫用方法，編譯器會捨棄執行個體成員。 如果使用執行個體接收者叫用方法，編譯器就會捨棄靜態成員。 沒有接收者時，編譯器只會在靜態內容中包含靜態成員，否則將同時包含靜態成員和執行個體成員。 當無法確定接收者是執行個體或型別時，編譯器會包含兩者。 無法使用隱含 `this` 執行個體接收者的靜態內容，包括未定義 `this` 的成員主體 (例如靜態成員)，以及不能使用 `this` 的位置 (例如欄位初始設定式和建構函式初始設定式)。
1. 當方法群組包含某些型別引數不滿足其限制式的泛型方法時，這些成員將會從候選集合中移除。
1. 針對方法群組轉換，其傳回型別與委派的傳回型別不符合的候選方法，將會從集合中移除。

您只會注意到此變更，因為若確定何種方法較佳，就會發現模稜兩可的方法多載會有較少的編譯器錯誤。

## <a name="new-compiler-options"></a>新的編譯器選項

新的編譯器選項支援 C# 程式的新組建和 DevOps 案例。

### <a name="public-or-open-source-signing"></a>公用或開放原始碼簽署

`-publicsign` 編譯器選項會指示編譯器使用公開金鑰簽署組件。 該組件標示為已簽署，但簽章取自公開金鑰。 此選項可讓您使用公開金鑰，從開放原始碼專案建置簽署的組件。

如需詳細資訊，請參閱 [-publicsign 編譯器選項](../language-reference/compiler-options/publicsign-compiler-option.md)一文。

### <a name="pathmap"></a>pathmap

`-pathmap` 編譯器選項會指示編譯器使用對應的來源路徑取代建置環境的來源路徑。 `-pathmap` 選項控制編譯器寫入 PDB 檔案或 <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> 的來源路徑。

如需詳細資訊，請參閱 [-pathmap 編譯器選項](../language-reference/compiler-options/pathmap-compiler-option.md)一文。
