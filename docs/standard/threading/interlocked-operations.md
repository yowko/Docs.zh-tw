---
title: "Interlocked Operations | Microsoft Docs"
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
  - "Interlocked class, about Interlocked class"
  - "threading [.NET Framework], Interlocked class"
ms.assetid: cbda7114-c752-4f3e-ada1-b1e8dd262f2b
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Interlocked Operations
<xref:System.Threading.Interlocked> 類別提供方法讓您可以同步處理對多個執行緒所共用之變數的存取。  如果變數存放在共用記憶體上，則不同處理序的執行緒可使用這個辦法。  Interlocked 作業屬於原子式，也就是說，整個作業是一個單位，相同變數的其他 Interlocked 作業無法將它中斷。  這一點對於具有先佔式多執行緒處理功能的作業系統而言很重要，在這種作業系統中，從記憶體位址載入某個值之後，並在有機會變更及儲存它之前，您可以暫止執行緒。  
  
 <xref:System.Threading.Interlocked> 類別提供了下列作業：  
  
-   在 .NET Framework 2.0 版中，<xref:System.Threading.Interlocked.Add%2A> 方法會將某個整數值加入至變數，並傳回該變數的新值  
  
-   在 .NET Framework 2.0 版中，<xref:System.Threading.Interlocked.Read%2A> 方法會以不可部分完成的作業 \(Atomic Operation\) 之方式來讀取 64 位元整數值，  這在 32 位元的作業系統上很有用，在這種作業系統上，通常不是以不可部分完成的作業之方式來讀取 64 位元整數  
  
-   <xref:System.Threading.Interlocked.Increment%2A> 和 <xref:System.Threading.Interlocked.Decrement%2A> 方法會讓變數遞增或遞減，並傳回結果值  
  
-   <xref:System.Threading.Interlocked.Exchange%2A> 方法會在指定的變數中執行不可部分完成的數值交換，傳回該值並以新的值取代它。  在 .NET Framework 2.0 版中，這個方法的泛型多載可以用來在任何參考型別的變數上執行這項交換。  請參閱 <xref:System.Threading.Interlocked.Exchange%60%601%28%60%600%40%2C%60%600%29>。  
  
-   <xref:System.Threading.Interlocked.CompareExchange%2A> 方法也會交換兩個值，但要視比較結果而定。  在 .NET Framework 2.0 版中，這個方法的泛型多載可以用來在任何參考型別的變數上執行這項交換。  請參閱 <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29>。  
  
 在現代的處理器上，通常可利用單一指令來實作 <xref:System.Threading.Interlocked> 類別的方法。  因此，它們提供非常高效能的同步處理，並且可用來建置高階同步處理辦法，如微調鎖定。  
  
 如需結合使用 <xref:System.Threading.Monitor> 和 <xref:System.Threading.Interlocked> 類別的範例，請參閱[監視器](../Topic/Monitors.md)。  
  
## CompareExchange 範例  
 <xref:System.Threading.Interlocked.CompareExchange%2A> 方法可以用來保護比簡單加減更複雜的計算。  下列範例示範加入至儲存為浮點數之累加值中的安全執行緒 \(Thread\-Safe\) 方法 \(如果是整數，<xref:System.Threading.Interlocked.Add%2A> 方法會是比較簡單的方案\)。如需完整的程式碼範例，請參閱 <xref:System.Threading.Interlocked.CompareExchange%2A> 採用單精確度和雙精度浮點引數的多載 \(<xref:System.Threading.Interlocked.CompareExchange%28System.Single%40%2CSystem.Single%2CSystem.Single%29> 和 <xref:System.Threading.Interlocked.CompareExchange%28System.Double%40%2CSystem.Double%2CSystem.Double%29>\)。  
  
 [!code-cpp[Conceptual.Interlocked#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Interlocked#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source1.cs#1)]
 [!code-vb[Conceptual.Interlocked#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source1.vb#1)]  
  
## Exchange 和 CompareExchange 的不具型別多載  
 <xref:System.Threading.Interlocked.Exchange%2A> 和 <xref:System.Threading.Interlocked.CompareExchange%2A> 方法具有採用 <xref:System.Object> 型別引數的多載。  每個這種多載的第一個引數都是 `ref Object` \(在 Visual Basic 中，是 `ByRef … As Object`\)，而型別安全則要求傳遞給這個引數的變數必須如同 <xref:System.Object> 一般地型別嚴格；呼叫這些方法時，您無法只將第一個引數轉換成型別 <xref:System.Object>。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，請使用 <xref:System.Threading.Interlocked.Exchange%2A> 和 <xref:System.Threading.Interlocked.CompareExchange%2A> 方法的泛型多載來交換強型別變數。  
  
 下列程式碼範例將示範 `ClassA` 型別只能設定一次的屬性，.NET Framework 1.0 或 1.1 版中可能會實作這個屬性。  
  
 [!code-cpp[Conceptual.Interlocked#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interlocked/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Interlocked#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interlocked/cs/source2.cs#2)]
 [!code-vb[Conceptual.Interlocked#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interlocked/vb/source2.vb#2)]  
  
## 請參閱  
 <xref:System.Threading.Interlocked>   
 <xref:System.Threading.Monitor>   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)