---
title: 中斷性變更的類型
description: 瞭解 .NET 如何嘗試為開發人員提供跨 .NET 版本的相容性，以及何種變更視為重大變更。
ms.date: 01/28/2021
ms.openlocfilehash: d539a82b21abc4df8d726673ef728020f36551bf
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216034"
---
# <a name="changes-that-affect-compatibility"></a>影響相容性的變更

在整個歷程記錄中，.NET 已嘗試維持從版本到版本的高階相容性，以及跨 .NET 的各項執行。 相較于 .NET Framework，雖然 .NET 5 (和 .NET Core) 和更新版本可視為新的技術，但是有兩個主要因素會限制這項 .NET 的執行能力與 .NET Framework 相互分離：

- 最初開發或是繼續開發 .NET Framework 應用程式的大量開發人員。 他們預期跨 .NET 實作有一致的行為。

- .NET Standard 程式庫專案可讓開發人員建立以 .NET Framework 和 .NET 5 (和 .NET Core) 和更新版本所共用的通用 Api 為目標的程式庫。 開發人員預期在 .NET 5 應用程式中使用的程式庫，其行為應該與 .NET Framework 應用程式中使用的相同程式庫相同。

除了 .NET 執行的相容性之外，開發人員還預期在 .NET 的各版本之間有高階的相容性。 尤其是針對舊版 .NET Core 所撰寫的程式碼應該在 .NET 5 或更新版本上順暢地執行。 事實上，許多開發人員預期在新發行的 .NET 版本中找到的新 Api，也應該與引進這些 Api 的發行前版本相容。

