---
title: "具有實值類型的參考語意"
description: "了解最小化安全地複製結構的語言功能"
author: billwagner
ms.author: wiwagn
ms.date: 11/10/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 9eeaf201c1f5a58044db62e356199b609c4c035a
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="reference-semantics-with-value-types"></a>具有實值類型的參考語意

若要使用實值類型的優點是它們通常避免堆積配置。
對應的缺點是它們傳值方式複製。 這些權衡取捨更難最佳化大量的資料運作的演算法。 C# 7.2 的新語言功能提供的傳址方式傳遞具有實值類型的語意。 如果明智地使用這些功能可減少兩個配置和複製作業。 這篇文章探討這些新功能。

大部分本文章中的範例程式碼會示範 C# 7.2 中新增的功能。 若要使用這些功能，您必須將專案設定為在您的專案中使用 C# 7.2 或更新版本。 您可以使用 Visual Studio，來選取它。 針對每個專案中，選取**專案**功能表，然後從**屬性**。 選取**建置**索引標籤上，按一下 **進階**。 從該處，您可以設定的語言版本。 選擇 「 7.2"，或 「 最新 」。  您可以編輯或*csproj*檔案，然後加入下列節點：

```XML
  <PropertyGroup>
    <LangVersion>7.2</LangVersion>
  </PropertyGroup>
```

您可以使用 「 7.2 」 或 「 最新 」 值。

## <a name="specifying-in-parameters"></a>指定`in`參數

將 C# 7.2`in`關鍵字來補充現有`ref`和`out`關鍵字，當您撰寫的傳址方式傳遞引數的方法。 `in`關鍵字指定您傳址方式傳遞參數，且所呼叫的方法不會修改傳遞給它的值。 

此新增可提供完整的詞彙來表達您的設計目的。 實值類型會複製時傳遞至呼叫的方法，當您未指定任何下列修飾詞。 每個這些修飾詞指定的實值類型由參考傳遞，避免複製。 每個修飾詞表示不同的目的：

- `out`： 這個方法會設定做為此參數的引數的值。
- `ref`： 這個方法可能會設定做為此參數的引數的值。
- `in`： 這個方法不會修改引數做為此參數的值。

當您將加入`in`修飾詞，以引數傳址方式傳遞，您會宣告您的設計目的是傳遞引數所參考，以避免不必要的複製。 您不想修改做為該引數的物件。 下列程式碼會顯示在 3D 空間中的兩個點之間的距離會計算方法的範例。 

