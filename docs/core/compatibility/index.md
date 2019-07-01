---
title: 評估中斷性變更 - .NET Core
description: 深入了解 .NET Core 嘗試針對跨 .NET 版本開發人員維護相容性的方式。
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: b58edd9ff0bd56b12b861162cc92d484a3b36c8b
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307553"
---
# <a name="evaluate-breaking-changes-in-net-core"></a>評估 .NET Core 中的中斷性變更

縱觀其歷程記錄，.NET 一直嘗試維護 .NET 各版本之間以及各種變體之間的相容性。 在 .NET Core 中仍是如此。 雖然 .NET Core 可以視為是獨立於 .NET Framework 之外的新技術，但是有兩個主要因素限制了 .NET Core 從 .NET Framework 分離的能力：

- 最初開發或是繼續開發 .NET Framework 應用程式的大量開發人員。 他們預期跨 .NET 實作有一致的行為。

- .NET Standard 程式庫專案可讓開發人員建立以 .NET Core 和 .NET Framework 所共用之通用 API 為目標的程式庫。 開發人員預期 .NET Core 應用程式中使用之程式庫的行為，應與 .NET Framework 應用程式中所使用的程式庫相同。

除了 .NET 實作之間的相容性之外，開發人員還希望 .NET Core 版本之間具有高層級相容性。 特別是，針對較早版本的 .NET Core 所撰寫的程式碼應該在新版的 .NET Core 上順暢地執行。 實際上，許多開發人員預期在新發行的 .NET Core 版本中找到的新 API，也應該與引入那些 API 的發行前版本相容。

