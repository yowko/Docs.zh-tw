---
title: "Hashtable 和 Dictionary 集合類型"
description: "Hashtable 和 Dictionary 集合類型"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 0f18fac7-fd0d-4f25-a046-1d3d51de062e
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: 721f16154e1df4b7a075639ccce6bf2650b46c9b

---

# <a name="hashtable-and-dictionary-collection-types"></a>Hashtable 和 Dictionary 集合類型

[System.Collections.Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable) 類別以及 [System.Collections.Generic.Dictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) 和 [System.Collections.Concurrent.ConcurrentDictionary<T>](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2) 泛型類別會實作 [System.Collections.IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary) 介面。 `Dictionary<T>` 泛型類別還會實作 [IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2) 泛型介面。 因此，這些集合中的每個項目是索引鍵-值組。

`Hashtable` 物件是由包含集合項目的值區所組成。 值區是 `Hashtable` 中項目的虛擬子群組，比大多數集合的搜尋和擷取更容易且更快速。 每個值區會與一個雜湊碼相關聯，這個雜湊碼是使用雜湊函式並根據項目的索引鍵所產生。

泛型 [HashSet&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.HashSet-1) 類別是包含唯一元素的未排序集合。 

雜湊函式是根據索引鍵傳回數值雜湊碼的演算法。 索引鍵是所儲存之物件的特定屬性值。 雜湊函式一律必須針對同一個索引鍵傳回相同的雜湊碼。 雜湊函式可以為兩個不同的索引鍵產生相同的雜湊碼，但是當雜湊函式為每個唯一的索引鍵產生唯一的雜湊碼時，可以提升從雜湊資料表擷取項目的效能。

當做 `Hashtable` 中項目使用的每個物件必須能夠使用 `GetHashCode` 方法的實作，為自己產生雜湊碼。 

將物件加入 `Hashtable` 之後，該物件會儲存在與符合物件雜湊碼的雜湊碼關聯的值區中。 當搜尋 `Hashtable` 中的值時，系統會針對該值產生雜湊碼，並搜尋與該雜湊碼關聯的值區。

例如，字串的雜湊函式可能會接受字串中每個字元的 ASCII 碼，並全部加入以產生雜湊碼。 字串 "picnic" 的雜湊碼與字串 "basket" 的雜湊碼不同；因此，字串 "picnic" 和 "basket" 會在不同的值區。 相反地，"stressed" 和 "desserts" 有相同的雜湊碼，因此會在相同的值區。

`Dictionary<T>` 和 `ConcurrentDictionary<T>` 類別的功能與 `Hashtable` 類別相同。 特定類型 (`Object` 以外的類型) 的 `Dictionary<T>` 提供比實值類型的 `Hashtable` 更佳的效能。 這是因為 `Hashtable` 的項目屬於 `Object` 類型；因此，當您儲存或擷取實值類型時，通常會發生 Boxing 和 Unboxing。 當多個執行緒可能同時存取集合時，應該使用 `ConcurrentDictionary<T>` 類別。

## <a name="see-also"></a>另請參閱

[Hashtable](https://docs.microsoft.com/dotnet/core/api/System.Collections.Hashtable)

[IDictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.IDictionary)

[Dictionary](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2)

[System.Collections.Generic.IDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IDictionary-2)

[System.Collections.Concurrent.ConcurrentDictionary&lt;TKey, TValue&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Concurrent.ConcurrentDictionary-2)

[常用的集合類型](commonly-used-collection-types.md)




<!--HONumber=Nov16_HO1-->


