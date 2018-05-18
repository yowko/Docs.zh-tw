---
title: 建立執行緒並在啟動時間傳遞資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96c0c898f103c058c370a0d108568056b1ff8196
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>建立執行緒並在啟動時間傳遞資料
建立作業系統處理序時，作業系統會插入執行緒以在該處理序中執行程式碼，包括任何原始的應用程式定義域。 從那時起，不一定要建立或終結任何作業系統執行緒，就能建立和終結應用程式定義域。 如果正在執行的程式碼為受控碼，則可藉由擷取類型 <xref:System.Threading.Thread> 的靜態 <xref:System.Threading.Thread.CurrentThread%2A> 屬性，來取得正在目前應用程式定義域中執行之執行緒的 <xref:System.Threading.Thread> 物件。 本主題說明執行緒的建立，並討論將資料傳遞至執行緒程序的替代方案。  
  
## <a name="creating-a-thread"></a>建立執行緒  
 建立新的 <xref:System.Threading.Thread> 物件，會建立新的受控執行緒。 <xref:System.Threading.Thread> 類別具有採用 <xref:System.Threading.ThreadStart> 委派或 <xref:System.Threading.ParameterizedThreadStart> 委派的建構函式；委派會包裝當您呼叫 <xref:System.Threading.Thread.Start%2A> 方法時新執行緒所叫用的方法。 呼叫 <xref:System.Threading.Thread.Start%2A> 超過一次，就會擲回 <xref:System.Threading.ThreadStateException>。  
  
 <xref:System.Threading.Thread.Start%2A> 方法會立即傳回，通常會在實際啟動新的執行緒之前。 您隨時都可使用 <xref:System.Threading.Thread.ThreadState%2A> 和 <xref:System.Threading.Thread.IsAlive%2A> 屬性來判斷執行緒的狀態，但不應使用這些屬性來進行執行緒活動的同步處理。  
  
> [!NOTE]
>  一旦啟動執行緒之後，就不需要保留對 <xref:System.Threading.Thread> 物件的參考。 執行緒會繼續執行，直到執行緒程序結束為止。  
  
 下列程式碼範例會建立兩個新的執行緒，來呼叫另一個物件上的執行個體和靜態方法。  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a>將資料傳遞給執行緒以及從執行緒擷取資料  
 在 .NET Framework 2.0 版中，<xref:System.Threading.ParameterizedThreadStart> 委派提供了一個簡易的方式，在您呼叫 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> 方法多載時，將包含資料的物件傳遞至執行緒。 請參閱 <xref:System.Threading.ParameterizedThreadStart>，以取得程式碼範例。  
  
 使用 <xref:System.Threading.ParameterizedThreadStart> 委派並非傳遞資料的類型安全方式，因為 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> 方法多載接受任何物件。 替代方法是在協助程式類別中封裝執行緒程序和資料，並使用 <xref:System.Threading.ThreadStart> 委派來執行執行緒程序。 接下來的兩個程式碼範例將示範這項技術。  
  
 這兩個委派都沒有傳回值，因為沒有地方可從非同步呼叫傳回資料。 若要擷取執行緒方法的結果，您可以使用回呼方法，如第二個程式碼範例所示。  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a>使用回呼方法擷取資料  
 下列範例示範從執行緒擷取資料的回呼方法。 包含資料和執行緒方法之類別的建構函式也會接受代表回呼方法的委派；在執行緒方法結束之前，它會叫用回呼委派。  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [使用執行緒和執行緒處理](../../../docs/standard/threading/using-threads-and-threading.md)