此文章概述相容性變更 (或中斷性變更) 的類別，以及 .NET 小組評估每個類別中的變更的方式。 了解 .NET 小組如何處理可能的中斷性變更，對於在 [dotnet/corefx](https://github.com/dotnet/corefx) GitHub 存放庫中建立提取要求以修改現有 API 行為的開發人員特別有幫助。

> [!NOTE]
> 如需相容性類別的定義，例如二進位檔案相容性和回溯相容性，請參閱[中斷性變更類別](categories.md)。

以下各節說明對 .NET Core API 所做的變更類別，以及其對應用程式相容性的影響。 ✔️ 圖示表示允許特定類型的變更， 表示不允許，而  表示可能允許或不允許的變更。 最後一個分類中的變更需要判斷並評估先前行為的可預測性、明顯性與一致性。

> [!NOTE]
> 除了作為如何評估 .NET Core 程式庫變更的指南之外，程式庫開發人員也可以使用這些準則來評估其程式庫 (以多個 .NET 實作和版本為目標) 的變更。

## <a name="modifications-to-the-public-contract"></a>公用合約的修改

此類別中的變更會修改  某個類型的公用介面區。 此類別中的大多數變更都是不允許的，因為它們違反了回溯相容性  (可讓使用舊版 API 開發的應用程式能夠在更新版本上執行而不必重新編譯的能力)。

### <a name="types"></a>型別

- **✔️ 當介面已由基底類型實作時，從類型中移除介面實作**

- **將新的介面實作加入類型**

  這是一個可接受的變更，因為它不會對現有的用戶端產生負面影響。 對類型的任何變更都必須在此處定義的可接受變更的界限內運作，以使新實作維持可接受。 如果您要加入的介面會直接影響設計工具或序列化程式產生無法在低層級取用之程式碼或資料的能力，請格外小心。 其中一個範例是 <xref:System.Runtime.Serialization.ISerializable> 介面。

- **引進新的基底類別**

  如果型別不引進任何新的[抽象](../../csharp/language-reference/keywords/abstract.md)成員或變更現有型別的語意或行為，則可以將型別引進兩個現有型別之間的階層中。 例如，在 .NET Framework 2.0 中，<xref:System.Data.Common.DbConnection> 類別成為 <xref:System.Data.SqlClient.SqlConnection> 的新基底類別，它先前直接衍生自 <xref:System.ComponentModel.Component>。

- **✔️ 將型別從一個組件移動到另一個組件**

  請注意，必須使用指向新組件的 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 標記舊  組件。

- **✔️ 將 [struct](../../csharp/language-reference/keywords/struct.md) 型別變更為 `readonly struct` 型別**

  請注意，不允許將 `readonly struct` 型別變更為 `struct` 型別。
  
- **✔️ 當沒有可存取  (公用或受保護) 的建構函式時，將[密封](../../csharp/language-reference/keywords/sealed.md)或[抽象](../../csharp/language-reference/keywords/abstract.md)關鍵字新增到型別**

- **✔️ 延伸型別的可見性**

- **變更型別的命名空間或名稱**

- **重新命名或移除公用型別**

   這會中斷使用已重新命名或已移除之型別的所有程式碼。

- **變更列舉的底層型別**

   這是編譯時期和行為的中斷性變更，以及可以使屬性引數無法進行剖析的二進位中斷性變更。

- **密封先前未密封的型別**

- **將介面加入至介面的基底類型集合**

   如果介面實作先前未實作的介面，則實作介面原始版本的所有型別都會中斷。

- **從基底類別集合移除類別，或從已實作介面集合移除介面**

  介面移除規則有一個例外：您可以新增衍生自已移除之介面的介面實作。 例如，如果型別或介面現在實作 <xref:System.ComponentModel.IComponent> (它會實作 <xref:System.IDisposable>)，則可以移除 <xref:System.IDisposable>。

- **將 `readonly struct` 型別變更為 [struct](../../csharp/language-reference/keywords/struct.md) 型別**

  請注意，不允許將 `struct` 型別更改為 `readonly struct` 型別。

- **將 [struct](../../csharp/language-reference/keywords/struct.md) 型別變更為 `ref struct` 型別，反之亦然**

- **降低型別的可見性**

   但是，允許增加型別的可見性。

### <a name="members"></a>成員

- **✔️ 展開非[虛擬](../../csharp/language-reference/keywords/sealed.md)成員的可見性**

- **✔️ 將抽象成員新增至沒有可存取  (公用或受保護) 建構函式的公用型別，否則型別將會被[密封](../../csharp/language-reference/keywords/sealed.md)**

  但是，不允許將抽象成員新增至具有可存取 (公用或受保護) 建構函式且不是 `sealed` 的型別。

- **✔️ 當型別沒有可存取 (公用或受保護) 建構函式或型別為[密封](../../csharp/language-reference/keywords/sealed.md) 時，限制[受保護](../../csharp/language-reference/keywords/protected.md)成員的可見性**

- **✔️ 將成員移動到階層中比移除它的型別更高的類別**

- **✔️ 新增或移除覆寫**

  請注意，引進覆寫可能會導致先前的取用者在呼叫[基礎映像](../../csharp/language-reference/keywords/base.md)時跳過覆寫。

- **✔️ 如果類別先前沒有建構函式，則將建構函式與預設 (無參數) 建構函式一起新增至類別中**

   但是，不允許將建構函式新增至先前沒有建構函式且沒有  新增預設建構函式的類別。

- **✔️ 將成員從[抽象](../../csharp/language-reference/keywords/abstract.md)變更為[虛擬](../../csharp/language-reference/keywords/virtual.md)**

- **✔️ 從 `ref readonly` 變更為 `ref` 傳回值 (虛擬方法或介面除外)**

- **✔️ 除非欄位的靜態類型是可變動的實值型別，否則從欄位中移除 [readonly](../../csharp/language-reference/keywords/readonly.md)**

- **✔️ 呼叫先前未定義的新事件**

- **將新的執行個體欄位新增至型別**

   此變更會影響序列化。

- **重新命名或移除公用成員或參數**

   這會中斷使用已重新命名或已移除之成員或參數的所有程式碼。

   請注意，這包括從屬性中移除或重新命名 getter 或 setter，以及重新命名或移除列舉成員。

- **將成員新增至介面**

- **變更公用常數或列舉成員的值**

- **變更屬性、欄位、參數或傳回值的型別**

- **新增、移除或變更參數的順序**

- **從參數中新增或移除 [in](../../csharp/language-reference/keywords/in.md)、[out](../../csharp/language-reference/keywords/out.md) 或 [ref](../../csharp/language-reference/keywords/ref.md) 關鍵字**

- **重新命名參數 (包括變更其大小寫)**

  這會視為中斷的原因有二：
  
  - 它中斷了晚期繫結的案例，例如 Visual Basic 中的晚期繫結功能和 C# 中的 [dynamic](../../csharp/language-reference/keywords/dynamic.md)。
  
  - 當開發人員使用[具名引數](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)時，它會中斷[來源相容性](categories.md#source-compatibility)。

- **從 `ref` 傳回值變更為 `ref readonly` 傳回值**

- **️ 在虛擬方法或介面上從 `ref readonly` 變更為 `ref` 傳回值**

- **在成員中新增或移除 [abstract](../../csharp/language-reference/keywords/abstract.md)**

- **從成員中移除 [virtual](../../csharp/language-reference/keywords/virtual.md) 關鍵字**

  雖然這通常不是一個中斷性變更，因為 C# 編譯器傾向於發出 [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) 中繼語言 (IL) 指令以呼叫非虛擬方法 (`callvirt` 會執行 Null 檢查，而正常呼叫不會)，由於以下幾個原因，此行為並不是不變的：
  - C# 不是 .NET 以其為目標的唯一語言。
  
  - 只要目標方法為非虛擬且可能不是 Null 時 (例如透過 [?. null 傳播運算子](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)存取的方法)，C# 編譯器就會漸漸地嘗試將 `callvirt` 最佳化為正常呼叫。
  
  使方法成為虛擬表示取用者程式碼通常最後會以非虛擬方式呼叫它。

- **將 [virtual](../../csharp/language-reference/keywords/virtual.md) 關鍵字新增至成員**

- **將虛擬成員設為抽象**

  [虛擬成員](../../csharp/language-reference/keywords/virtual.md)提供了一種方法實作，可以  由衍生類別覆寫。 [抽象成員](../../csharp/language-reference/keywords/abstract.md)不提供任何實作，且必須  被覆寫。

- **將抽象成員新增至具有可存取 (公用或受保護) 建構函式且不是 [sealed](../../csharp/language-reference/keywords/sealed.md) 的公用型別**

- **從成員中新增或移除 [static](../../csharp/language-reference/keywords/static.md) 關鍵字**

- **新增一個防止現有多載的多載，並定義不同的行為**

  這會中斷繫結到先前多載的現有用戶端。 例如，如果某個類別具有接受 <xref:System.UInt32> 的方法的單一版本，則現有的取用者在傳遞 <xref:System.Int32> 值時將成功繫結至該多載。 但是，如果新增接受 <xref:System.Int32> 的多載，則在重新編譯或使用晚期繫結時，編譯器現在會繫結至新的多載。 如果產生不同的行為，這是一個中斷性變更。

- **將建構函式新增至先前沒有建構函式且沒有新增預設建構函式的類別**

- **️ 將 [readonly](../../csharp/language-reference/keywords/readonly.md) 新增至欄位中**

- **降低成員的可見性**

   這包括在可存取  (公用或受保護) 建構函式且型別*非* [sealed](../../csharp/language-reference/keywords/sealed.md) 時，降低[受保護](../../csharp/language-reference/keywords/protected.md)成員的可見性。 如果不是這種情況，則允許降低受保護成員的可見性。

   請注意，這允許增加成員的可見性。

- **變更成員型別**

   無法修改方法的傳回值，或屬性或欄位的型別。 例如，傳回 <xref:System.Object> 之方法的簽章不能變更為傳回 <xref:System.String>，反之亦然。

- **將欄位新增至先前沒有狀態的結構**

  只要變數型別是無狀態結構，明確指派規則就允許使用未初始化的變數。 如果將結構設定為具狀態，程式碼最後可能會遇到未初始化的資料。 這可能是一個來源中斷和二進位中斷性變更。

- **引發先前從未引發的現有事件**

## <a name="behavioral-changes"></a>行為變更

### <a name="assemblies"></a>組件

- **✔️ 在仍支援相同平台的情況下，讓組件可移植**

- **變更組件的名稱**
- **變更組件的公開金鑰**

### <a name="properties-fields-parameters-and-return-values"></a>屬性、欄位、參數與傳回值

- **✔️ 將屬性、欄位、傳回值或 [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數的值變更為衍生程度較大的型別**

  例如，傳回 <xref:System.Object> 型別的方法可以傳回 <xref:System.String> 執行個體。 (但是，無法變更方法簽章。)

- **✔️ 如果成員不是[虛擬](../../csharp/language-reference/keywords/virtual.md)，則增加屬性或參數的可接受值範圍**

  請注意，雖然可以傳遞給方法或由成員傳回之值的範圍可以擴展，但參數或成員類型不能。 例如，雖然傳遞至方法的值可以從 0-124 擴充至 0-255，但參數類型無法從 <xref:System.Byte> 變更為 <xref:System.Int32>。

- **如果成員為[虛擬](../../csharp/language-reference/keywords/virtual.md)，則增加屬性或參數的可接受值範圍**

   此變更會中斷現有的覆寫成員，這些成員將無法在擴充的值範圍內正常執行。

- **縮減屬性或參數的可接受值範圍**

- **增加屬性、欄位、傳回值或 [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數的傳回值範圍**

- **變更屬性、欄位、方法傳回值或 [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數的傳回值**

- **變更屬性、欄位或參數的預設值**

- **變更傳回數值的有效位數**

- **剖析輸入和擲回新的例外狀況中的變更 (即使文件中未指定剖析行為)**

### <a name="exceptions"></a>例外狀況

- **✔️ 擲回衍生程度比現有例外狀況更大的例外狀況**

  因為新的例外狀況是現有例外狀況的子類別，所以先前的例外狀況處理程式碼會繼續處理例外狀況。 例如，在 .NET Framework 4 中，文化特性建立和擷取方法已開始擲回 <xref:System.Globalization.CultureNotFoundException> 而不是 <xref:System.ArgumentException> (如果找不到文化特性)。 因為 <xref:System.Globalization.CultureNotFoundException> 衍生自 <xref:System.ArgumentException>，所以這是一個可接受的變更。

- **✔️ 擲回比 <xref:System.NotSupportedException>、<xref:System.NotImplementedException>、<xref:System.NullReferenceException> 更具體的例外情況**

- **✔️ 擲回被視為無法復原的例外狀況**

  無法復原的例外狀況不應該攔截，而應該由高層級追補處理常式處理。 因此，使用者不應該擁有攔截這些明確例外狀況的程式碼。 無法復原的例外狀況有：

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **✔️ 在新的程式碼路徑中擲回新的例外狀況**

  該例外狀況必須僅套用到使用新參數值或狀態執行的新程式碼路徑，而且無法由以舊版為目標的現有程式碼執行。

- **✔️ 移除例外狀況以啟用更穩定的行為或新的案例**

  例如，之前只處理正值並擲回 <xref:System.ArgumentOutOfRangeException> 的 `Divide` 方法可以變更為支援負值和正值，而不擲回例外狀況。

- **✔️ 變更錯誤訊息的文字**

  開發人員不應該依賴錯誤訊息的文字，這也會根據使用者的文化特性而變更。

- **擲回以上未列出之任何其他情況中的例外狀況**

- **移除以上未列出之任何其他情況中的例外狀況**

### <a name="attributes"></a>屬性

- **✔️ 變更不  可觀察的屬性值**

- **變更可  觀察的屬性值**

- **移除屬性**

  在大部分情況下，移除屬性 (例如<xref:System.NonSerializedAttribute>) 是一個中斷性變更。

## <a name="platform-support"></a>平台支援

- **✔️ 支援先前不支援的平台上的作業**

- **不支援或現在針對先前平台上支援的作業需要特定 Service Pack**

## <a name="internal-implementation-changes"></a>內部實作的變更

- **變更內部型別的介面區**

   通常允許此類變更，儘管它們可能會中斷私人反映。 在一些熱門的協力廠商程式庫或大量開發人員依賴內部 API 的案例中，可能不允許此類變更。

- **變更成員的內部實作**

  通常允許這些變更，儘管它們可能會中斷私人反映。 在一些客戶程式碼經常依賴私人反映或變更引進非預期之副作用的情況下，可能不允許這些變更。

- **✔️ 提升作業效能**

   修改作業效能的能力是很重要的，但此類變更可能會中斷仰賴目前作業速度的程式碼。 對於仰賴非同步作業時間的程式碼尤其如此。 請注意，效能變更應該不會影響相關 API 的其他行為；否則，變更將會中斷。

- **✔️ 間接 (通常是不利) 變更作業的效能**

  如果由於某些其他原因而未將相關變更歸類為中斷，則這是可以接受的。 通常，需要採取可能包括額外的作業或新增新功能的動作。 這幾乎一律會影響效能，但對於使相關 API 如預期般運作至關重要。

- **將同步 API 變更為非同步 (反之亦然)**

## <a name="code-changes"></a>程式碼變更

- **✔️ 將 [params](../../csharp/language-reference/keywords/params.md) 新增至參數**

- **將 [struct](../../csharp/language-reference/keywords/struct.md) 變更為 [class](../../csharp/language-reference/keywords/class.md)，反之亦然**

- **將 [checked](../../csharp/language-reference/keywords/virtual.md) 關鍵字新增至程式碼區塊**

   此變更可能會導致先前執行的程式碼擲回 <xref:System.OverflowException> 且無法接受。

- **從參數中移除 [params](../../csharp/language-reference/keywords/params.md)**

- **變更引發事件的順序**

  開發人員可以合理地預期事件以相同的順序引發，而開發人員程式碼經常會取決於事件的引發順序。

- **移除在指定動作上的事件引發**

- **變更指定事件的呼叫次數**

- **將 <xref:System.FlagsAttribute> 新增至列舉型別**
