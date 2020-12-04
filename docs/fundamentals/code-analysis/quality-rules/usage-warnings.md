---
title: '使用規則 (程式碼分析) '
description: 瞭解程式碼分析使用規則。
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- rules, usage
- managed code analysis rules, usage rules
- usage rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: c8b14d2f92502d5a82e41a322e599745bdcf8b85
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2020
ms.locfileid: "96586463"
---
# <a name="usage-rules"></a>使用規則

使用規則支援適當使用 .NET。

## <a name="in-this-section"></a>本節內容

|規則|描述|
|----------|-----------------|
|[CA1801:必須檢閱未使用的參數](ca1801.md)|方法簽章包括不用於方法主體中的參數；|
|[CA1816:正確呼叫 GC.SuppressFinalize](ca1816.md)|實值處置的方法不會呼叫，或不是執行 `GC.SuppressFinalize` 呼叫的方法 `Dispose` `GC.SuppressFinalize` ; 或方法呼叫 `GC.SuppressFinalize` ，並 `this` `Me` 在 Visual Basic) 中傳遞非 (的其他內容。|
|[CA2200:必須重新擲回以保存堆疊詳細資料](ca2200.md)|例外狀況遭到重新擲回，而且已在 throw 陳述式中明確指定此例外狀況。 如果例外狀況是透過在陳述式中指定例外狀況而重新擲回，則會遺失在擲回例外狀況之原始方法和目前方法之間呼叫的方法清單。|
|[CA2201:不要引發保留的例外狀況類型](ca2201.md)|這會讓原始錯誤難以偵測和偵測。|
|[CA2207:必須將實值類型的靜態欄位內嵌初始化](ca2207.md)|實值類型會宣告明確的靜態建構函式。 若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。|
|[CA2208:必須正確執行個體化引數例外狀況](ca2208.md)|對例外狀況類型為 (或衍生自) ArgumentException 的預設 (無參數) 建構函式進行呼叫，或將錯誤的字串引數傳遞至例外狀況類型為 (或衍生自) ArgumentException 的參數化建構函式。|
|[CA2211:非常數欄位不應該為可見的](ca2211.md)|非常數或唯讀的靜態欄位不是安全線程。 對這類欄位的存取權必須謹慎控制，且需要先進的程式設計技巧來同步處理對類別物件的存取。|
|[CA2213:可處置的欄位應該受到處置](ca2213.md)|型別，這個型別 <xref:System.IDisposable?displayProperty=fullName> 會針對也會實作為型別的宣告欄位 `IDisposable` 。 宣告 `Dispose` 類型的方法不會呼叫欄位的方法 `Dispose` 。|
|[CA2214:不要呼叫建構函式中的可覆寫方法](ca2214.md)|當函式呼叫虛擬方法時，叫用方法之實例的函式可能尚未執行。|
|[CA2215:Dispose 方法應該呼叫基底類別處置](ca2215.md)|如果型別繼承自可處置的型別，則必須 `Dispose` 從它自己的方法呼叫基底型別的方法 `Dispose` 。|
|[CA2216:可處置的類型應該宣告完成項](ca2216.md)|實作為的型別 <xref:System.IDisposable?displayProperty=fullName> ，而且有一些欄位建議使用非受控資源，並不會依照所述的方式來執行完成項 `Object.Finalize` 。|
|[CA2217:不要以 FlagsAttribute 標記列舉](ca2217.md)|外部可見的列舉會標示為 `FlagsAttribute` ，而且有一或多個值不是兩個或列舉上其他已定義值的組合。|
|[CA2218:覆寫 Equals 時必須一併覆寫 GetHashCode](ca2218.md)|Public 類型會覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName> ，但不會覆寫 <xref:System.Object.GetHashCode%2A?displayProperty=fullName> 。|
|[CA2219:不要在 exception 子句中引發例外狀況](ca2219.md)|在 finally 或 fault 子句中引發例外狀況時，新的例外狀況會隱藏作用中的例外狀況。 在 filter 子句中引發例外狀況時，執行階段會以無訊息模式攔截例外狀況。 這會讓原始錯誤難以偵測和偵測。|
|[CA2224:多載等號比較運算子時必須一併覆寫 Equals](ca2224.md)|Public 型別會執行等號比較運算子，但不會覆寫 <xref:System.Object.Equals%2A?displayProperty=fullName> 。|
|[CA2225:運算子多載必須有具名的替代方法](ca2225.md)|偵測到運算子多載，且找不到預期的具名替代方法。 已命名的替代成員提供與運算子相同功能的存取權，並提供給以不支援多載運算子的語言撰寫程式的開發人員使用。|
|[CA2226:運算子應該有對稱的多載](ca2226.md)|型別會執行相等或不等比較運算子，且不會執行相反的運算子。|
|[CA2227:集合屬性應該為唯讀](ca2227.md)|可寫入的集合屬性允許使用者以不同的集合來取代該集合。 唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。|
|[CA2229:必須實作序列化建構函式](ca2229.md)|若要修正此規則的違規情形，請實作序列化建構函式。 針對密封類別，讓建構函式成為 private，否則為 protected。|
|[CA2231:在覆寫 ValueType.Equals 上多載等號運算子](ca2231.md)|實值型別 `Object.Equals` 會覆寫，但不會執行等號比較運算子。|
|[CA2234:必須傳遞 System.Uri 物件而非字串](ca2234.md)|呼叫字串參數名稱包含 "uri"、"URI"、"urn"、"URN"、"url" 或 "URL"，  方法的宣告類型包含具有參數的對應方法多載 <xref:System.Uri?displayProperty=fullName> 。|
|[CA2235:必須標記所有不可序列化的欄位](ca2235.md)|可序列化之類型中所宣告之類型的執行個體 (Instance) 欄位是不可序列化的。|
|[CA2237:ISerializable 類型必須標記 SerializableAttribute](ca2237.md)|若要以可序列化的 common language runtime 辨識，型別必須以 SerializableAttribute 屬性標記，即使型別使用自訂序列化常式，也是透過介面的實 `ISerializable` 。|
|[CA2241:必須提供格式化方法的正確引數](ca2241.md)|傳遞給的格式引數 <xref:System.String.Format%2A?displayProperty=nameWithType> 不包含對應至每個物件引數的格式專案，反之亦然。|
|[CA2242:必須正確測試 NaN](ca2242.md)|此運算式會針對或測試 `Single.Nan` 值 `Double.Nan` 。 使用 `Single.IsNan(Single)` 或 `Double.IsNan(Double)` 來測試值。|
|[CA2243:屬性字串常值必須正確剖析](ca2243.md)|屬性的字串常值參數未正確剖析 URL、GUID 或版本。|
|[CA2244：請勿複製索引元素初始化](ca2244.md)|物件初始化運算式有一個以上的索引元素初始化運算式具有相同的常數索引。 但最後一個初始化運算式是多餘的。|
|[CA2245：請勿將屬性指派給屬性自身](ca2245.md)|屬性意外指派給本身。|
|[CA2246：請勿在相同的陳述式中指派符號及其成員](ca2246.md)|不建議在相同的語句中指派符號及其成員，也就是欄位或屬性。 如果成員存取的目的是要在指派之前使用符號的舊值，或是在此語句中指派新值，則不會很清楚。|
|[CA2247：傳遞到 TaskCompletionSource 建構函式的引數應為 TaskCreationOptions 列舉，而非 TaskContinuationOptions 列舉](ca2246.md)|>taskcompletionsource 具有可使用 TaskCreationOptions 來控制基礎工作的函式，以及採用儲存在工作中之物件狀態的函式。  不小心傳遞 System.threading.tasks.taskcontinuationoptions> 而非 TaskCreationOptions，會導致呼叫將選項視為狀態。|
|[CA2248：提供正確的 ' enum ' 引數給 ' Enum. HasFlag '](ca2248.md)|作為引數傳遞至方法呼叫的列舉類型 `HasFlag` ，與呼叫列舉型別不同。|
|[CA2249：請考慮使用 String.Contains 而非 String.IndexOf](ca2249.md)|呼叫 `string.IndexOf` 結果的位置來檢查是否有子字串存在，可由取代 `string.Contains` 。|
