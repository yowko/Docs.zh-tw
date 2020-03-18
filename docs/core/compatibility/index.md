---
title: 中斷性變更的類型
description: 瞭解 .NET Core 如何嘗試維護跨 .NET 版本的開發人員的相容性，以及哪種更改被視為重大更改。
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628588"
---
# <a name="changes-that-affect-compatibility"></a>影響相容性的更改

縱觀其歷程記錄，.NET 一直嘗試維護 .NET 各版本之間以及各種變體之間的相容性。 在 .NET Core 中仍是如此。 雖然 .NET Core 可以視為是獨立於 .NET Framework 之外的新技術，但是有兩個主要因素限制了 .NET Core 從 .NET Framework 分離的能力：

- 最初開發或是繼續開發 .NET Framework 應用程式的大量開發人員。 他們預期跨 .NET 實作有一致的行為。

- .NET Standard 程式庫專案可讓開發人員建立以 .NET Core 和 .NET Framework 所共用之通用 API 為目標的程式庫。 開發人員預期 .NET Core 應用程式中使用之程式庫的行為，應與 .NET Framework 應用程式中所使用的程式庫相同。

除了 .NET 實作之間的相容性之外，開發人員還希望 .NET Core 版本之間具有高層級相容性。 特別是，針對較早版本的 .NET Core 所撰寫的程式碼應該在新版的 .NET Core 上順暢地執行。 實際上，許多開發人員預期在新發行的 .NET Core 版本中找到的新 API，也應該與引入那些 API 的發行前版本相容。