[!code-csharp[InArgument](../../samples/csharp/reference-semantics/Program.cs#InArgument "Specifying an In argument")]

引數是兩個結構，其中每個包含三個雙精度浮點數。 Double 是 8 個位元組，因此每個引數是 24 個位元組。 藉由指定`in`修飾詞，您 4 或 8 個位元組將參考傳遞給這些引數，根據電腦的架構。 大小差異很小，但是當您的應用程式使用許多不同的值在緊密迴圈中呼叫這個方法時，它可以快速地在加入。
 
`in`修飾詞補充`out`和`ref`以及其他的方式。 您無法建立只存在的不同方法的多載`in`，`out`或`ref`。 這些新的規則擴充一律為已定義的行為相同`out`和`ref`參數。

`in`修飾詞可能會套用至參數的任何成員： 方法、 委派、 lambda、 區域函式、 索引子、 運算子。

不同於`ref`和`out`引數，您可以使用常值或常數的引數的`in`參數。 此外，不同於`ref`或`out`參數，您不需要套用`in`位於呼叫位置的修飾詞。 下列程式碼會示範兩個呼叫的例子`CalculateDistance`方法。 第一個使用傳址方式傳遞的兩個本機變數。 第二個包含方法呼叫的過程中建立的暫存變數。 

[!code-csharp[UseInArgument](../../samples/csharp/reference-semantics/Program.cs#UseInArgument "Specifying an In argument")]

有數種方式，在其中編譯器可確保唯讀性質`in`引數會強制執行。  首先，呼叫的方法無法直接指派給`in`參數。 它不能直接指派到的任何欄位`in`參數。 此外，您無法將傳遞`in`任何方法要求 (demand) 的參數`ref`或`out`修飾詞。
編譯器會強制執行的`in`引數是唯讀變數。 您可以呼叫任何使用傳值方式傳遞語意的執行個體方法。 在這些情況下，一份`in`建立參數。 因為編譯器可能會建立暫存變數，針對任何`in`參數，您也可以指定預設值為任何`in`參數。 下列程式碼會使用該值來第二個點的預設值為指定的原點 （0，0 點）：

[!code-csharp[InArgumentDefault](../../samples/csharp/reference-semantics/Program.cs#InArgumentDefault "Specifying defaults for an in parameter")]

`in`參數指定也可以搭配參考類型或內建的數字值。 不過，這兩種情況的優點是降到最低。

## <a name="ref-readonly-returns"></a>`ref readonly`傳回

您也可能想要實值類型傳址方式傳回，但不允許呼叫端修改該值。 使用`ref readonly`修飾詞來表示該設計的意圖。 它會通知讀取器，所傳回的參考現有的資料，但是不允許修改。 

編譯器會強制執行，而呼叫端無法修改的參考。 若要直接指派給值的嘗試產生編譯時期錯誤。 不過，編譯器無法知道是否任何成員方法會修改該結構的狀態。
若要確保不會修改物件，編譯器會建立複本，並使用該複本的參考，呼叫成員。 任何修改，就該防禦的複本。 

可能是，程式庫使用`Point3D`通常會使用整個程式碼的來源。 每個執行個體建立新的物件在堆疊上。 它可能會有幫助建立常數和傳址方式傳回。 但是，如果您傳回內部儲存的參考，您可能想要強制呼叫端不能修改參照的儲存體。 下列程式碼會定義傳回的唯讀屬性`readonly ref`至`Point3D`所指定的來源。

[!code-csharp[OriginReference](../../samples/csharp/reference-semantics/Point3D.cs#OriginReference "Creating a readonly Origin reference")]

建立一份 ref readonly 傳回十分簡單： 只要將它指派給未宣告的變數`ref readonly`修飾詞。 編譯器產生的程式碼將物件複製作業的一部分。 

當您指派的變數`ref readonly return`，您可以指定`ref readonly`變數或依值複本的唯讀參考：

[!code-csharp[AssignRefReadonly](../../samples/csharp/reference-semantics/Program.cs#AssignRefReadonly "Assigning a ref readonly")]

在上述程式碼中的第一個指派會建立一份`Origin`常數，並將複製的指派。 第二個指派的參考。 請注意，`readonly`修飾詞必須是變數的宣告的一部分。 無法修改它所參考的參考。 若要這樣做的嘗試會導致編譯時期錯誤。

## <a name="readonly-struct-type"></a>`readonly struct` 類型

套用`ref readonly`到高流量使用的結構應該就足夠。
其他時候，您可能想要建立不可變的結構。 然後您可以一律傳遞唯讀參考。 當您存取做為結構的方法時，所發生練習移除防衛複製`in`參數。

您可以執行此動作建立`readonly struct`型別。 您可以加入`readonly`結構宣告修飾詞。 編譯器會強制執行該結構的所有成員都都`readonly`;`struct`必須是不變。

有其他最佳化`readonly struct`。 您可以使用`in`修飾詞在每個位置其中`readonly struct`是引數。 此外，您可以傳回`readonly struct`為`ref return`傳回其存留期超過方法傳回的物件範圍的物件。

最後，編譯器會產生更有效率的程式碼呼叫的成員時`readonly struct`:`this`參考，而不是 的副本收件者，一律為`in`成員方法參考所傳遞的參數。 此最佳化儲存當您使用多個複製`readonly struct`。 `Point3D`是很好的候選項目，這項變更。 下列程式碼顯示更新`ReadonlyPoint3D`結構：

[!code-csharp[ReadonlyOnlyPoint3D](../../samples/csharp/reference-semantics/Point3D.cs#ReadonlyOnlyPoint3D "Defining an immutable structure")]

## <a name="ref-struct-type"></a>`ref struct` 類型

另一項相關的語言功能是能夠宣告必須為堆疊配置的實值類型。 換句話說，這些類型可以永遠不會建立在堆積上以另一類別的成員。 這項功能的主要動機是<xref:System.Span%601>和相關的結構。 <xref:System.Span%601>可能包含 managed 的指標做為其中一個成員，另一個則是範圍的長度。 因為 C# 不支援不安全的環境之外的 managed 記憶體的指標，則它是實際稍有不同實作。 變更指標和長度的任何寫入不是不可部分完成的。 這表示<xref:System.Span%601>會受限於超出範圍的錯誤或其他型別安全違規不限於單一的堆疊框架。 此外，將 managed 的指標放置在 GC 堆積上通常會損毀在 JIT 時間。

您可能會有類似的需求，建立使用的記憶體使用[ `stackalloc` ](language-reference/keywords/stackalloc.md)或在使用 interop 應用程式開發介面的記憶體。 您可以定義自己`ref struct`這些需求的類型。 在本文中，您會看到使用範例`Span<T>`為了簡單起見。

`ref struct`宣告會宣告此類型的結構必須是在堆疊上。 語言規則可確保安全使用這些型別。 其他類型宣告為`ref struct`包含<xref:System.ReadOnlySpan%601>。 

保留目標`ref struct`堆疊配置的變數導入了數個規則，編譯器會強制執行所有輸入`ref struct`型別。

- 您無法 box 處理`ref struct`。 您無法將指派`ref struct`型別的型別變數`object`， `dynamic`，或任何介面類型。
- 您無法宣告`ref struct`類別或一般結構的成員。
- 您無法宣告區域變數的`ref struct`非同步方法中的型別。 您也可以在傳回的同步方法中宣告`Task`，`Task<T>`或類似工作的類型。
- 您無法宣告`ref struct`迭代器中的本機變數。
- 您無法擷取`ref struct`lambda 運算式或區域函式中的變數。

這些限制可確保您沒有不小心使用`ref struct`無法將它升級為 managed 堆積的方式。

## <a name="conclusions"></a>結論

這些增強功能的 C# 語言專為效能關鍵的演算法，可以達到所需的效能非常重要之記憶體配置。 您可能會發現您通常不使用這些功能在您撰寫的程式碼中。 不過，這些增強功能已採用在.NET Framework 中的許多位置。 當有越來越多的 Api 使用這些功能，您會看到您自己的應用程式的效能改善。
