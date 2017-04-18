---
title: "Creating Threads and Passing Data at Start Time | Microsoft Docs"
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
  - "threading [.NET Framework], creating"
  - "threading [.NET Framework], passing data to threads"
  - "threading [.NET Framework], retrieving data from threads"
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Creating Threads and Passing Data at Start Time
當建立作業系統處理序時，作業系統會插入執行緒以在該處理序中執行程式碼，包括任何原始應用程式定義域。  從該處，可建立及終結應用程式定義域，而不一定需要建立及終結任何作業系統執行緒。  如果正在執行的是 Managed 程式碼，則可藉由擷取 <xref:System.Threading.Thread> 型別的靜態 <xref:System.Threading.Thread.CurrentThread%2A> 屬性，獲得現行應用程式定義域中正在執行的執行緒之 <xref:System.Threading.Thread> 物件。  本主題將說明執行緒的建立，並討論將資料傳遞給執行緒程序的替代方案。  
  
## 建立執行緒  
 建立新的 <xref:System.Threading.Thread> 物件時，新的 Managed 執行緒也會隨之建立。  <xref:System.Threading.Thread> 類別具有會採用 <xref:System.Threading.ThreadStart> 委派或 <xref:System.Threading.ParameterizedThreadStart> 委派的建構函式；當您呼叫 <xref:System.Threading.Thread.Start%2A> 方法時，委派會包裝新執行緒所叫用的方法。  多次呼叫 <xref:System.Threading.Thread.Start%2A> 會擲回 <xref:System.Threading.ThreadStateException>。  
  
 通常在新執行緒實際啟動之前，會立即傳回 <xref:System.Threading.Thread.Start%2A> 方法。  您隨時都可以使用 <xref:System.Threading.Thread.ThreadState%2A> 和 <xref:System.Threading.Thread.IsAlive%2A> 屬性來決定執行緒的狀態，但絕不能使用這些屬性來同步處理執行緒的活動。  
  
> [!NOTE]
>  一旦執行緒啟動之後，便不需要保留 <xref:System.Threading.Thread> 物件的參考。  此執行緒會繼續執行，一直到執行緒的程序結束為止。  
  
 下列程式碼範例建立兩個新執行緒，以在另一個物件上呼叫執行個體及靜態方法。  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## 將資料傳遞給執行緒以及擷取來自執行緒的資料  
 在 .NET Framework 2.0 版中，當您呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> 方法多載時，<xref:System.Threading.ParameterizedThreadStart> 委派可讓您輕鬆地將含有資料的物件傳遞給執行緒。  如需程式碼範例，請參閱 <xref:System.Threading.ParameterizedThreadStart>。  
  
 使用 <xref:System.Threading.ParameterizedThreadStart> 委派並不是傳遞資料的型別安全方式，因為 <xref:System.Threading.Thread.Start%2A?displayProperty=fullName> 方法多載會接受任何物件。  替代方案是在 Helper 類別中封裝執行緒程序和資料，並使用 <xref:System.Threading.ThreadStart> 委派來執行執行緒程序。  下列兩個程式碼範例將會示範這項技術。  
  
 這些委派都不具有傳回值，因為沒有地方可供傳回來自非同步呼叫的資料。  若要擷取執行緒方法的結果，可以依照第二個程式碼範例所示，使用回呼 \(Callback\) 方法。  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### 使用回呼方法擷取資料  
 下列範例示範回呼 \(Callback\) 方法，它會從執行緒擷取資料。  類別的建構函式 \(Constructor\) 包含資料和執行緒方法，它也接受代表回呼方法的委派；在執行緒方法結束之前，它會叫用 \(Invoke\) 回呼委派。  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## 請參閱  
 <xref:System.Threading.Thread>   
 <xref:System.Threading.ThreadStart>   
 <xref:System.Threading.ParameterizedThreadStart>   
 <xref:System.Threading.Thread.Start%2A?displayProperty=fullName>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)