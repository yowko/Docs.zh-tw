---
title: "處置模式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Dispose 方法"
  - "類別庫設計方針 [.NET Framework] Dispose 方法"
  - "類別庫設計方針 [.NET Framework] 的 Finalize 方法"
  - "自訂 Dispose 方法名稱"
  - "Finalize 方法"
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# 處置模式
所有程式執行期間都取得一或多個系統資源，例如記憶體、 系統控制代碼或資料庫連接。 開發人員必須小心使用這類的系統資源，因為它們已取得並使用之後必須釋放它們。  
  
 CLR 提供自動記憶體管理支援。 Managed 記憶體 \(C\# 運算子所配置的記憶體 `new`\) 不需要明確釋放。 它會自動釋放記憶體回收行程 \(GC\)。 這可讓開發人員從繁瑣且更釋放記憶體的工作，並已針對.NET Framework 所提供前所未有的產能的主要原因之一。  
  
 不幸的是，受管理的記憶體只是許多類型的系統資源。 受管理的記憶體之外的資源仍必須明確釋放，統稱為 unmanaged 資源。 GC 特別並非設計來管理這類 unmanaged 的資源，這表示負責管理 unmanaged 的資源所在的開發人員手中。  
  
 CLR 提供一些協助釋放 unmanaged 的資源。<xref:System.Object?displayProperty=fullName> 宣告虛擬方法 <xref:System.Object.Finalize%2A> （也稱為完成項），gc 之前呼叫物件的記憶體由 GC 回收，且可以釋放 unmanaged 的資源。 覆寫完成項的型別稱為可最終處理的型別。  
  
 雖然在某些案例中清除有效完成項，它們會有兩個重大缺點︰  
  
-   GC 會偵測到的物件可供回收時，會呼叫完成項。 這會發生在尚無法確定一段時間之後不再需要的資源。 當開發人員可以或想要釋放的資源和資源所完成項當發行的時間之間的延遲可能會在取得許多很少資源 （可以輕鬆地耗盡資源） 的程式，或在資源有成本保持在使用 （例如，大量 unmanaged 的記憶體緩衝區） 的情況下，將無法接受。  
  
-   在 CLR 需要呼叫完成項，它必須延後的記憶體物件的集合 （集合之間執行的完成項） 記憶體回收的捨入的下一步\]。 這表示物件的記憶體 （和它所參考的所有物件） 將不會釋放的時間更長的時間。  
  
 因此，依賴完成項不可能適合在許多情況下，請務必處理很少的資源時，盡，回收 unmanaged 的資源時或在高高效能案例中加入的 GC 負荷的最終處理是不被接受。  
  
 這個架構會提供 <xref:System.IDisposable?displayProperty=fullName> 應該為開發人員提供由手動方法來釋放 unmanaged 的資源，因為不需要實作的介面。 它也提供 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 方法，可以告訴 GC 的物件已手動處置，因此不需要最終處理而失效，在此情況下之前回收物件的記憶體。 型別都會實作 `IDisposable` 介面就是可處置型別。  
  
 Dispose 模式是標準化的使用方式和實作完成項和 `IDisposable` 介面。  
  
 模式比對的主要動機是要減少實作的複雜性 <xref:System.Object.Finalize%2A> 和 <xref:System.IDisposable.Dispose%2A> 方法。 複雜度源自方法共用 （差異在本章稍後說明） 的部分而非全部的程式碼路徑的事實。 此外，還有歷史原因模式的演進，具決定性的資源管理的語言支援與相關的某些項目。  
  
 **✓ 執行** 包含可處置型別的執行個體的型別上實作基本的處置模式。 請參閱 [基本的處置模式](#basic_pattern) 基本模式的詳細資訊的區段。  
  
 如果類型是負責其他可處置物件的存留期，開發人員將需要處置，太方法。 使用容器的 `Dispose` 方法是方便您進行這項作業。  
  
 **✓ 執行** 實作基本的處置模式，並提供完成項型別上持有資源需要明確釋放並沒有完成項。  
  
 例如，應該在儲存 unmanaged 的記憶體緩衝區的型別上實作這個模式。[變成可最終處理的型別](#finalizable_types) 一節將討論與實作完成項相關的指導方針。  
  
 **✓ 考慮** 實作基本的處置模式類別本身不保存 unmanaged 資源，或可處置的物件但可能會有執行的子類型。  
  
 是一個絕佳範例 <xref:System.IO.Stream?displayProperty=fullName> 類別。 雖然它是不保留任何資源的抽象基底類別，它的子類別的大部分作業，並基於此原因，它會實作此模式。  
  
<a name="basic_pattern"></a>   
## 基本的處置模式  
 基本模式的實作需要實作 `System.IDisposable` 介面，以及將宣告 `Dispose(bool)` 方法實作之間共用的所有資源清除邏輯 `Dispose` 方法，並選擇性完成項。  
  
 下列範例示範基本模式的簡單實作︰  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 布林值參數 `disposing` 指出方法是否已從叫用 `IDisposable.Dispose` 實作或從完成項。`Dispose(bool)` 實作應該檢查參數，才能存取其他參考物件 （例如，在上述範例中的資源欄位）。 呼叫此方法時，應該只能存取這類物件 `IDisposable.Dispose` 實作 \(當 `disposing` 參數等於 true\)。 如果方法叫用完成項完成 \(`disposing` 為 false\)，不應存取其他物件。 原因是物件的完成中無法預期的順序，因此它們，或任何相依性，可能有已完成。  
  
 此外，本節適用於具有未實作 Dispose 模式的基底類別。 如果您繼承自類別已經實作模式，只是覆寫 `Dispose(bool)` 方法，以提供額外的資源清除邏輯。  
  
 **✓ 執行** 宣告受保護的虛擬 void `Dispose(bool disposing)` 方法來集中處理所有的邏輯相關釋放 unmanaged 的資源。  
  
 在這個方法中發生的所有資源清除。 從完成項呼叫方法和 `IDisposable.Dispose` 方法。 參數會是 false，如果從完成項內叫用的。 它應該用來確保任何最終處理期間執行的程式碼不會存取其他可最終處理物件。 下一節中詳述的實作完成項的詳細資料。  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ 執行** 實作 `IDisposable` 介面只呼叫 `Dispose(true)` 後面 `GC.SuppressFinalize(this)`。  
  
 若要呼叫 `SuppressFinalize` 才應該發生 `Dispose(true)` 順利執行。  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X 不** 進行無參數 `Dispose` 虛擬方法。  
  
 `Dispose(bool)` 方法就是應該加以覆寫子類別。  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 **X 不** 宣告的任何多載 `Dispose` 以外的方法 `Dispose()` 和 `Dispose(bool)`。  
  
 `Dispose` 應該被視為協助編寫這種模式，並防止困惑實作者、 使用者和編譯器是保留的字。 有些語言可能會選擇自動實作此模式於特定類型。  
  
 **✓ 執行** 允許 `Dispose(bool)` 方法來呼叫一次以上。 此方法可能會選擇第一次呼叫之後需要執行任何動作。  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X 避免** 擲回例外狀況從 `Dispose(bool)` 重大其中包含的處理序已損毀的情況下除外 （遺漏、 不一致的共用的狀態等。）。  
  
 使用者期望呼叫 `Dispose` 將不會引發例外狀況。  
  
 如果 `Dispose` 可能會引發例外狀況，將不會執行進一步的 finally 區塊清除邏輯。 若要解決這個問題，使用者必須將每次呼叫 `Dispose` \(在 finally 區塊 ！\) 在 try 區塊中，進而導致非常複雜的清除處理常式。 如果執行 `Dispose(bool disposing)` 方法中，永遠不會擲回的例外狀況，如果處置為 false。 如果完成項內容中執行，如此一來會終止處理序。  
  
 **✓ 執行** 擲回 <xref:System.ObjectDisposedException> 從已經過處置物件之後無法使用的任何成員。  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ 考慮** 提供的方法， `Close()`, ，除了 `Dispose()`, ，是否關閉區域中的標準術語。  
  
 這麼做，它時，請務必 `Close` 實作相同 `Dispose` ，請考慮實作 `IDisposable.Dispose` 方法明確。  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## 可進行最終處理的型別  
 可進行最終處理的型別擴充基本的處置模式，透過覆寫完成項，並提供完成項中的程式碼路徑是 `Dispose(bool)` 方法。  
  
 主要是因為您無法在執行期間進行特定系統的狀態 （通常是有效的） 的假設，很難正確地實作完成項。 下列指導方針應納入，請仔細考慮。  
  
 請注意，有些指導方針適不只是個 `Finalize` 方法，但任何程式碼呼叫來自完成項。 如果基本處置先前所定義的模式，這一點表示的內部執行的邏輯 `Dispose(bool disposing)` 時 `disposing` 參數為 false。  
  
 如果基底類別已經變成可最終處理，而且會實作基本的處置模式，您不應覆寫 `Finalize` 一次。 您應該改為只覆寫 `Dispose(bool)` 方法，以提供額外的資源清除邏輯。  
  
 下列程式碼示範可最終處理的型別︰  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X 避免** 進行最終處理的型別。  
  
 請仔細考慮任何案例中您將需要完成項。 沒有實際從效能和程式碼的複雜度觀點來完成設定式的執行個體相關聯的成本。 偏好使用資源的包裝函式，例如 <xref:System.Runtime.InteropServices.SafeHandle> 封裝 unmanaged 的資源，可能的話，在此情況下完成項會變成不需要因為包裝函式是負責自己的資源清除作業。  
  
 **X 不** 進行最終處理實值型別。  
  
 只有參考型別實際上取得最終處理而由 CLR，因此若嘗試將實值型別完成項將會被忽略。 C\# 和 c \+ \+ 編譯器強制執行此規則。  
  
 **✓ 執行** 進行型別變成可最終處理，如果類型是負責釋放 unmanaged 的資源並沒有自己的完成項。  
  
 在實作完成項，只要呼叫 `Dispose(false)` ，並將內的所有資源清除邏輯 `Dispose(bool disposing)` 方法。  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 **✓ 執行** 在每個可進行最終處理的型別上實作基本的處置模式。  
  
 這可讓使用者類型的明確執行完成項是負責這些相同資源的決定性的清除方法。  
  
 **X 不** 存取任何最終處理物件完成項程式碼路徑，因為，它們將已完成的重大風險之中。  
  
 例如，具有參考另一個可進行最終處理物件 B 變成可最終處理物件的不能可靠地使用 B 中 A 的完成項，反之亦然。 以隨機順序 （缺乏關鍵結束的弱式排序保證） 呼叫的完成項。  
  
 此外，請注意，以靜態變數儲存的物件將會收集在特定時間點期間的應用程式定義域卸載或結束處理程序。 存取是指可最終處理物件 （或呼叫靜態方法，可能會使用靜態變數中儲存的值） 的靜態變數可能不安全的 if <xref:System.Environment.HasShutdownStarted%2A?displayProperty=fullName> 傳回 true。  
  
 **✓ 執行** 讓您 `Finalize` 受保護的方法。  
  
 C\#、 c \+ \+ 和 VB.NET 開發人員不需要擔心，因為編譯器可以協助強制執行這項指導方針。  
  
 **X 不** 讓例外狀況逸出和完成項邏輯，除了嚴重系統失敗。  
  
 如果來自完成項擲回例外狀況，CLR 就會關閉整個處理序 （如.NET Framework 2.0 版\)，防止其他完成項執行並被釋放的控管的資源。  
  
 **✓ 考慮** 建立和使用重要的可最終處理物件 \(具有型別階層架構，其中包含的型別 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>\) 的情況下，在其中完成項必須甚至時一定得執行強制應用程式定義域卸載，執行緒中止。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [常見的設計模式](../../../docs/standard/design-guidelines/common-design-patterns.md)   
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)