此文章概述相容性變更 (或中斷性變更) 的類別，以及 .NET 小組評估每個類別中的變更的方式。 瞭解 .NET 團隊如何處理可能的突發更改對於在[dotnet/運行時](https://github.com/dotnet/runtime)GitHub 存儲庫中打開拉取請求的開發人員來說尤其有用，這些開發人員修改了現有 API 的行為。

> [!NOTE]
> 如需相容性類別的定義，例如二進位檔案相容性和回溯相容性，請參閱[中斷性變更類別](categories.md)。

以下各節介紹對 .NET 核心 API 所做的更改類別及其對應用程式相容性的影響。 更改要麼允許✔️，要麼不允許❌，要麼需要判斷和評估，以及評估以前的行為❓的可預測性、明顯性和一致性。

> [!NOTE]
> 除了作為如何評估 .NET Core 程式庫變更的指南之外，程式庫開發人員也可以使用這些準則來評估其程式庫 (以多個 .NET 實作和版本為目標) 的變更。

## <a name="modifications-to-the-public-contract"></a>公用合約的修改

此類別中的變更會修改某個類型的公用介面區。 此類別中的大多數變更都是不允許的，因為它們違反了回溯相容性** (可讓使用舊版 API 開發的應用程式能夠在更新版本上執行而不必重新編譯的能力)。

### <a name="types"></a>類型

- ✔️**允許：當介面已由基類型實現時，從類型中刪除介面實現**

- ❓**要求：向類型添加新的介面實現**

  這是一個可接受的變更，因為它不會對現有的用戶端產生負面影響。 對類型的任何變更都必須在此處定義的可接受變更的界限內運作，以使新實作維持可接受。 如果您要加入的介面會直接影響設計工具或序列化程式產生無法在低層級取用之程式碼或資料的能力，請格外小心。 其中一個範例是 <xref:System.Runtime.Serialization.ISerializable> 介面。

- ❓**要求：引入新的基類**

  如果類型不引入任何新的[抽象](../../csharp/language-reference/keywords/abstract.md)成員或更改現有類型的語義或行為，則可以將其引入到兩種現有類型的層次結構中。 例如，在 .NET Framework 2.0 中，<xref:System.Data.Common.DbConnection> 類別成為 <xref:System.Data.SqlClient.SqlConnection> 的新基底類別，它先前直接衍生自 <xref:System.ComponentModel.Component>。

- ✔️**允許：將類型從一個程式集移動到另一個程式集**

  *舊*程式集必須用<xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>指向新程式集的 標記。

- ✔️**允許：將[結構](../../csharp/language-reference/builtin-types/struct.md)類型`readonly struct`更改為類型**

  不允許將`readonly struct`類型更改為`struct`類型。

- ✔️**允許：在沒有*可訪問*（公共或受保護）建構函式時，將[密封](../../csharp/language-reference/keywords/sealed.md)或[抽象](../../csharp/language-reference/keywords/abstract.md)關鍵字添加到類型中**

- ✔️**允許：擴大某種類型的可見度**

- ❌**取消：更改類型的命名空間或名稱**

- ❌**取消：重命名或刪除公共類型**

   這會中斷使用已重新命名或已移除之型別的所有程式碼。

- ❌**取消：更改枚舉的基礎類型**

   這是編譯時期和行為的中斷性變更，以及可以使屬性引數無法進行剖析的二進位中斷性變更。

- ❌**非封閉：密封以前未密封的類型**

- ❌**拒絕：將介面添加到介面的基類型集**

   如果介面實作先前未實作的介面，則實作介面原始版本的所有型別都會中斷。

- ❓**要求：從基類集或介面從已實現的介面集中刪除類**

  介面移除規則有一個例外：您可以新增衍生自已移除之介面的介面實作。 例如，如果型別或介面現在實作 <xref:System.ComponentModel.IComponent> (它會實作 <xref:System.IDisposable>)，則可以移除 <xref:System.IDisposable>。

- ❌**拒絕：將`readonly struct`類型更改為[結構](../../csharp/language-reference/builtin-types/struct.md)類型**

  但是，`struct`允許將類型更改為`readonly struct`類型。

- ❌**拒絕：將[結構](../../csharp/language-reference/builtin-types/struct.md)類型更改為`ref struct`類型，反之亦然**

- ❌**禁止：降低類型的可見度**

   但是，允許增加型別的可見性。

### <a name="members"></a>成員

- ✔️**允許：擴展不是[虛擬](../../csharp/language-reference/keywords/sealed.md)成員的可見度**

- ✔️**允許：將抽象成員添加到沒有*可訪問*（公共或受保護）建構函式或該類型[已密封](../../csharp/language-reference/keywords/sealed.md)的公共類型**

  但是，不允許將抽象成員新增至具有可存取 (公用或受保護) 建構函式且不是 `sealed` 的型別。

- ✔️**允許：當類型沒有可訪問（公共或受保護）建構函式或類型[密封](../../csharp/language-reference/keywords/sealed.md)時，限制[受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度**

- ✔️**允許：將成員移動到層次結構中比從中刪除該成員的類型更高的類中**

- ✔️**允許：添加或刪除覆蓋**

  引入重寫可能會導致以前的消費者在調用[base](../../csharp/language-reference/keywords/base.md)時跳過重寫。

- ✔️**允許：如果類以前沒有建構函式，則將建構函式添加到類和無參數建構函式**

   但是，不允許將建構函式新增至先前沒有建構函式且沒有** 新增無參數建構函式的類別。

- ✔️**允許：將成員從[抽象](../../csharp/language-reference/keywords/abstract.md)更改為[虛擬](../../csharp/language-reference/keywords/virtual.md)**

- ✔️**允許：從`ref readonly`更改為`ref`傳回值（虛擬方法或介面除外）**

- ✔️**允許：從欄位中刪除[唯讀](../../csharp/language-reference/keywords/readonly.md)，除非欄位的靜態類型是可變數值型別**

- ✔️**允許：調用以前未定義的新事件**

- ❓**要求：向類型添加新實例欄位**

   此變更會影響序列化。

- ❌**取消：重命名或刪除公共成員或參數**

   這會中斷使用已重新命名或已移除之成員或參數的所有程式碼。

   這包括從屬性中刪除或重命名 getter 或 setter，以及重命名或刪除枚舉成員。

- ❌**拒絕：將成員添加到介面**

- ❌**取消：更改公共常量或枚舉成員的值**

- ❌**取消：更改屬性、欄位、參數或傳回值的類型**

- ❌**取消：添加、刪除或更改參數的順序**

- ❌**拒絕：從參數[中](../../csharp/language-reference/keywords/in.md)添加或刪除 中[、out](../../csharp/language-reference/keywords/out.md)或[ref](../../csharp/language-reference/keywords/ref.md)關鍵字**

- ❌**取消：重具名引數（包括更改其大小寫）**

  這會視為中斷的原因有二：

  - 它中斷了晚期繫結的案例，例如 Visual Basic 中的晚期繫結功能和 C# 中的 [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type)。

  - 當開發人員使用[具名引數](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments)時，它會中斷[來源相容性](categories.md#source-compatibility)。

- ❌**拒絕：從`ref`傳回值更改為`ref readonly`傳回值**

- ❌️**拒絕：在虛擬方法或`ref readonly`介面上`ref`從 更改為傳回值**

- ❌**禁止：從成員添加或刪除[摘要](../../csharp/language-reference/keywords/abstract.md)**

- ❌**取消：從成員中刪除[虛擬](../../csharp/language-reference/keywords/virtual.md)關鍵字**

  雖然這通常不是一個中斷性變更，因為 C# 編譯器傾向於發出 [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) 中繼語言 (IL) 指令以呼叫非虛擬方法 (`callvirt` 會執行 Null 檢查，而正常呼叫不會)，由於以下幾個原因，此行為並不是不變的：
  - C# 不是 .NET 以其為目標的唯一語言。

  - 只要目標方法為非虛擬且可能不是 Null 時 (例如透過 [?. null 傳播運算子](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)存取的方法)，C# 編譯器就會漸漸地嘗試將 `callvirt` 最佳化為正常呼叫。

  使方法成為虛擬表示取用者程式碼通常最後會以非虛擬方式呼叫它。

- ❌**拒絕：將[虛擬](../../csharp/language-reference/keywords/virtual.md)關鍵字添加到成員**

- ❌**內容：使虛擬成員抽象**

  [虛擬成員](../../csharp/language-reference/keywords/virtual.md)提供了一種方法實作，可以** 由衍生類別覆寫。 [抽象成員](../../csharp/language-reference/keywords/abstract.md)不提供任何實作，且必須** 被覆寫。

- ❌**拒絕：將抽象成員添加到具有可訪問（公共或受保護）建構函式且未[密封](../../csharp/language-reference/keywords/sealed.md)的公共類型**

- ❌**取消：從成員添加或刪除[靜態](../../csharp/language-reference/keywords/static.md)關鍵字**

- ❌**取消：添加排除現有重載並定義其他行為的重載**

  這會中斷繫結到先前多載的現有用戶端。 例如，如果某個類別具有接受 <xref:System.UInt32> 的方法的單一版本，則現有的取用者在傳遞 <xref:System.Int32> 值時將成功繫結至該多載。 但是，如果新增接受 <xref:System.Int32> 的多載，則在重新編譯或使用晚期繫結時，編譯器現在會繫結至新的多載。 如果產生不同的行為，這是一個中斷性變更。

- ❌**拒絕：將建構函式添加到以前沒有建構函式的類，而不添加無參數建構函式**

- ❌️**拒絕：將[可讀添加到](../../csharp/language-reference/keywords/readonly.md)欄位**

- ❌**禁止：降低成員的可見度**

   這包括在*存在可訪問*（`public``protected`或 ） 建構函式且類型*未*[密封](../../csharp/language-reference/keywords/sealed.md)時降低[受保護](../../csharp/language-reference/keywords/protected.md)成員的可見度。 如果不是這種情況，則允許降低受保護成員的可見性。

   允許增加成員的可見度。

- ❌**取消：更改成員的類型**

   無法修改方法的傳回值，或屬性或欄位的型別。 例如，傳回 <xref:System.Object> 之方法的簽章不能變更為傳回 <xref:System.String>，反之亦然。

- ❌**拒絕：將欄位添加到以前沒有狀態的結構**

  只要變數型別是無狀態結構，明確指派規則就允許使用未初始化的變數。 如果將結構設定為具狀態，程式碼最後可能會遇到未初始化的資料。 這可能是一個來源中斷和二進位中斷性變更。

- ❌**未通過：在以前從未觸發現有事件時觸發它**

## <a name="behavioral-changes"></a>行為變更

### <a name="assemblies"></a>組件

- ✔️**允許：在仍支援相同平臺時使元件便於使用**

- ❌**取消：更改程式集的名稱**
- ❌**取消：更改程式集的公開金鑰**

### <a name="properties-fields-parameters-and-return-values"></a>屬性、欄位、參數與傳回值

- ✔️**允許：將屬性、欄位、傳回值或[出](../../csharp/language-reference/keywords/out-parameter-modifier.md)參數的值更改為更派生的類型**

  例如，傳回 <xref:System.Object> 型別的方法可以傳回 <xref:System.String> 執行個體。 (但是，無法變更方法簽章。)

- ✔️**允許：如果成員不是[虛擬](../../csharp/language-reference/keywords/virtual.md)的，則增加屬性或參數的已接受值範圍**

  雖然可以傳遞給方法或由成員返回的值範圍可以展開，但參數或成員類型不能。 例如，雖然傳遞至方法的值可以從 0-124 擴充至 0-255，但參數類型無法從 <xref:System.Byte> 變更為 <xref:System.Int32>。

- ❌**禁止：如果成員為[虛擬](../../csharp/language-reference/keywords/virtual.md)，則增加屬性或參數的已接受值範圍**

   此變更會中斷現有的覆寫成員，這些成員將無法在擴充的值範圍內正常執行。

- ❌**取消：減小屬性或參數的已接受值範圍**

- ❌**取消：增加屬性、欄位、傳回值或[出參數](../../csharp/language-reference/keywords/out-parameter-modifier.md)的傳回值範圍**

- ❌**取消：更改屬性、欄位、方法傳回值或[out](../../csharp/language-reference/keywords/out-parameter-modifier.md)參數的傳回值**

- ❌**拒絕：更改屬性、欄位或參數的預設值**

- ❌**非分配：更改數值傳回值的精度**

- ❓**要求判斷：在分析輸入和引發新異常時發生更改（即使文檔中未指定分析行為**）

### <a name="exceptions"></a>例外狀況

- ✔️**允許：引發比現有異常更派生的異常**

  因為新的例外狀況是現有例外狀況的子類別，所以先前的例外狀況處理程式碼會繼續處理例外狀況。 例如，在 .NET Framework 4 中，文化特性建立和擷取方法已開始擲回 <xref:System.Globalization.CultureNotFoundException> 而不是 <xref:System.ArgumentException> (如果找不到文化特性)。 因為 <xref:System.Globalization.CultureNotFoundException> 衍生自 <xref:System.ArgumentException>，所以這是一個可接受的變更。

- ✔️**允許：引發比<xref:System.NotSupportedException>更具體的異常， <xref:System.NullReferenceException> <xref:System.NotImplementedException> **

- ✔️**允許：引發被視為不可恢復的異常**

  無法復原的例外狀況不應該攔截，而應該由高層級追補處理常式處理。 因此，使用者不應該擁有攔截這些明確例外狀況的程式碼。 無法復原的例外狀況有：

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- ✔️**允許：在新的代碼路徑中引發新的異常**

  該異常必須僅適用于使用新參數值或狀態執行且無法由面向早期版本的現有代碼執行的新代碼路徑。

- ✔️**允許：刪除異常以啟用更健壯的行為或新方案**

  例如，之前只處理正值並擲回 <xref:System.ArgumentOutOfRangeException> 的 `Divide` 方法可以變更為支援負值和正值，而不擲回例外狀況。

- ✔️**允許：更改錯誤訊息的文本**

  開發人員不應該依賴錯誤訊息的文字，這也會根據使用者的文化特性而變更。

- ❌**非保留：在上述未列出的任何其他情況下引發異常**

- ❌**非保留：刪除上述未列出的任何其他情況下的異常**

### <a name="attributes"></a>屬性

- ✔️**允許：更改*無法*觀察到的屬性的值**

- ❌**不可否認：更改可觀察屬性的值*is* **

- ❓**要求：刪除屬性**

  在大部分情況下，移除屬性 (例如<xref:System.NonSerializedAttribute>) 是一個中斷性變更。

## <a name="platform-support"></a>平台支援

- ✔️**允許：支援以前不支援的平臺上的操作**

- ❌**取消：不支援或現在需要特定服務包，用於以前在平臺上支援的操作**

## <a name="internal-implementation-changes"></a>內部實作的變更

- ❓**要求：更改內部類型的表面積**

   通常允許此類變更，儘管它們可能會中斷私人反映。 在一些熱門的協力廠商程式庫或大量開發人員依賴內部 API 的案例中，可能不允許此類變更。

- ❓**要求：更改成員的內部實現**

  通常允許這些變更，儘管它們可能會中斷私人反映。 在一些客戶程式碼經常依賴私人反映或變更引進非預期之副作用的情況下，可能不允許這些變更。

- **✔️：提高操作性能**

   修改作業效能的能力是很重要的，但此類變更可能會中斷仰賴目前作業速度的程式碼。 對於仰賴非同步作業時間的程式碼尤其如此。 性能更改不應對相關 API 的其他行為產生影響;否則，更改將中斷。

- ✔️**允許：間接（而且經常不利）改變操作性能**

  如果由於某些其他原因而未將相關變更歸類為中斷，則這是可以接受的。 通常，需要採取可能包括額外的作業或新增新功能的動作。 這幾乎一律會影響效能，但對於使相關 API 如預期般運作至關重要。

- ❌**非同步：將同步 API 更改為非同步（反之亦然）**

## <a name="code-changes"></a>程式碼變更

- ✔️**允許：向參數添加[參數](../../csharp/language-reference/keywords/params.md)**

- ❌**拒絕：將[結構](../../csharp/language-reference/builtin-types/struct.md)更改為[類](../../csharp/language-reference/keywords/class.md)，反之亦然**

- ❌**拒絕：將[選中](../../csharp/language-reference/keywords/virtual.md)的關鍵字添加到代碼塊**

   此變更可能會導致先前執行的程式碼擲回 <xref:System.OverflowException> 且無法接受。

- ❌**取消：從參數中刪除[參數](../../csharp/language-reference/keywords/params.md)**

- ❌**取消：變更事件觸發順序**

  開發人員可以合理地預期事件以相同的順序引發，而開發人員程式碼經常會取決於事件的引發順序。

- ❌**取消：刪除對給定操作引發事件**

- ❌**取消：更改調用給定事件的次數**

- ❌**拒絕：將 添加到<xref:System.FlagsAttribute>枚舉類型**
