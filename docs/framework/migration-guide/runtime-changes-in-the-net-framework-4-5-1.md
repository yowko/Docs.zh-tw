---
title: ".NET Framework 4.5.1 中的執行階段變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式相容性"
  - "執行階段變更"
  - ".NET Framework 4.5.1"
ms.assetid: da880ad7-ba0a-4368-b340-705e3533c351
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# .NET Framework 4.5.1 中的執行階段變更
在某些罕見的情況下，執行階段變更可能會影響以 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 或 4.5 為目標但在 4.51 執行階段上執行的現有應用程式， 其中包含下列區域的變更：  
  
-   [核心](#Core)  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
 下表中的 [範圍] 一欄指定每項變更的重要性：  
  
-   主要。 影響大量應用程式或需要大幅修改程式碼的重大變更。 請注意，執行階段變更不屬於此分類。  
  
-   次要。 影響少量應用程式或需要稍微修改程式碼的變更。  
  
-   邊緣。 在非常特定 (罕見) 的情況下影響應用程式的變更。  
  
-   透明。 此變更對應用程式的開發人員或使用者的影響不明顯。 發生此變更的應用程式應該不需要修改。  
  
<a name="Core"></a>   
## <a name="core-runtime-changes"></a>核心執行階段變更  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>序列化</TKey, TValue>|A <xref:System.Collections.Concurrent.ConcurrentDictionary%602>與.NET Framework 4.5 中序列化物件<xref:System.Runtime.Serialization.NetDataContractSerializer>無法還原序列化，.NET Framework 4.5.1 和 4.5.2 中只是因為內部型別中的變更。\</TKey, TValue><br /><br /> 這項變更未*不*適用於下列案例︰<br /><br /> A <xref:System.Collections.Concurrent.ConcurrentDictionary%602>序列化.NET Framework 4.5 中的物件，並且在還原序列化[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]。</TKey, TValue> <xref:System.Runtime.Serialization.NetDataContractSerializer>中[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]能夠還原序列化物件。<br /><br /> A <xref:System.Collections.Concurrent.ConcurrentDictionary%602>較新版的.NET Framework 中序列化的物件，並且在.NET Framework 4.5 中還原序列化。\</TKey, TValue> <xref:System.Runtime.Serialization.NetDataContractSerializer> .NET Framework 4.5 中可還原序列化物件。<br /><br /> 版本間序列化和還原序列化<xref:System.Collections.Concurrent.ConcurrentDictionary%602>物件之間任何版本的.NET Framework 在.NET Framework 4.5 之後。</TKey, TValue> 這項變更會套用至物件序列化為.NET Framework 4.5*只*。|兩種解決方法都有必要序列化<xref:System.Collections.Concurrent.ConcurrentDictionary%602>物件的.NET Framework 4.5 和更新版本的.NET framework 上將它還原序列化︰\</TKey, TValue><br /><br /> 使用替代的序列化程式，例如<xref:System.Runtime.Serialization.DataContractSerializer>或<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>。<br /><br /> 升級至[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]，可支援的還原序列化<xref:System.Collections.Concurrent.ConcurrentDictionary%602>物件序列化為.NET Framework 4.5。\</TKey, TValue>|次要|  
|<xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName>類別|<xref:System.Diagnostics.Tracing.EventListener>會截斷內嵌 null 的字串。 不支援 null 字元<xref:System.Diagnostics.Tracing.EventSource>類別。|變更只會影響使用的應用程式<xref:System.Diagnostics.Tracing.EventListener>讀取<xref:System.Diagnostics.Tracing.EventSource>程序中的資料並使用 null 字元做為分隔符號。|邊緣|  
|<xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>類別|執行階段現在會強制執行指定下列的合約︰ 一個類別衍生自<xref:System.Diagnostics.Tracing.EventSource>定義 ETW 事件方法必須呼叫基底類別<xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=fullName>方法與事件識別碼後面接著傳遞 ETW 事件方法相同的引數。|<xref:System.IndexOutOfRangeException>會擲回例外狀況<xref:System.Diagnostics.Tracing.EventListener>讀取<xref:System.Diagnostics.Tracing.EventSource>違反本合約之事件來源的程序中的資料。<br /><br /> 請參閱[緩和︰ EventSource.WriteEvent 方法呼叫](../../../docs/framework/migration-guide/mitigation-eventsource-writeevent-method-calls.md)|次要|  
|還原序列化跨應用程式網域的物件|在某些情況下，當應用程式使用具有不同應用程式基底的兩個或多個應用程式網域時，嘗試在邏輯呼叫內容中還原序列化跨應用程式網域的物件會擲回例外狀況。|只有在非常特定的情況下才會引發此問題。 如需詳細資訊和緩和措施，請參閱[緩和︰ 還原序列化的物件應用程式定義域之間](../../../docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md)。|邊緣|  
|<xref:System.IO.Stream.Dispose%2A?displayProperty=fullName>方法|在[!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)]應用程式，[!INCLUDE[wrt](../../../includes/wrt-md.md)]資料流配接器不會再呼叫<xref:System.IO.Stream.FlushAsync%2A>方法從<xref:System.IO.Stream.Dispose%2A>方法。|這項變更應該是透明的。 開發人員可以撰寫下列程式碼來還原舊有行為：<br /><br /> `using (System.IO.Stream stream = GetWindowsRuntimeStream() As Stream)  {     // do something     await stream.FlushAsync();   }`|透明|  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf-runtime-changes"></a>Windows Communication Foundation (WCF) 執行階段變更  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|[minFreeMemoryPercentageToActiveService](http://msdn.microsoft.com/library/ms731336.aspx)組態設定|此設定建立伺服器上必須提供才能啟動 WCF 服務的最小記憶體。 它為了防止<xref:System.OutOfMemoryException>例外狀況。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，此設定不會造成影響。 在 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 中，會遵守此設定。|如果 Ｗeb 伺服器上可用的記憶體小於此組態設定所定義的百分比，則會發生例外狀況。 某些成功啟動並在有限記憶體環境下執行的 WCF 服務現在可能會失敗。<br /><br /> 請參閱[緩和︰ minFreeMemoryPercentageToActiveService 組態設定](../../../docs/framework/migration-guide/mitigation-minfreememorypercentagetoactiveservice-configuration-setting.md)。|次要|  
  
## <a name="see-also"></a>另請參閱  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-1.md)   
 [4.5 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.5.2 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)