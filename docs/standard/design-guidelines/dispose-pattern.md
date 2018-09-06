---
title: Dispose 模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff52e17cfe4a4236e4d165c0961ca3a23fed9a72
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864640"
---
# <a name="dispose-pattern"></a>Dispose 模式
所有程式執行期間都取得一或多個系統資源，例如記憶體、 系統的控制代碼或資料庫連接。 開發人員需要時務必謹慎使用這類系統的資源，因為它們必須在取得並使用後釋放。  
  
 CLR 會提供自動記憶體管理的支援。 受控記憶體 (使用 C# 運算子配置的記憶體`new`) 不需要明確釋放。 它會自動釋放記憶體回收行程 (GC)。 這可讓開發人員從繁瑣且更釋出記憶體的工作，並已針對.NET Framework 所提供前所未有的產能的主要原因之一。  
  
 不幸的是，受管理的記憶體只是許多類型的系統資源。 除了受管理的記憶體資源仍然必須明確地釋放，並稱為 unmanaged 資源。 GC 已沒有特別設計來管理這類未受管理的資源，這表示負責管理 unmanaged 的資源存在於開發人員手。  
  
 CLR 提供一些協助中釋放 unmanaged 的資源。 <xref:System.Object?displayProperty=nameWithType> 宣告虛擬方法<xref:System.Object.Finalize%2A>（也稱為 「 完成項 」） 的 gc 之前呼叫物件的記憶體由 GC 回收，且可以釋放 unmanaged 的資源。 覆寫完成項的類型被指可完成的類型。  
  
 雖然在某些案例中清除作業有效完成項，它們會有兩個很大的缺點：  
  
-   GC 會偵測到的物件可供回收時，會呼叫完成項。 這會發生於未定一段時間後不再需要資源。 當開發人員無法，或想要釋放的資源和資源的完成項當發行的時間之間的延遲可能會在取得許多很少資源 （可以輕鬆地耗盡的資源） 的程式，或在無法接受資源可使用 （例如，大型的 unmanaged 的記憶體緩衝區） 中，將高成本的情況。  
  
-   在 CLR 需要呼叫完成項，它必須延後收集物件的記憶體回收 （集合之間執行的完成項） 的捨入的下一步。 這表示，在物件的記憶體 （和所有物件，它是指） 將不會釋放段較長的時間。  
  
 因此，在完成項信賴憑證者可能不適合在許多情況下，當務必盡可能的情況下，快速回收 unmanaged 的資源，很少資源，在處理時，或在高度高效能在其中的案例中新增的 GC 額外負荷最終處理的是無法接受。  
  
 「 架構 」 提供<xref:System.IDisposable?displayProperty=nameWithType>應該為開發人員提供手動的方式來釋放 unmanaged 的資源，因為它們不需要實作的介面。 它也提供<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>方法，可以告訴 GC，物件已手動處置的不需要完成，在此情況下之前回收物件的記憶體。 型別都會實作`IDisposable`介面就是可處置的類型。  
  
 Dispose 模式要標準化的使用方式與實作完成項和`IDisposable`介面。  
  
 模式的主要動機是要減少的實作的複雜性<xref:System.Object.Finalize%2A>而<xref:System.IDisposable.Dispose%2A>方法。 複雜度是源自方法共用 （差異會在本章稍後所述） 的部分而非全部的程式碼路徑的事實。 此外，有的發展的語言支援具決定性的資源管理相關的模式的一些項目歷程記錄的原因。  
  
 **✓ DO** 包含的可處置的類型執行個體的型別上實作基本的處置模式。 請參閱[基本的處置模式](#basic_pattern)區段，如需有關基本模式。  
  
 如果類型是負責其他可處置物件的存留期，開發人員需要想辦法太處置它們。 使用容器的`Dispose`方法是便利的方式，才能達到這個目的。  
  
 **✓ DO** 實作基本的處置模式，並提供完成項型別上保留的資源需要明確地釋放沒有完成項。  
  
 比方說，您應該實作模式儲存未受管理的記憶體緩衝區的型別上。 [最終處理的型別](#finalizable_types)章節討論與實作完成項相關的指導方針。  
  
 **✓ CONSIDER** 實作基本的處置模式類別本身不保存 unmanaged 資源，或是可處置的物件但可能會有執行的子類型。  
  
 最佳的範例是<xref:System.IO.Stream?displayProperty=nameWithType>類別。 雖然很不保留任何資源的抽象基底類別，但大部分其子類別的執行，因為這個緣故，它會實作此模式。  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>基本的處置模式  
 模式的基本實作，包括實作`System.IDisposable`介面和宣告`Dispose(bool)`方法，會實作所有的資源清除邏輯，以在之間共用`Dispose`方法，並選擇性完成項。  
  
 下列範例示範基本模式的簡單實作：  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder() {  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposing) {  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 布林值參數`disposing`表示方法從叫用`IDisposable.Dispose`實作或完成項。 `Dispose(bool)`實作應檢查參數，然後再存取其他參考物件 （例如，在上述範例中的資源欄位）。 從呼叫方法時，應該只能存取這類物件`IDisposable.Dispose`實作 (當`disposing`參數等於 true)。 如果方法會叫用完成項完成 (`disposing`為 false)，不應該存取其他物件。 原因是物件的完成，無法預期的順序，因此它們，或任何其相依性，可能會有已經結束。  
  
 此外，這一節適用於具有未實作 Dispose 模式的基底類別。 如果您繼承自的類別已實作的模式，只是覆寫`Dispose(bool)`方法，以提供其他資源的清除邏輯。  
  
 **✓ DO** 宣告 `protected virtual void Dispose(bool disposing)` 來釋放 unmanaged 的資源相關的方法來集中管理所有邏輯。  
  
 在此方法中，應該進行所有的資源清除。 這兩個完成項呼叫的方法和`IDisposable.Dispose`方法。 參數會是如果正在叫用完成項內，則為 false。 它應該用來確保任何最終處理期間執行的程式碼不會存取其他可完成的物件。 在下一節中詳述實作完成項的詳細資料。  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ DO** 實作 `IDisposable` 介面只呼叫 `Dispose(true)` 後面 `GC.SuppressFinalize(this)`。  
  
 若要在呼叫`SuppressFinalize`才應該發生`Dispose(true)`順利執行。  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X DO NOT** 進行無參數 `Dispose` 虛擬方法。  
  
 `Dispose(bool)`方法就是應該加以覆寫子類別。  
  
```csharp
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
```  
  
 **X DO NOT** 宣告的任何多載 `Dispose` 方法以外 `Dispose()` 和 `Dispose(bool)`。  
  
 `Dispose` 應視為協助編寫此模式，並防止困惑實作者、 使用者和編譯器的保留的字。 有些語言可能會選擇會自動在特定類型上實作此模式。  
  
 **✓ DO** 允許 `Dispose(bool)` 方法來呼叫一次以上。 方法可能會選擇第一個呼叫之後會執行任何動作。  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X AVOID** 擲回例外狀況從 `Dispose(bool)` 重大其中包含處理序已損毀的情況下除外 （流失，不一致的共用的狀態等。）。  
  
 使用者會預期呼叫`Dispose`將不會引發例外狀況。  
  
 如果`Dispose`可能會引發例外狀況，將不會執行進一步的 finally 區塊清除邏輯。 若要解決這個問題，使用者必須將每次呼叫`Dispose`(在 finally 區塊 ！) 在 try 區塊中，這會導致非常複雜的清除作業處理常式。 如果執行`Dispose(bool disposing)`方法中，永遠不會擲回的例外狀況，如果處置為 false。 如果完成項內容中執行，如此一來會終止處理序。  
  
 **✓ DO** 擲回 <xref:System.ObjectDisposedException> 從已經過處置物件後，無法使用的任何成員。  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething() {  
        if (disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
        ...  
    }  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ CONSIDER** 提供方法 `Close()`，除了 `Dispose()`，如果關閉是標準區域中的術語。  
  
 這樣一來，時，請務必`Close`實作相同`Dispose`，並考慮實作`IDisposable.Dispose`方法明確。  
  
```csharp
public class Stream : IDisposable {  
    IDisposable.Dispose() {  
        Close();  
    }  
    public void Close() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a>最終處理的類型  
 最終處理的型別會擴充基本的處置模式，藉由覆寫完成項，並提供最終處理程式碼路徑中的型別`Dispose(bool)`方法。  
  
 主要是因為您不能假設系統的狀態 （通常是有效的） 在執行期間，很難正確地實作完成項。 下列指導方針應該列入仔細考量。  
  
 請注意，有些指導方針套用不只是為`Finalize`方法，但任何程式碼呼叫來自完成項。 在其基本 Dispose 模式預先定義的情況下，這表示內部執行的邏輯`Dispose(bool disposing)`當`disposing`參數為 false。  
  
 如果基底類別已經是最終處理，而且會實作基本的處置模式，您不應該覆寫`Finalize`一次。 您應該改為只覆寫`Dispose(bool)`方法，以提供其他資源的清除邏輯。  
  
 下列程式碼會顯示可完成類型的範例：  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder() {  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing) {  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing) { // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    public void Dispose() {
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X AVOID** 進行最終處理的類型。  
  
 請仔細考慮的只要在其中您認為需要完成項。 沒有即時完成項，從效能和程式碼複雜度觀點來看的執行個體相關聯的成本。 偏好使用資源的包裝函式，例如<xref:System.Runtime.InteropServices.SafeHandle>封裝 unmanaged 的資源，可能的話，在此情況下完成項將不再需要因為包裝函式是負責它自己的資源清除。  
  
 **X DO NOT** 進行最終處理實值類型。  
  
 實際上只是參考型別取得完成由 CLR，因此任何嘗試對實值型別中的完成項將會被忽略。 C# 和 c + + 編譯器強制執行此規則。  
  
 **✓ DO** 讓類型變成可最終處理，如果類型是負責釋放 unmanaged 的資源，但是沒有自己的完成項。  
  
 當實作完成項，只要呼叫`Dispose(false)`內的所有資源清除邏輯隨時隨地`Dispose(bool disposing)`方法。  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing) {
        ...  
    }  
}  
```  
  
 **✓ DO** 每個可進行最終處理的類型上實作基本的處置模式。  
  
 這可讓使用者類型的方法來明確地執行具決定性的清除作業的完成項是負責那些相同的資源。  
  
 **X DO NOT** 存取在完成項程式碼路徑中，任何最終處理物件，因為有極大的風險，它們將已完成。  
  
 比方說，最終處理物件的另一個可完成物件 B 參考無法可靠地使用 B 中 A 的完成項，反之亦然。 以隨機順序 （除了關鍵結束的弱式排序保證），會呼叫完成項。  
  
 此外，請注意，靜態變數中儲存的物件將會收集在特定時間點期間的應用程式定義域卸載或結束處理程序。 存取最終處理物件 （或呼叫靜態方法，可能會使用儲存在靜態變數的值） 是指靜態變數可能不安全的如果<xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType>，則傳回 true。  
  
 **✓ DO** 請您 `Finalize` 受保護的方法。  
  
 C#、 c + + 和 VB.NET 開發人員不需要擔心這個問題，因為編譯器可以協助強制執行這項指導方針。  
  
 **X DO NOT** 讓例外狀況逸出與完成項邏輯，除了嚴重系統失敗。  
  
 如果來自完成項擲回例外狀況，CLR 就會關閉整個程序 （從.NET Framework 2.0 版)，防止其他完成項執行並以節制的方式將被釋放的資源。  
  
 **✓ CONSIDER** 建立和使用的重要變成可最終處理物件 (具有型別階層架構，其中包含的型別 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) 的情況下，在其中完成項絕對必須執行而且即使發生強制應用程式定義域卸載和執行緒中止。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [一般設計模式](../../../docs/standard/design-guidelines/common-design-patterns.md)  
- [記憶體回收](../../../docs/standard/garbage-collection/index.md)
