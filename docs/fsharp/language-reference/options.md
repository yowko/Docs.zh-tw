---
title: 選項
description: 瞭解當命名值F#或變數的實際值可能不存在時, 如何使用選項類型。
ms.date: 05/16/2016
ms.openlocfilehash: 9326cf04f53adac7422c09a49a59c4eecd49486d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627345"
---
# <a name="options"></a>選項

當命名值或F#變數的實際值可能不存在時, 會使用中的選項類型。 選項具有基礎類型, 而且可以保留該類型的值, 或者可能沒有值。

## <a name="remarks"></a>備註

下列程式碼說明產生選項類型的函式。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

如您所見, 如果輸入`a`大於 0, `Some(a)`就會產生。  否則, `None`就會產生。

當選項`None`沒有實際的值時, 會使用此值。 否則, 運算式`Some( ... )`會為選項提供值。 值`Some` `true`和`None`在模式比對中很有用, `exists`如下列函式所示, 如果選項具有值`false` , 則會傳回, 如果不是, 則會傳回。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>使用選項

當搜尋未傳回相符的結果時, 通常會使用選項, 如下列程式碼所示。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

在先前的程式碼中, 會以遞迴方式搜尋清單。 `pred`函式`tryFindMatch`會採用會傳回布林值的述詞函式, 以及要搜尋的清單。 如果找到滿足述詞的專案, 遞迴就會結束, 而且函數會傳回值做為運算式`Some(head)`中的選項。 當符合空的清單時, 遞迴就會結束。 此時找不到值`head` , 而且`None`會傳回。

許多F#搜尋集合中不一定存在`option`值的程式庫函數會傳回類型。 依照`try`慣例, 這些函式會以前置詞開頭, [`Seq.tryFindIndex`](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)例如。

當您嘗試建立值時可能會擲回例外狀況時, 選項也可能很有用, 例如。 下列程式碼範例會說明這點。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

上`openFile`一個範例中的函式具有`string -> File option`型別, 因為`File`如果檔案成功開啟, 以及發生`None`例外狀況, 就會傳回物件。 視情況而定, 它可能不是適當的設計選擇來攔截例外狀況, 而不是讓它傳播。

此外, 仍然可以`null`將或值`Some`設為 null, 以作為選項的大小寫。 這通常是避免的, 通常是在例行F#的程式設計中, 但可能是因為 .net 中參考型別的本質。

## <a name="option-properties-and-methods"></a>選項屬性和方法

選項類型支援下列屬性和方法。

|屬性或方法|類型|描述|
|------------------|----|-----------|
|[無](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|靜態屬性, 可讓您建立具有`None`值的選項值。|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|`true`如果選項`None`具有值, 則傳回。|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|如果選項的值不`None`是, 則傳回。 `true`|
|[部分](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|靜態成員, 它會建立值不`None`是的選項。|
|[值](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|傳回基礎值, 或`System.NullReferenceException`如果值為`None`, 則擲回。|

## <a name="option-module"></a>選項模組

有一個模組[選項](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c), 其中包含對選項執行作業的實用函式。 有些函式會重複屬性的功能, 但在需要函式的內容中很有用。 [IsSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79)和[選項。 isNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819)都是測試選項是否包含值的模組函式。 [選項。 get 會取得](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea)值 (如果有的話)。 如果沒有值, 則`System.ArgumentException`會擲回。

如果[Option.bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0)有值, 則 [系結函式] 會在值上執行函數。 函式必須只接受一個引數, 而其參數類型必須是選項類型。 函數的傳回值是另一個選項類型。

選項模組也包含函式, 這些函式會對應至可供清單、陣列、序列和其他集合類型使用的函數。 這些功能包括[`Option.map`](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622)、 [`Option.iter`](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191)、 [`Option.forall`](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428)、 [`Option.exists`](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99)、 [、`Option.foldBack`](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb)[和`Option.count`](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876)。 [`Option.fold`](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8) 這些函式可讓選項當做零或一個元素的集合使用。 如需詳細資訊和範例, 請參閱[清單](lists.md)中的集合函數討論。

## <a name="converting-to-other-types"></a>轉換成其他類型

選項可以轉換成清單或陣列。 當選項轉換成其中一個資料結構時, 產生的資料結構會有零個或一個元素。 若要將選項轉換為數組, 請[`Option.toArray`](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64)使用。 若要將選項轉換為清單, 請[`Option.toList`](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1)使用。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [F# 類型](fsharp-types.md)
