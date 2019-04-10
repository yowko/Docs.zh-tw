---
title: releaseHandleFailed MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), handles
- release handle failed
- CriticalHandle class, run-time errors
- releaseHandleFailed MDA
- ReleaseHandle method
- SafeHandle class, run-time errors
- MDAs (managed debugging assistants), handles
ms.assetid: 44cd98ba-95e5-40a1-874d-e8e163612c51
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b149a9b8ee41f5e196fd69258044f9b6563cb99
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217870"
---
# <a name="releasehandlefailed-mda"></a>releaseHandleFailed MDA
當衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 或 <xref:System.Runtime.InteropServices.CriticalHandle> 之類別的 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法傳回 `false` 時，會啟動 `releaseHandleFailed` Managed 偵錯助理 (MDA) 來通知開發人員。  
  
## <a name="symptoms"></a>徵兆  
 資源或記憶體流失。  如果衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 或 <xref:System.Runtime.InteropServices.CriticalHandle> 之類別的 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法失敗，則該類別所封裝的資源可能尚未釋出或清除。  
  
## <a name="cause"></a>原因  
 如果使用者建立衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 或 <xref:System.Runtime.InteropServices.CriticalHandle> 的類別，則必須提供 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法的實作；因此，這是個別資源特有的情況。 不過，需求如下：  
  
-   <xref:System.Runtime.InteropServices.SafeHandle> 和<xref:System.Runtime.InteropServices.CriticalHandle>類型代表重要處理序資源周圍的包裝函式。 記憶體遺漏會使處理序過一段時間後即無法使用。  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法執行其函式時，絕不能失敗。 一旦處理序取得這類資源，<xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 是將其釋出的唯一方式。 因此，失敗即代表資源流失。  
  
-   在 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 執行期間，如果發生任何失敗，而導致無法釋出資源，就是 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法本身實作中的 Bug。 即使該程式碼呼叫別人撰寫的程式碼來執行其函式，程式設計師都有責任確保合約的履行。  
  
## <a name="resolution"></a>解決方式  
 如果是程式碼所使用的特定 <xref:System.Runtime.InteropServices.SafeHandle> (或 <xref:System.Runtime.InteropServices.CriticalHandle>) 類型引發了 MDA 通知，則應檢閱程式碼，尋找從 <xref:System.Runtime.InteropServices.SafeHandle> 擷取未經處理的控制代碼值並複製在他處的地方。 這是 <xref:System.Runtime.InteropServices.SafeHandle> 或 <xref:System.Runtime.InteropServices.CriticalHandle> 實作中造成失敗的一般原因，因為執行階段後來就不會再追蹤未經處理之控制代碼值的使用狀況。 如果未經處理的控制代碼複本隨後關閉，可能會導致後來的 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 呼叫失敗，因為是在相同的控制代碼上嘗試關閉，而現在為無效。  
  
 有很多種方式會發生不正確的控制代碼重複：  
  
-   尋找對 <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> 方法的呼叫。 呼叫此方法機會應該非常少，如果您發現了，該呼叫周圍應該會有對 <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> 和 <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> 方法的呼叫。 後面這二個方法會指定可安全使用未經處理之控制代碼值的程式碼區域。 在此區域之外，或是如果參考計數從未在第一時間遞增，則可隨時在另一個執行緒上呼叫 <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> 或 <xref:System.Runtime.InteropServices.SafeHandle.Close%2A>，以使控制代碼值失效。 在追蹤所有使用 <xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A> 的地方後，您應遵循未經處理之控制代碼所採用的路徑，確保不會將它交給最後會呼叫 `CloseHandle` 的某個元件，或是將會釋放控制代碼的其他低階原生方法。  
  
-   確定用來初始化 <xref:System.Runtime.InteropServices.SafeHandle> (具有有效之未經處理的控制代碼值) 的程式碼擁有控制代碼。 如果您在非程式碼擁有的控制代碼周圍構成 <xref:System.Runtime.InteropServices.SafeHandle>，而沒有在基底建構函式中，將 `ownsHandle` 參數設為 `false`，則 <xref:System.Runtime.InteropServices.SafeHandle> 和真正的控制代碼擁有者可以嘗試關閉此控制代碼，如果 <xref:System.Runtime.InteropServices.SafeHandle> 競爭失敗，就會導致 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 發生錯誤。  
  
