---
title: "Managed and Unmanaged Threading in Windows | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "threading [.NET Framework], unmanaged"
  - "threading [.NET Framework], managed"
  - "managed threading"
ms.assetid: 4fb6452f-c071-420d-9e71-da16dee7a1eb
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# Managed and Unmanaged Threading in Windows
所有執行緒的管理都會透過 <xref:System.Threading.Thread> 類別進行，包括 Common Language Runtime 建立的執行緒，以及在執行階段外部建立但進入 Managed 環境執行程式碼的執行緒。 執行階段會監視在其處理序中所有曾在 Managed 執行環境中執行程式碼的執行緒， 但不會追蹤其他任何執行緒。 執行緒可透過 COM Interop \(因為執行階段會將 Managed 物件當做 COM 物件公開給 Unmanaged 世界\)、COM [DllGetClassObject](https://msdn.microsoft.com/en-us/library/ms680760.aspx) 函式和平台叫用來進入 Managed 執行環境。  
  
 當 Unmanaged 執行緒透過類似 COM 可呼叫包裝函式來進入執行階段時，系統會檢查此執行緒的執行緒本機存放區，以尋找內部 Managed <xref:System.Threading.Thread> 物件。 如果找到一個物件，表示執行階段已感知此執行緒。 但是，如果找不到任何 <xref:System.Threading.Thread> 物件，執行階段會建置新物件並安裝到此執行緒的執行緒本機存放區中。  
  
 在 Managed 執行緒中，<xref:System.Threading.Thread.GetHashCode%2A?displayProperty=fullName> 是穩定的 Managed 執行緒識別。 在執行緒的存留期間，此值不會與其他任何執行緒的值相衝突，不論您是從哪一個應用程式定義域取得此值。  
  
> [!NOTE]
>  作業系統的 **ThreadId** 與 Managed 執行緒之間沒有固定的關係，因為未受管理的主機可控制 Managed 執行緒與 Unmanaged 執行緒之間的關係。 具體來說，精密的主機可使用 Fiber 應用程式開發介面，對同一個作業系統執行緒排程許多 Managed 執行緒，或是在不同的作業系統執行緒之間移動 Managed 執行緒。  
  
## 從 Win32 執行緒對應至 Managed 執行緒  
 下表將 Win32 執行緒項目對應至其近似的執行階段對等項目。 請注意，此對應並不代表功能完全一樣。 例如，**TerminateThread** 不會執行 **finally** 子句或釋放資源，並且無法防止。 但是，<xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 會執行所有復原程式碼、回收所有資源，並且可使用 <xref:System.Threading.Thread.ResetAbort%2A> 加以拒絕。 在揣測功能之前，請務必仔細閱讀相關文件。  
  
|在 Win32 中|在 Common Language Runtime 中|  
|---------------|---------------------------------|  
|**CreateThread**|**Thread** 和 <xref:System.Threading.ThreadStart> 的組合|  
|**TerminateThread**|<xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>|  
|**SuspendThread**|<xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|  
|**ResumeThread**|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName>|  
|**Sleep**|<xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>|  
|執行緒控制代碼上的 **WaitForSingleObject**|<xref:System.Threading.Thread.Join%2A?displayProperty=fullName>|  
|**ExitThread**|沒有對等項目|  
|**GetCurrentThread**|<xref:System.Threading.Thread.CurrentThread%2A?displayProperty=fullName>|  
|**SetThreadPriority**|<xref:System.Threading.Thread.Priority%2A?displayProperty=fullName>|  
|沒有對等項目|<xref:System.Threading.Thread.Name%2A?displayProperty=fullName>|  
|沒有對等項目|<xref:System.Threading.Thread.IsBackground%2A?displayProperty=fullName>|  
|近似 **CoInitializeEx** \(OLE32.DLL\)|<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=fullName>|  
  
## Managed 執行緒和 COM Apartment  
 可標記 Managed 執行緒，以表示它將裝載[單一執行緒](http://msdn.microsoft.com/library/windows/desktop/ms680112.aspx)或[多執行緒](http://msdn.microsoft.com/library/windows/desktop/ms693421.aspx) Apartment。 \(如需 COM 執行緒架構的詳細資訊，請參閱[處理序、執行緒和 Apartment](http://msdn.microsoft.com/library/windows/desktop/ms693344.aspx)。\)<xref:System.Threading.Thread.GetApartmentState%2A> 類別的 <xref:System.Threading.Thread.SetApartmentState%2A>、<xref:System.Threading.Thread.TrySetApartmentState%2A> 和 <xref:System.Threading.Thread> 方法會傳回並指派執行緒的 Apartment 狀態。 如果尚未設定此狀態，則 <xref:System.Threading.Thread.GetApartmentState%2A> 會傳回 <xref:System.Threading.ApartmentState?displayProperty=fullName>。  
  
 只有在執行緒處於 <xref:System.Threading.ThreadState?displayProperty=fullName> 狀態時，才能設定此屬性；每個執行緒只能設定此屬性一次。  
  
 如果啟動執行緒之前未設定 Apartment 狀態，則會將執行緒初始化為多執行緒 Apartment \(MTA\)。 受到 <xref:System.Threading.ThreadPool> 控制的完成項執行緒及所有執行緒都是 MTA。  
  
> [!IMPORTANT]
>  對於應用程式啟動程式碼而言，控制 Apartment 狀態的唯一方式是將 <xref:System.MTAThreadAttribute> 或 <xref:System.STAThreadAttribute> 套用至進入點程序。 在 .NET Framework 1.0 和 1.1 中，<xref:System.Threading.Thread.ApartmentState%2A> 屬性可設定為程式碼的第一行。 在 .NET Framework 2.0 中則不允許這麼做。  
  
 公開至 COM 之 Managed 物件的行為會像是已彙總無限制執行緒封送處理器。 換句話說，您可以使用無限制執行緒方式從任何 COM Apartment 呼叫 Managed 物件。 只有衍生自 <xref:System.EnterpriseServices.ServicedComponent> 或 <xref:System.Runtime.InteropServices.StandardOleMarshalObject> 的 Managed 物件才不會表現出無限制執行緒行為。  
  
 在 Managed 世界中，除非您使用內容及內容繫結 Managed 執行個體，否則不支援 <xref:System.Runtime.Remoting.Contexts.SynchronizationAttribute>。 如果您正在使用 [Enterprise Services](../Topic/System.EnterpriseServices.md)，則您的物件必須衍生自 <xref:System.EnterpriseServices> \(其本身係衍生自 <xref:System.ContextBoundObject>\)。  
  
 當 Managed 程式碼呼叫 COM 物件時，一律會遵循 COM 規則。 換句話說，程式碼會依照 OLE32 指示，透過 COM Apartment Proxy 和 COM\+ 1.0 內容包裝函式來呼叫。  
  
## 封鎖問題  
 如果執行緒對作業系統發出 Unmanaged 呼叫，而此呼叫在 Unmanaged 程式碼中封鎖了執行緒，則執行階段將不會針對 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 或 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 取得其控制權。 如果是 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName>，執行階段會為 **Abort** 標記執行緒，並在它重新進入 Managed 程式碼時取得其控制權。 建議您使用 Managed 封鎖，而不要使用 Unmanaged 封鎖。<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName>、<xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName>、<xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName>、<xref:System.Threading.Monitor.Enter%2A?displayProperty=fullName>、<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=fullName>、<xref:System.Threading.Thread.Join%2A?displayProperty=fullName>、<xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=fullName> 等對於 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=fullName> 和 <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> 都會有回應。 此外，如果執行緒位在單一執行緒 Apartment 中，則當執行緒被封鎖時，所有這些 Managed 封鎖作業都會正確提取 Apartment 中的訊息。  
  
## 請參閱  
 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=fullName>   
 <xref:System.Threading.ThreadState>   
 <xref:System.EnterpriseServices.ServicedComponent>   
 <xref:System.Threading.Thread>   
 <xref:System.Threading.Monitor>