本文概述會影響相容性的變更，以及 .NET 小組評估各種變更類型的方式。 瞭解 .NET 團隊如何進行可能的重大變更，對於開啟可修改 [現有 .Net api](https://github.com/dotnet/runtime)行為的提取要求的開發人員而言特別有用。

下列各節說明對 .NET Api 所做的變更分類，以及其對應用程式相容性的影響。 您可以✔️、不允許 ❌ 或需要判斷變更，以及如何❓上一個行為的可預測、明顯和一致的評估。

> [!NOTE]
>
> - 除了提供 .NET 程式庫變更的指南之外，程式庫開發人員也可以使用這些準則來評估其以多個 .NET 執行和版本為目標的程式庫變更。
> - 如需相容性類別的詳細資訊（例如，向前和回溯相容性），請參閱 [相容性](categories.md)。

## <a name="modifications-to-the-public-contract"></a>公用合約的修改

此類別中的變更會修改某個類型的公用介面區。 此類別中的大多數變更都是不允許的，因為它們違反了回溯相容性 (可讓使用舊版 API 開發的應用程式能夠在更新版本上執行而不必重新編譯的能力)。

### <a name="types"></a>類型

- ✔️ **允許：當介面已由基底類型執行時，從類型中移除介面實** 作為

- ❓**需要判斷：將新的介面實作為型** 別

  這是一個可接受的變更，因為它不會對現有的用戶端產生負面影響。 對類型的任何變更都必須在此處定義的可接受變更的界限內運作，以使新實作維持可接受。 如果您要加入的介面會直接影響設計工具或序列化程式產生無法在低層級取用之程式碼或資料的能力，請格外小心。 其中一個範例是 <xref:System.Runtime.Serialization.ISerializable> 介面。

- ❓ **需要判斷：引進新的基類**

  如果型別不會引進任何新的 [抽象](../../csharp/language-reference/keywords/abstract.md) 成員，或變更現有型別的語義或行為，則可以將型別引進兩個現有的型別。 例如，在 .NET Framework 2.0 中，<xref:System.Data.Common.DbConnection> 類別成為 <xref:System.Data.SqlClient.SqlConnection> 的新基底類別，它先前直接衍生自 <xref:System.ComponentModel.Component>。

- **允許✔️：將類型從某個元件移至另一個元件**

  *舊* 的元件必須以 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> 指向新元件的來標記。

- **允許✔️：將 [結構](../../csharp/language-reference/builtin-types/struct.md)類型變更為 `readonly struct` 類型**

  `readonly struct`不允許將類型變更為 `struct` 類型。

- ✔️ **允許：當沒有 *可存取* 的 (公用或受保護) 函式時，將 [Sealed](../../csharp/language-reference/keywords/sealed.md)或 [abstract](../../csharp/language-reference/keywords/abstract.md)關鍵字加入至類型**

- **允許✔️：擴充類型的可見度**

- ❌不 **允許：變更型別的命名空間或名稱**

- ❌不 **允許：重新命名或移除公用類型**

   這會中斷使用已重新命名或已移除之型別的所有程式碼。

- ❌**不允許：變更列舉的基礎類型**

   這是編譯時期和行為的中斷性變更，以及可以使屬性引數無法進行剖析的二進位中斷性變更。

- ❌**不允許：密封先前未密封的型** 別

- ❌**不允許：將介面加入至介面的基底類型集合**

   如果介面實作先前未實作的介面，則實作介面原始版本的所有型別都會中斷。

- ❓ **需要判斷：從基類集合或從實介面集的介面中移除類別**

  介面移除規則有一個例外：您可以新增衍生自已移除之介面的介面實作。 例如，如果型別或介面現在實作 <xref:System.ComponentModel.IComponent> (它會實作 <xref:System.IDisposable>)，則可以移除 <xref:System.IDisposable>。

- ❌不 **允許：將 `readonly struct` 類型變更為 [結構](../../csharp/language-reference/builtin-types/struct.md) 類型**

  `struct`不過，您可以將類型變更為 `readonly struct` 類型。

- ❌不 **允許：將 [結構](../../csharp/language-reference/builtin-types/struct.md)類型變更為 `ref struct` 類型，** 反之亦然

- ❌不 **允許：減少類型的可見度**

   但是，允許增加型別的可見性。

### <a name="members"></a>成員

- **允許✔️：展開非 [虛擬](../../csharp/language-reference/keywords/sealed.md)成員的可見度**

- **允許✔️：將抽象成員新增至無法 *存取* (公用或受保護) 的函式，或類型為 [密封](../../csharp/language-reference/keywords/sealed.md)的公用類型**

  但是，不允許將抽象成員新增至具有可存取 (公用或受保護) 建構函式且不是 `sealed` 的型別。

- ✔️ **允許：當類型無法存取 (公用或受保護) 的函式，或類型為 [密封](../../csharp/language-reference/keywords/sealed.md)時，限制 [受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度**

- **允許✔️：將成員移至階層中較高層級的類別，而不是移除它的類型**

- **允許✔️：新增或移除覆寫**

  引進覆寫可能會導致先前的取用者在呼叫 [base](../../csharp/language-reference/keywords/base.md)時略過覆寫。

- ✔️ **允許：如果類別先前沒有任何函式，將函式新增至類別，以及無參數的** 函式

   但是，不允許將建構函式新增至先前沒有建構函式且沒有新增無參數建構函式的類別。

- **允許✔️：將成員從 [abstract](../../csharp/language-reference/keywords/abstract.md)變更為 [virtual](../../csharp/language-reference/keywords/virtual.md)**

- **允許✔️：從 `ref readonly` `ref` 虛擬方法或介面變更為傳回值 ()**

- ✔️ **允許：從欄位移除 [readonly](../../csharp/language-reference/keywords/readonly.md) ，除非欄位的靜態類型是可** 變動的實數值型別

- **允許✔️：呼叫先前未定義的新事件**

- ❓**需要判斷：將新的實例欄位新增至型** 別

   此變更會影響序列化。

- ❌不 **允許：重新命名或移除公用成員或參數**

   這會中斷使用已重新命名或已移除之成員或參數的所有程式碼。

   這包括從屬性中移除或重新命名 getter 或 setter，以及重新命名或移除列舉成員。

- ❌**不允許：將成員新增至介面**

- ❌不 **允許：變更公用常數或列舉成員的值**

- ❌不 **允許：變更屬性、欄位、參數或傳回值的類型**

- ❌不 **允許：新增、移除或變更參數的順序**

- ❌不 **允許：從參數新增或移除 [in](../../csharp/language-reference/keywords/in.md)、 [out](../../csharp/language-reference/keywords/out.md) 或 [ref](../../csharp/language-reference/keywords/ref.md) 關鍵字**

- ❌不 **允許：重新具名引數 (包括變更其大小寫)**

  這會視為中斷的原因有二：

  - 它中斷了晚期繫結的案例，例如 Visual Basic 中的晚期繫結功能和 C# 中的 [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type)。

  - 當開發人員使用[具名引數](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)時，它會中斷[來源相容性](categories.md#source-compatibility)。

- ❌不 **允許：從傳回 `ref` 值變更為傳回 `ref readonly` 值**

- ❌️不 **允許： `ref readonly` `ref` 在虛擬方法或介面上從變更為傳回值**

- ❌不 **允許：新增或移除成員的 [抽象](../../csharp/language-reference/keywords/abstract.md)**

- ❌不 **允許：從成員中移除 [虛擬](../../csharp/language-reference/keywords/virtual.md) 關鍵字**

  雖然這通常不是一個中斷性變更，因為 C# 編譯器傾向於發出 [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) 中繼語言 (IL) 指令以呼叫非虛擬方法 (`callvirt` 會執行 Null 檢查，而正常呼叫不會)，由於以下幾個原因，此行為並不是不變的：
  - C# 不是 .NET 以其為目標的唯一語言。

  - 只要目標方法為非虛擬且可能不是 Null 時 (例如透過 [?. null 傳播運算子](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)存取的方法)，C# 編譯器就會漸漸地嘗試將 `callvirt` 最佳化為正常呼叫。

  使方法成為虛擬表示取用者程式碼通常最後會以非虛擬方式呼叫它。

- ❌不 **允許：將 [虛擬](../../csharp/language-reference/keywords/virtual.md) 關鍵字新增至成員**

- ❌不 **允許：讓虛擬成員成為抽象**

  [虛擬成員](../../csharp/language-reference/keywords/virtual.md)提供了一種方法實作，可以由衍生類別覆寫。 [抽象成員](../../csharp/language-reference/keywords/abstract.md)不提供任何實作，且必須被覆寫。

- ❌**不允許：將抽象成員新增至可存取 (公用或受保護) 的函式，且未 [密封](../../csharp/language-reference/keywords/sealed.md)的公用類型**

- ❌不 **允許：從成員新增或移除 [靜態](../../csharp/language-reference/keywords/static.md) 關鍵字**

- ❌不 **允許：加入可防止現有多載的多載，並定義不同的行為**

  這會中斷繫結到先前多載的現有用戶端。 例如，如果某個類別具有接受 <xref:System.UInt32> 的方法的單一版本，則現有的取用者在傳遞 <xref:System.Int32> 值時將成功繫結至該多載。 但是，如果新增接受 <xref:System.Int32> 的多載，則在重新編譯或使用晚期繫結時，編譯器現在會繫結至新的多載。 如果產生不同的行為，這是一個中斷性變更。

- ❌**不允許：將函式新增至先前沒有任何函式的類別，而不新增無參數的** 函式

- ❌️不 **允許：將 [readonly](../../csharp/language-reference/keywords/readonly.md) 加入至欄位**

- ❌不 **允許：減少成員的可見度**

   這包括減少 [受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度（當有 *可存取* 的 (`public` 或 `protected`) 的函式，且類型 *未*[密封](../../csharp/language-reference/keywords/sealed.md)時）。 如果不是這種情況，則允許降低受保護成員的可見性。

   允許提高成員的可見度。

- ❌不 **允許：變更成員的類型**

   無法修改方法的傳回值，或屬性或欄位的型別。 例如，傳回 <xref:System.Object> 之方法的簽章不能變更為傳回 <xref:System.String>，反之亦然。

- ❌**不允許：將欄位新增至先前沒有狀態的結構**

  只要變數型別是無狀態結構，明確指派規則就允許使用未初始化的變數。 如果將結構設定為具狀態，程式碼最後可能會遇到未初始化的資料。 這可能是一個來源中斷和二進位中斷性變更。

- ❌**不允許：引發先前從未引發的現有事件**

## <a name="behavioral-changes"></a>行為變更

### <a name="assemblies"></a>組件

- **允許✔️：仍支援相同平臺時，讓元件可** 攜

- ❌**不允許：變更元件的名稱**
- ❌**不允許：變更元件的公開金鑰**

### <a name="properties-fields-parameters-and-return-values"></a>屬性、欄位、參數與傳回值

- **允許✔️：將屬性、欄位、傳回值或 [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)參數的值變更為更衍生的類型**

  例如，傳回 <xref:System.Object> 型別的方法可以傳回 <xref:System.String> 執行個體。 (但是，無法變更方法簽章。)

- **允許✔️：如果成員不是 [虛擬](../../csharp/language-reference/keywords/virtual.md)的，則增加屬性或參數的可接受值範圍**

  雖然可以傳遞給方法或由成員傳回的值範圍可以展開，但參數或成員類型則不能。 例如，雖然傳遞至方法的值可以從 0-124 擴充至 0-255，但參數類型無法從 <xref:System.Byte> 變更為 <xref:System.Int32>。

- ❌**不允許：如果成員為 [虛擬](../../csharp/language-reference/keywords/virtual.md)，則增加屬性或參數的可接受值範圍**

   此變更會中斷現有的覆寫成員，這些成員將無法在擴充的值範圍內正常執行。

- ❌不 **允許：減少屬性或參數的可接受值範圍**

- ❌不 **允許：增加屬性、欄位、傳回值或 [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數的傳回值範圍**

- ❌不 **允許：變更屬性、欄位、方法傳回值或 [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數的傳回值**

- ❌不 **允許：變更屬性、欄位或參數的預設值**

- ❌不 **允許：變更數值傳回值的有效位數**

- ❓ **需要判斷：剖析輸入和擲回新的例外狀況的變更， (即使檔中未指定剖析行為**

### <a name="exceptions"></a>例外狀況

- 允許✔️：擲回 **比現有例外狀況更多的衍生例外** 狀況

  因為新的例外狀況是現有例外狀況的子類別，所以先前的例外狀況處理程式碼會繼續處理例外狀況。 例如，在 .NET Framework 4 中，文化特性建立和擷取方法已開始擲回 <xref:System.Globalization.CultureNotFoundException> 而不是 <xref:System.ArgumentException> (如果找不到文化特性)。 因為 <xref:System.Globalization.CultureNotFoundException> 衍生自 <xref:System.ArgumentException>，所以這是一個可接受的變更。

- 允許✔️：擲回 **比 <xref:System.NotSupportedException> 、 <xref:System.NotImplementedException> 、、 <xref:System.NullReferenceException> 更明確的例外** 狀況

- 允許✔️：擲回 **被視為無法** 復原的例外狀況

  無法復原的例外狀況不應該攔截，而應該由高層級追補處理常式處理。 因此，使用者不應該擁有攔截這些明確例外狀況的程式碼。 無法復原的例外狀況有：

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **允許✔️：在新的程式碼路徑中擲回新的例外** 狀況

  例外狀況必須只套用至新的程式碼路徑，該路徑會以新的參數值或狀態執行，而且無法由以舊版為目標的現有程式碼執行。

- **允許✔️：移除例外狀況以啟用更健全的行為或新案例**

  例如，之前只處理正值並擲回 <xref:System.ArgumentOutOfRangeException> 的 `Divide` 方法可以變更為支援負值和正值，而不擲回例外狀況。

- **允許✔️：變更錯誤訊息的文字**

  開發人員不應該依賴錯誤訊息的文字，這也會根據使用者的文化特性而變更。

- ❌**不允許：擲回例外狀況的其他任何情況下未列出**

- ❌**不允許：移除上方未列出的任何其他案例中的例外狀況**

### <a name="attributes"></a>屬性

- **允許✔️：變更 *不可* 觀察的屬性值**

- ❌***不* 允許：變更可觀察的屬性值**

- ❓ **需要判斷：移除屬性**

  在大部分情況下，移除屬性 (例如<xref:System.NonSerializedAttribute>) 是一個中斷性變更。

## <a name="platform-support"></a>平台支援

- **允許✔️：在先前不支援的平臺上支援操作**

- ❌**不允許：不支援或現在針對平臺上先前支援的作業要求特定的 service pack**

## <a name="internal-implementation-changes"></a>內部實作的變更

- ❓ **需要判斷：變更內部型別的介面區**

   通常允許此類變更，儘管它們可能會中斷私人反映。 在一些熱門的協力廠商程式庫或大量開發人員依賴內部 API 的案例中，可能不允許此類變更。

- ❓**需要判斷：變更成員的內部實** 作為

  通常允許這些變更，儘管它們可能會中斷私人反映。 在一些客戶程式碼經常依賴私人反映或變更引進非預期之副作用的情況下，可能不允許這些變更。

- **允許✔️：改善作業的效能**

   修改作業效能的能力是很重要的，但此類變更可能會中斷仰賴目前作業速度的程式碼。 對於仰賴非同步作業時間的程式碼尤其如此。 效能變更應該不會影響 API 的其他行為，否則，變更將會中斷。

- **允許✔️：間接 (，而且通常會) 變更作業的效能**

  如果由於某些其他原因而未將相關變更歸類為中斷，則這是可以接受的。 通常，需要採取可能包括額外的作業或新增新功能的動作。 這幾乎一律會影響效能，但對於使相關 API 如預期般運作至關重要。

- ❌不 **允許：將同步 API 變更為非同步 (，反之亦然)**

## <a name="code-changes"></a>程式碼變更

- **允許✔️：將 [](../../csharp/language-reference/keywords/params.md)參數加入至參數**

- ❌不 **允許：將 [結構](../../csharp/language-reference/builtin-types/struct.md)變更為 [類別](../../csharp/language-reference/keywords/class.md)，** 反之亦然

- ❌不 **允許：將 [Checked](../../csharp/language-reference/keywords/virtual.md) 關鍵字加入至程式碼區塊**

   此變更可能會導致先前執行的程式碼擲回 <xref:System.OverflowException> 且無法接受。

- ❌不 **允許： [](../../csharp/language-reference/keywords/params.md)從參數中移除參數**

- ❌不 **允許：變更引發事件的順序**

  開發人員可以合理地預期事件以相同的順序引發，而開發人員程式碼經常會取決於事件的引發順序。

- ❌**不允許：移除指定動作上引發的事件**

- ❌**不允許：變更指定事件的呼叫次數**

- ❌**不允許：將加入 <xref:System.FlagsAttribute> 至列舉型** 別