-   當 <xref:System.Runtime.InteropServices.SafeHandle> 在應用程式定義域之間封送處理時，請確認所使用的 <xref:System.Runtime.InteropServices.SafeHandle> 衍生已標示為可序列化。 衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 的類別極少會被可序列化，若發生此情況下，其應實作 <xref:System.Runtime.Serialization.ISerializable> 介面，或使用其他技術手動控制序列化和還原序列化程序。 這是必要的，因為預設的序列化動作是要建立所含括之未經處理控制代碼值的位元複製，這會導致兩個 <xref:System.Runtime.InteropServices.SafeHandle> 執行個體以為它們擁有相同的控制代碼。 這兩個執行個體都會嘗試在某個時間點，在相同的控制代碼上呼叫 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>。 第二個這麼做的 <xref:System.Runtime.InteropServices.SafeHandle> 將會失敗。 序列化 <xref:System.Runtime.InteropServices.SafeHandle> 時，正確的做法是為您的原生控制代碼類型呼叫 `DuplicateHandle` 函式或類似的函式，以建立不同的合法控制代碼複本。 如果您的控制代碼類型不支援這麼做，則將其含括在內的 <xref:System.Runtime.InteropServices.SafeHandle> 類型無法成為可序列化。  
  
-   若要追蹤哪裡有控制代碼提早關閉，導致最後呼叫 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> 方法時失敗，您可以將偵錯工具中斷點放在要用來釋放控制代碼的原生常式上，例如 `CloseHandle` 函式。 在有壓力的情況下，或甚至是中型功能測試，都不能這麼做，因為這類常式經常要處理極高的流量。 為了擷取呼叫端的身分識別 (或可能是完整的堆疊追蹤)，以及所要釋放之控制代碼的值，檢測用來呼叫原生釋放方法的程式碼可能會有所幫助。  控制代碼值可以和這個 MDA 所報告的值做比較。  
  
-   請注意，某些原生控制代碼類型 (例如可透過 `CloseHandle` 函式釋放的所有 Win32 控制代碼)，會共用相同的控制代碼命名空間。 一個控制代碼類型的錯誤釋放，可能會造成另一個控制代碼類型的問題。 比方說，不小心將 Win32 事件處理常式關閉兩次，可能會導致明顯無關的檔案控制代碼永久關閉。 當已釋放控制代碼，而控制代碼值變成可用來追蹤另一個資源，而該資源可能是另一種類型時，就會發生這種情況。 如果發生這種情況，接著又有錯誤的第二次釋放，不相關之執行緒的控制代碼可能會失效。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  
 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>Output  
 訊息指出 <xref:System.Runtime.InteropServices.SafeHandle> 或 <xref:System.Runtime.InteropServices.CriticalHandle> 無法適當地釋放控制代碼。 例如:   
  
```  
"A SafeHandle or CriticalHandle of type 'MyBrokenSafeHandle'   
failed to properly release the handle with value 0x0000BEEF. This   
usually indicates that the handle was released incorrectly via   
another means (such as extracting the handle using DangerousGetHandle   
and closing it directly or building another SafeHandle around it."  
```  
  
## <a name="configuration"></a>組態  
  
```xml  
<mdaConfig>  
  <assistants>  
    <releaseHandleFailed/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>範例  
 以下是可啟動 `releaseHandleFailed` MDA 的程式碼範例。  
  
```csharp
bool ReleaseHandle()  
{  
    // Calling the Win32 CloseHandle function to release the   
    // native handle wrapped by this SafeHandle. This method returns   
    // false on failure, but should only fail if the input is invalid   
    // (which should not happen here). The method specifically must not   
    // fail simply because of lack of resources or other transient   
    // failures beyond the user’s control. That would make it unacceptable   
    // to call CloseHandle as part of the implementation of this method.  
    return CloseHandle(handle);  
}  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [診斷 Managed 偵錯助理的錯誤](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)
