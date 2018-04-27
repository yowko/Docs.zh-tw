---
title: Dispose 模式
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cb83b943a03eadd760d0080b1c9920e2c1e78cce
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="dispose-pattern"></a>Dispose 模式
所有程式執行期間都取得一或多個系統資源，例如記憶體、 系統處理或資料庫連接。 開發人員需要時請小心使用這類的系統資源，因為它們已取得並使用之後必須釋放它們。  
  
 CLR 會提供自動記憶體管理的支援。 Managed 記憶體 (使用 C# 運算子配置的記憶體`new`) 不需要明確釋放。 它會自動釋放記憶體回收行程 (GC)。 這可以讓開發人員從繁瑣且困難的工作，釋出記憶體，且已前所未有的產能，.NET Framework 所提供的主要原因之一。  
  
 不幸的是，受管理的記憶體只是許多類型的系統資源。 除了受管理的記憶體之外的資源仍必須明確釋放且稱為 unmanaged 資源。 GC 特別設計無法管理這類 unmanaged 的資源，這表示管理 unmanaged 的資源的責任在於開發人員提供的指針。  
  
 CLR 會提供一些幫助釋放 unmanaged 的資源。 <xref:System.Object?displayProperty=nameWithType> 宣告虛擬方法<xref:System.Object.Finalize%2A>（也稱為完成項） 的 gc 之前呼叫物件的記憶體回收 gc 並會覆寫來釋放 unmanaged 的資源。 覆寫完成項的類型被指可最終處理的類型。  
  
 雖然在某些案例中清除有效完成項，但它們是使用兩個很大的缺點：  
  
-   GC 偵測到的物件可供回收時，會呼叫完成項。 這會發生在特定一段時間之後再也不需要有資源。 當開發人員無法或想要發行的資源和資源所完成項當發行的時間之間的延遲可能會在取得許多很少的資源 （可能會輕易地耗盡資源） 的程式或在無法接受資源有成本保持在使用 （例如大量 unmanaged 的記憶體緩衝區） 的情況。  
  
-   當 CLR 需要呼叫完成項時，它必須延後的記憶體物件的集合 （集合之間執行完成項） 記憶體回收的捨入的下一步。 這表示的時間更長的時間將會釋放物件的記憶體 （和其參考的所有物件）。  
  
 因此，完成項上獨佔式信賴憑證者可能不適合在許多情況下，務必盡，回收 unmanaged 的資源，很少資源，在處理時或在高高效能的案例中加入的 GC 額外負荷最終處理的是無法接受。  
  
 架構提供<xref:System.IDisposable?displayProperty=nameWithType>應該要提供開發人員手動的方式來釋放 unmanaged 的資源，因為它們不需要實作的介面。 它也提供<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>可以得知在 GC 的方法物件已手動處置，因此不需要最終處理而失效，在此情況下之前回收物件的記憶體。 型別都會實作`IDisposable`介面指可處置的類型。  
  
 處置的模式是標準化的使用方式和實作完成項和`IDisposable`介面。  
  
 模式的主要動機是減少實作的複雜性<xref:System.Object.Finalize%2A>和<xref:System.IDisposable.Dispose%2A>方法。 複雜度源自的方法有部份但並非所有的程式碼路徑 （在本章稍後描述其差異） 的事實。 此外，還有歷史原因相關的具決定性的資源管理語言支援的進化模式的某些項目。  
  
 **✓ 不要**包含的可處置的類型執行個體的型別上實作基本的處置模式。 請參閱[基本的處置模式](#basic_pattern)如需詳細資訊，在基本模式。  
  
 如果類型是負責其他可處置的物件的存留期，開發人員需要能夠太處置它們。 使用容器的`Dispose`方法是方便進行這項作業。  
  
 **✓ 不要**實作基本的處置模式，並提供完成項型別上保留的資源需要明確地釋放沒有完成項。  
  
 例如，應該在儲存未受管理的記憶體緩衝區的型別上實作這個模式。 [變成可最終處理的型別](#finalizable_types)章節討論與實作完成項相關的指導方針。  
  
 **✓ 考慮**實作基本的處置模式類別本身不保存 unmanaged 資源，或是可處置的物件但可能會有執行的子類型。  
  
 是一個絕佳範例<xref:System.IO.Stream?displayProperty=nameWithType>類別。 雖然它是不保留任何資源的抽象基底類別，它的子類別的大部分作業，並因此，它會實作此模式。  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>基本的處置模式  
 實作模式的基本實作牽涉到`System.IDisposable`介面，以及將宣告`Dispose(bool)`方法，可實作之間共用的所有資源清除邏輯`Dispose`方法，並選擇性的完成項。  
  
 下列範例示範基本模式的簡單實作：  
  
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
  
 布林值參數`disposing`指出方法已從叫用`IDisposable.Dispose`實作或完成項。 `Dispose(bool)`實作應檢查參數，才能存取其他參考的物件 （例如，在上述範例中的資源欄位）。 呼叫此方法時，應該只能存取這類物件`IDisposable.Dispose`實作 (當`disposing`參數等於 true)。 如果方法叫用完成項 (`disposing`為 false)，不應該存取其他物件。 原因是物件的無法預期的順序完成，因此它們，或其任何相依性，可能會有已完成。  
  
 此外，本章節適用於具有未實作 Dispose 模式的基底類別。 如果您繼承自的類別已實作的模式，只是覆寫`Dispose(bool)`方法以提供額外的資源將清除邏輯。  
  
 **✓ 不要**宣告`protected virtual void Dispose(bool disposing)`來釋放 unmanaged 的資源相關的方法來集中管理所有邏輯。  
  
 所有資源清除應都發生在這個方法。 方法呼叫來自完成項和`IDisposable.Dispose`方法。 參數會是如果正在從叫用完成項內則為 false。 它應該用於確保在最終處理期間執行的任何程式碼不會存取其他最終處理物件。 下一節會說明實作完成項的詳細資料。  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ 不要**實作`IDisposable`介面只呼叫`Dispose(true)`後面`GC.SuppressFinalize(this)`。  
  
 若要呼叫`SuppressFinalize`才應該發生`Dispose(true)`順利執行。  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X 不**進行無參數`Dispose`虛擬方法。  
  
 `Dispose(bool)`方法是由子類別應該覆寫。  
  
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
  
 **X 不**宣告的任何多載`Dispose`方法以外`Dispose()`和`Dispose(bool)`。  
  
 `Dispose` 應視為協助編訂此模式並防止混淆實作者、 使用者和編譯器之間的保留的字。 某些語言可能會選擇自動在特定類型上實作此模式。  
  
 **✓ 不要**允許`Dispose(bool)`方法來呼叫一次以上。 此方法可能會選擇不執行任何動作後第一次呼叫。  
  
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
  
 **避免 x**擲回例外狀況從`Dispose(bool)`重大其中包含處理序已損毀的情況下除外 （流失，不一致的共用的狀態等。）。  
  
 使用者可預期的呼叫`Dispose`將不會引發例外狀況。  
  
 如果`Dispose`可能會引發例外狀況，將不會執行進一步的 finally 區塊清除邏輯。 若要解決這個問題，使用者必須換行的每個呼叫`Dispose`(內 finally 區塊 ！) 在 try 區塊中，這會導致非常複雜的清除的處理常式。 如果執行`Dispose(bool disposing)`方法時，永遠不會擲回的例外狀況，如果正在處置為 false。 若一個完成項內容中執行，如此一來會終止處理程序。  
  
 **✓ 不要**擲回<xref:System.ObjectDisposedException>從已經過處置物件後，無法使用的任何成員。  
  
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
  
 **✓ 考慮**提供方法`Close()`，除了`Dispose()`，如果關閉是標準區域中的術語。  
  
 這樣做，它時，請務必`Close`實作相同`Dispose`並考慮實作`IDisposable.Dispose`方法明確。  
  
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
## <a name="finalizable-types"></a>可進行最終處理的類型  
 可進行最終處理的類型都是擴充基本的處置模式，藉由覆寫完成項，並提供結束程式碼路徑中的類型`Dispose(bool)`方法。  
  
 完成項是簡單難以正確地實作，主要是因為您無法在執行期間進行系統的狀態 （通常是有效的） 假設。 下列指導方針應該應該謹慎考量。  
  
 請注意，有些指導方針套用無法只供`Finalize`方法，但任何程式碼呼叫來自完成項。 如果基本處置先前所定義的模式，這一點表示內部執行的邏輯`Dispose(bool disposing)`時`disposing`參數為 false。  
  
 如果基底類別已是可進行最終處理，並實作基本的處置模式，您不應覆寫`Finalize`一次。 您應該改為只覆寫`Dispose(bool)`方法以提供額外的資源將清除邏輯。  
  
 下列程式碼會顯示可完成類型的範例：  
  
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
  
 **請避免 x**進行最終處理的類型。  
  
 請仔細考慮任何案例中您將需要完成項。 沒有實際具有完成項，從效能和程式碼複雜度觀點來看的執行個體相關聯的成本。 偏好使用資源的包裝函式，例如<xref:System.Runtime.InteropServices.SafeHandle>封裝 unmanaged 的資源，可能的話，在此情況下完成項會變成不需要因為包裝函式是負責其自己的資源清除。  
  
 **X 不**進行最終處理實值類型。  
  
 實際上只是參考型別取得完成 clr，並因此將略過任何嘗試完成項置於實值類型。 C# 和 c + + 編譯器強制執行此規則。  
  
 **✓ 不要**讓類型變成可最終處理，如果類型是負責釋放 unmanaged 的資源，但是沒有自己的完成項。  
  
 當實作完成項時，只需呼叫`Dispose(false)`，並將內的所有資源清除邏輯`Dispose(bool disposing)`方法。  
  
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
  
 **✓ 不要**每個可進行最終處理的類型上實作基本的處置模式。  
  
 這可讓使用者類型的方法來明確地執行完成項是負責這些相同資源的具決定性的清除。  
  
 **X 不**存取在完成項程式碼路徑中，任何最終處理物件，因為有極大的風險，它們將已完成。  
  
 例如，參考到另一個可進行最終處理物件 B 變成可最終處理物件 A 無法可靠地使用 B 中 A 的完成項，反之亦然。 完成項 （不重要的最終處理的弱式排序保證） 以隨機順序呼叫。  
  
 此外，請注意，以靜態變數儲存的物件會取得收集特定時間點期間的應用程式定義域卸載或結束程序。 存取是指可最終處理物件 （或呼叫靜態方法，可能會使用靜態變數中儲存的值） 的靜態變數可能不安全的如果<xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType>傳回 true。  
  
 **✓ 不要**請您`Finalize`受保護的方法。  
  
 C#、 c + + 和 VB.NET 開發人員不需要擔心，因為編譯器有助於強制執行這項指導方針。  
  
 **X 不**讓例外狀況逸出與完成項邏輯，除了嚴重系統失敗。  
  
 如果來自完成項擲回例外狀況，CLR 會關閉 (as of.NET Framework 2.0 版)，整個程序防止執行並以節制的方式將被釋放資源的其他完成項。  
  
 **✓ 考慮**建立和使用的重要變成可最終處理物件 (具有型別階層架構，其中包含的型別<xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) 的情況下，在其中完成項絕對必須執行而且即使發生強制應用程式定義域卸載和執行緒中止。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [一般設計模式](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [記憶體回收](../../../docs/standard/garbage-collection/index.md)
