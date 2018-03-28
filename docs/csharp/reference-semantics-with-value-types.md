---
title: 具備實值型別的參考語意
description: 了解最小化安全地複製結構的語言功能
author: billwagner
ms.author: wiwagn
ms.date: 11/10/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 8a0cfe83200d50eefa9b01ab51591a5fe0703ec0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="reference-semantics-with-value-types"></a>具備實值型別的參考語意

使用實值型別的優點是他們通常可避免堆積配置。
相對地，缺點則是他們根據實值複製。 這種兩難的情況使得最佳化針對大量資料進行運作的演算法，變得更加困難。 C# 7.2 中新的語言功能提供一項新的機制，可對實值型別使用利用參考傳遞的語意。 若能善用這些功能，即可同時最小化配置及複製作業。 本文會探討這些新功能。

文中有許多程式碼範例示範有 C# 7.2 的新增功能。 若要使用這些功能，必須在您的專案中將專案設為使用 C# 7.2 或更新版本。 您可使用 Visual Studio 進行選取。 請為每個專案，從功能表選取 [專案]，然後選取 [屬性]。 選取 [建置] 索引標籤，然後按一下 [進階]。 您可於該位置設定語言版本。 請選擇 [7.2] 或 [最新版]。  或者，您也可以編輯 *csproj* 檔案，並新增下列節點：

```XML
  <PropertyGroup>
    <LangVersion>7.2</LangVersion>
  </PropertyGroup>
```

您可以為值使用 [7.2] 或 [最新版]。

## <a name="specifying-in-parameters"></a>指定 `in` 參數

當您撰寫利用參考傳遞引數的方法時，C# 7.2 會新增 `in` 關鍵字來補充現有的 `ref` 和 `out` 關鍵字。 `in` 關鍵字會指定您利用參考傳遞參數，且呼叫的方法不會修改傳遞給他的值。 

該新增功能提供完整的詞彙能表達您的設計目的。 當您未指定下列任一修飾詞時，會在傳遞至呼叫的方法時，複製實值型別。 每個修飾詞皆會指定要利用參考傳遞實值型別，避免複製。 每個修飾詞皆表示不同之目的：

- `out`：此方法會設定用作為此參數的引數值。
- `ref`：此方法會設定用作為此參數的引數值。
- `in`：此方法不會修改用作為此參數的引數值。

當您新增 `in` 修飾詞來利用參考傳遞引數時，即表明您的設計目的是利用參考傳遞引數，來避免不必要的複製。 您並不想修改用作為該引數的物件。 下列程式碼示範計算 3D 空間中不同兩點間距離的方法。 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

引數為雙結構，每個結構皆包含三個雙精度浮點數。 一個雙精度浮點數是 8 個位元組，因此每個引數是 24 個位元組。 透過指定 `in` 修飾詞，將 4 或 8 個位元組參考傳遞到這些引數，位元組大小取決於電腦的架構。 位元組大小的差異很小，但是當您的應用程式使用許多不同的值在緊密迴圈中呼叫此方法時，差異會快速加大。
 
`in` 修飾詞也可於其他方面補足 `out` 和 `ref`。 您無法為差異處只有是否出現 `in`、`out` 或 `ref` 的方法，建立多載。 這些新規則沿用一直以來為 `out` 和 `ref` 參數所定義的相同行為。

`in` 修飾詞可套用至任何使用下列參數的成員：方法、委派、Lambda、區域函式、索引子、運算子。

不同於 `ref` 和 `out` 引數，您可以對 `in` 參數的引數使用常值或常數。 此外，不同於 `ref` 或 `out` 參數，您也不需要在呼叫位置套用 `in` 修飾詞。 下列程式碼示範兩種呼叫 `CalculateDistance` 方法的範例。 第一種使用兩個利用參考傳遞的區域變數。 第二種則包含建立為方法呼叫之一部份的暫存變數。 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

編譯器確保強制讓 `in` 引數為唯讀性質的方式有數種。  首先，呼叫的方法不可直接指派到 `in` 參數。 該方法不可直接指派到 `in` 參數的任何欄位。 此外，您也無法將 `in` 參數傳遞到需要 `ref` 或 `out` 修飾詞的任何方法。
編譯器會強制讓 `in` 引數為唯讀變數。 您可以呼叫使用利用實值傳遞之語意的任何執行個體方法。 在那些執行個體中，會建立 `in` 參數的複本。 因為編譯器可為任何 `in` 參數建立暫存變數，所以您也可以為任何 `in` 參數指定預設值。 下列程式碼使用了該方式將原點 (點 0, 0) 指定為第二個點的預設值：

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

參考型別或內建數值也可使用 `in` 參數指定。 但這兩種用法的優點皆不彰顯 (若有的話)。

## <a name="ref-readonly-returns"></a>`ref readonly` 傳回

同時也建議您利用參考傳回實值型別，但不允許呼叫端修改該值。 請使用 `ref readonly` 修飾詞來表示該設計目的。 該修飾詞會通知讀取器，目前正在將參考傳回現有資料，但不允許修改。 

編譯器會強制呼叫端無法修改該參考。 若嘗試直接指派到值，會產生編譯時期錯誤。 但編譯器無法知道是否有任何成員方法修改了該結構的狀態。
為確保物件未經修改，編譯器會建立複本，並使用該複本呼叫成員參考。 任何修改皆僅會修改防禦複本。 

