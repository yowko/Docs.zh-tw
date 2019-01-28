---
title: 決定何時實作事件架構非同步模式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
ms.openlocfilehash: acc732f72e9dae0796da78cdbb8ef4666ae9791a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574426"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>決定何時實作事件架構非同步模式
事件架構非同步模式提供的模式可公開類別的非同步行為。 引進此模式之後，[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 定義兩種模式來公開非同步行為：以 <xref:System.IAsyncResult?displayProperty=nameWithType> 介面為基礎的非同步模式與事件架構模式。 本主題說明適合實作這兩種模式的時機。  
  
 如需使用 <xref:System.IAsyncResult> 介面進行非同步程式設計的詳細資訊，請參閱[非同步程式設計模型 (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md)。  
  
## <a name="general-principles"></a>一般準則  
 一般而言，您應該儘可能使用事件架構非同步模式來公開非同步功能。 不過，事件架構模式無法符合一些需求。 在那些情況下，除了事件架構模式之外，您可能還必須實作 <xref:System.IAsyncResult> 模式。  
  
> [!NOTE]
>  實作 <xref:System.IAsyncResult> 模式但未一併實作事件架構模式的情況非常罕見。  
  
## <a name="guidelines"></a>方針  
 下列清單說明實作事件架構非同步模式時的指導方針：  
  
-   使用事件架構模式作為預設 API 來公開類別的非同步行為。  
  
-   當您的類別主要用於用戶端應用程式 (例如 Windows Forms) 時，請不要公開 <xref:System.IAsyncResult> 模式。  
  
-   只有在為符合您的需求時，才公開 <xref:System.IAsyncResult> 模式。 例如，與現有 API 的相容性可能需要您公開 <xref:System.IAsyncResult> 模式。  
  
-   沒有一併公開事件架構模式時，請不要公開 <xref:System.IAsyncResult> 模式。  
  
-   如果您必須公開 <xref:System.IAsyncResult> 模式，請以進階選項的方式執行此動作。 例如，如果您透過產生 <xref:System.IAsyncResult> 模式的選項來產生 Proxy 物件，預設會產生事件架構模式。  
  
-   請在您的 <xref:System.IAsyncResult> 模式實作上建置事件架構模式實作。  
  
-   避免在相同類別上公開這兩個事件架構模式和 <xref:System.IAsyncResult> 模式。 在「較高層級的」類別上公開事件架構模式，並在「較低層級的」類別上公開 <xref:System.IAsyncResult> 模式。 例如，比較 <xref:System.Net.WebClient> 元件上的事件架構模式與 <xref:System.Web.HttpRequest> 類別上的 <xref:System.IAsyncResult> 模式。  
  
    -   當基於相容性需要時，請在相同類別上公開事件架構模式與 <xref:System.IAsyncResult> 模式。 例如，如果您已發行使用 <xref:System.IAsyncResult> 模式的 API，則需要保留 <xref:System.IAsyncResult> 模式以提供回溯相容性。  
  
    -   如果產生的物件模型複雜度超過個別實作的優點，請在相同類別上公開事件架構模式與 <xref:System.IAsyncResult> 模式。 最好在單一類別上公開這兩個模式，而不是避免公開事件架構模式。  
  
    -   如果您必須在單一類別上公開事件架構模式和 <xref:System.IAsyncResult> 模式，請以進階選項的方式，使用設為 <xref:System.ComponentModel.EditorBrowsableState.Advanced> 的 <xref:System.ComponentModel.EditorBrowsableAttribute> 來標示 <xref:System.IAsyncResult> 模式實作。 這會向 Visual Studio IntelliSense 這類設計環境表示，不要顯示 <xref:System.IAsyncResult> 屬性和方法。 這些屬性和方法仍完全可供使用，但透過 IntelliSense 處理的開發人員會有較清楚的 API 檢視。  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>除了公開事件架構模式之外還公開 IAsyncResult 模式的準則  
 雖然在先前所述的案例下，事件架構非同步模式有許多優點，但也有一些缺點，如果您最以效能為重，應多加注意。  
  
 有三種案例，事件架構模式與 <xref:System.IAsyncResult> 模式都不會處理：  
  
-   封鎖等候一個 <xref:System.IAsyncResult>  
  
-   封鎖等候多個 <xref:System.IAsyncResult> 物件  
  
-   輪詢 <xref:System.IAsyncResult> 是否完成  
  
 您可以使用事件架構模式來處理這些案例，但這樣做會比使用 <xref:System.IAsyncResult> 模式更麻煩。  
  
 開發人員經常針對有極高效能需求的服務使用 <xref:System.IAsyncResult> 模式。 例如，輪詢完成案例就是高效能伺服器技巧。  
  
 此外，因為事件架構模式會建立較多物件 (特別是 <xref:System.EventArgs>) 且會跨執行緒進行同步處理，所以效率會比 <xref:System.IAsyncResult> 差。  
  
 如果您決定使用 <xref:System.IAsyncResult> 模式，下列清單顯示一些可遵循的建議：  
  
-   只有在您具體需要支援 <xref:System.Threading.WaitHandle> 或 <xref:System.IAsyncResult> 物件時，才公開 <xref:System.IAsyncResult> 模式。  
  
-   只有在您現有的 API 使用 <xref:System.IAsyncResult> 模式時，才公開 <xref:System.IAsyncResult> 模式。  
  
-   如果您的現有 API 以 <xref:System.IAsyncResult> 模式為基礎，也請考慮在下一版公開事件架構模式。  
  
-   只有在您有高效能需求，且已驗證事件架構模式無法符合該需求，但 <xref:System.IAsyncResult> 模式能符合時，才公開 <xref:System.IAsyncResult> 模式。  
  
## <a name="see-also"></a>另請參閱

- [如何：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)
- [實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
