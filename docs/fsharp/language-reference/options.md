---
title: 選項 (F#)
description: '了解如何使用 F # 選項類型時的實際值可能不存在的具名的值或變數。'
ms.date: 05/16/2016
ms.openlocfilehash: 0859cb42e72ef9e67551b884f5cf6130fb099a78
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46479516"
---
# <a name="options"></a>選項

實際的值可能不存在的具名的值或變數時，會使用 F # 中的選項類型。 選項有基礎類型，並可保存的值，該型別，或可能不會有值。

## <a name="remarks"></a>備註

下列程式碼說明的函式會產生選項類型。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1404.fs)]

如您所見，如果輸入`a`大於 0，`Some(a)`產生。  否則，`None`產生。

值`None`選項沒有實際的值時，會使用。 否則，運算式`Some( ... )`可讓選擇的值。 值`Some`並`None`可用於模式比對，如下列函式所示`exists`，就會傳回`true`如果選項的值和`false`則。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1401.fs)]

## <a name="using-options"></a>使用選項

選項時常用的搜尋不會傳回符合的結果，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1403.fs)]

在先前的程式碼清單會遞迴地搜尋。 此函式`tryFindMatch`採用述詞函式`pred`傳回布林值，以及要搜尋的清單。 如果找到符合述詞的項目，則遞迴結束和函式傳回的值當做運算式中的選項`Some(head)`。 遞迴結束時，會比對空的清單。 值，此時`head`沒有找到，和`None`會傳回。

許多 F # 程式庫函式值，可能會或可能不存在傳回集合中搜尋`option`型別。 依照慣例，這些函式則是以開頭`try`前置詞，例如[ `Seq.tryFindIndex` ](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。

值可能不存在，例如，如果可能的話，當您嘗試建構值時，會擲回例外狀況時，選項可以也很有用。 下列程式碼範例會說明這點。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1402.fs)]

`openFile`在上述範例中的函式具有類型`string -> File option`因為它會傳回`File`物件如果已順利開啟檔案和`None`發生的例外狀況。 視情況而定，它可能不是適當的設計選擇來攔截例外狀況，而不是允許傳播。

## <a name="option-properties-and-methods"></a>選項屬性和方法

選項類型支援下列屬性和方法。

|屬性或方法|類型|描述|
|------------------|----|-----------|
|[無](https://msdn.microsoft.com/library/83ef260a-aa33-4e6f-aee6-b9bf0a461476)|`'T option`|可讓您建立具有的選項值的靜態屬性`None`值。|
|[IsNone](https://msdn.microsoft.com/library/f08532ca-1716-4f60-ae59-8ef6256df234)|`bool`|傳回`true`若選項有`None`值。|
|[IsSome](https://msdn.microsoft.com/library/c5088d51-c5d7-425f-a77f-12c379bb356f)|`bool`|傳回`true`如果選項的值不是`None`。|
|[某些](https://msdn.microsoft.com/library/12f048d2-e293-4596-accb-de036ecd63fc)|`'T option`|靜態成員，會建立一個選項，其值不是`None`。|
|[值](https://msdn.microsoft.com/library/c79f68e8-11fd-45b1-a053-e8fc38b56df7)|`'T`|傳回基礎值，或擲回`System.NullReferenceException`如果值為`None`。|

## <a name="option-module"></a>Option 模組

沒有模組，這[選項](https://msdn.microsoft.com/library/e615e4d3-bbbb-49ba-addc-6061ea2e2f4c)，其中包含在選項執行作業的實用函式。 某些函式會重複屬性的功能，但可用於內容需要函式的位置。 [Option.isSome](https://msdn.microsoft.com/library/41ad0857-5672-4326-84b5-c33dc43dcf79)並[Option.isNone](https://msdn.microsoft.com/library/73db6a53-15e7-40a6-94f9-a0049e5f4819)是這兩個模組函式，測試是否選擇保留的值。 [Option.get](https://msdn.microsoft.com/library/803e9fcb-6edd-4910-808c-25f08cbc55ea)取得值，如果有的話。 如果沒有任何值，就會擲回`System.ArgumentException`。

[Option.bind](https://msdn.microsoft.com/library/c3406192-24ac-49b5-bc3b-8f805187f1c0)函式值，執行的函式的值。 函式必須接受一個引數，且其參數類型必須是選項類型。 此函式的傳回值是另一個選項類型。

Option 模組也會包含對應至可供清單、 陣列、 順序和其他集合類型的函式的函式。 這些函式包含[ `Option.map` ](https://msdn.microsoft.com/library/91a20385-7e73-40c2-9adc-635e86d6a622)， [ `Option.iter` ](https://msdn.microsoft.com/library/83389eef-3dff-4074-b4cc-f69581c25191)， [ `Option.forall` ](https://msdn.microsoft.com/library/ba884586-5eae-49c5-9e36-05481c1c3428)， [ `Option.exists` ](https://msdn.microsoft.com/library/a606d2d4-fddc-4eab-ab37-c6138fb7ad99)， [ `Option.foldBack` ](https://msdn.microsoft.com/library/a882fbaf-c019-46f0-b4f5-b8c2b8b90ffb)， [ `Option.fold` ](https://msdn.microsoft.com/library/af896794-3d53-406c-9411-316cd5c33ad8)，和[ `Option.count` ](https://msdn.microsoft.com/library/2dac83a9-684e-4d0f-b50e-ff722a8bb876)。 這些函式會啟用零個或一個項目的集合，例如要使用的選項。 如需詳細資訊和範例，請參閱集合中的函式的討論[列出](lists.md)。

## <a name="converting-to-other-types"></a>將轉換成其他類型

選項可以轉換為清單或陣列。 當選項轉換成這些資料結構時，所產生的資料結構會有零個或一個項目。 若要轉換為陣列的選項，使用[ `Option.toArray` ](https://msdn.microsoft.com/library/c8044873-ba17-4b52-8231-eb1a28318c64)。 若要將選項轉換清單，請使用[ `Option.toList` ](https://msdn.microsoft.com/library/5f1af295-9fa9-40ad-b4a1-3578d94d44e1)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [F# 類型](fsharp-types.md)