使用 `Point3D` 的程式庫似乎通常會在整篇程式碼中使用原點。 每個執行個體都會在堆疊上建立新的物件。 如此有助建立常數並利用參考傳回常數。 但是，如果您將參考傳回內部儲存體，可能會希望強制限制呼叫端不可修改參考的儲存體。 下列程式碼定義了將 `readonly ref` 傳回至指定原點之 `Point3D` 的唯讀屬性。

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

建立 ref readonly 傳回的複本十分簡單：只要將其指派到並非利用 `ref readonly` 修飾詞宣告的變數即可。 編譯器會產生程式碼，將物件複製為指派的一部分。 

當您指派變數到 `ref readonly return` 時，可指定 `ref readonly` 變數或 readonly 所參考的實值複本：

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

在上述程式碼中的第一項指派，會建立 `Origin` 常數的複本，並指派該複本。 第二項指派則會指派參考。 請注意，`readonly` 修飾詞必須是變數宣告的一部分。 其參考項目無法修改。 如果嘗試修改，會導致編譯時期錯誤。

## <a name="readonly-struct-type"></a>`readonly struct` 類型

將 `ref readonly` 套用到高流量的結構應該已足夠。
其他請況下，則建議您建立不可變的結構。 如此一來，您即就可一律利用 readonly 參考進行傳遞。 該做法會移除在您存取用作為 `in` 參數之結構方法時，所產生的保護複本。

建立 `readonly struct` 類型即可執行此作業。 您可以將 `readonly` 修飾詞新增至結構宣告。 編譯器會將該結構的所有執行個體成員，強制為 `readonly`，且 `struct` 不得可變動。

`readonly struct` 有其他最佳化。 您可以在每個 `readonly struct` 為引數的位置處，使用 `in` 修飾詞。 此外，當您傳回存留期超過方法傳回物件之範圍的物件時，可將 `readonly struct` 傳回為 `ref return`。

最後，當您呼叫 `readonly struct` 的成員時，編譯器會產生極具效率的程式碼：`this` 參考 (而非接收器的複本) 會一律為利用參考傳遞至成員方法的 `in` 參數。 當您使用 `readonly struct` 時，此項最佳化可儲存更多複製內容。 `Point3D` 是此項變極佳的候選項目。 下列程式碼示範更新過後的 `ReadonlyPoint3D` 結構：

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>`ref struct` 類型

另一項相關的語言功能，是可宣告必須配置堆疊的實值型別。 換句話說，這些類型在堆積上絶對不會建立為另一種類別的成員。 此功能的主要動機是 <xref:System.Span%601> 及相關的結構。 <xref:System.Span%601> 的受控指標可能是其成員之一，而另一則為範圍的長度。 因為 C# 不支援不安全的內容外之受控記憶體的指標，所以實作上會有些微的差異。 任何變更指標和長度的寫入，都非不可部分完成。 這表示 <xref:System.Span%601> 會受限於超出範圍的錯誤，或有其他類型的安全違規不限於單一堆疊框架。 此外，將受控指標放置於 GC 堆積上通常會於 JIT 時間損毀。

當您使用以 [`stackalloc`](language-reference/keywords/stackalloc.md) 建立的記憶體，或使用來自 Interop API 的記憶體時，可能會有類似需求。 您可依照那些需求定義自己的 `ref struct` 類型。 本文中提供的範例利用了 `Span<T>` 達到簡潔性。

`ref struct` 宣告會宣告此類型的結構必須位於堆疊中。 語言規則可確保會安全地使用這些類型。 其他宣告為 `ref struct` 的類型包括 <xref:System.ReadOnlySpan%601>。 

希望將類型 `ref struct` 保留為配置有堆疊的變數之目標，會讓編譯器強制對所有 `ref struct` 類型進行數項規則。

- 您無法分隔 `ref struct`。 您不可為類型是 `object`、`dynamic` 或任何介面類型的變數，指派 `ref struct` 類型。
- 您不可將 `ref struct` 宣告為類別或一般結構的成員。
- 您不可在非同步方法中宣告類型為 `ref struct` 的區域變數。 但可以在傳回 `Task`、`Task<T>` 或類似工作之類型的同步方法中，宣告這些區域變數。
- 您不可在迭代器中宣告 `ref struct` 區域變數。
- 您不可在 Lambda 運算式或區域函式中擷取 `ref struct` 變數。

這些限制可確保您不會不小心地用到 `ref struct`，而可能將其升階至受控堆積。

## <a name="readonly-ref-struct-type"></a>`readonly ref struct` 類型

宣告結構為 `readonly ref` 會結合 `ref struct` 與 `readonly struct` 宣告的優點與限制。 

下列範例示範了 `readonly ref struct` 的宣告。

```csharp
readonly ref struct ReadOnlyRefPoint2D
{
    public int X { get; }
    public int Y { get; }
    
    ReadOnlyRefPoint2D(int x, int y) => (X, Y) = (x, y);
}
```

## <a name="conclusions"></a>結論

這些 C# 語言的增強功能專為注重效能的演算法所設計，對於這些演算法來說，記憶體的配置對於達到所需效能至關重要。 您會發現到您不常在您撰寫的程式碼中使用這些功能。 但在 .NET Framework 中，已有許多位置採用這些增強功能。 隨著愈來愈多的 API 利用到這些功能之後，您會發現自己的應用程式效能會有所改善。
