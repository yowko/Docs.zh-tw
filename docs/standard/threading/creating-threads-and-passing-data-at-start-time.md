---
title: "建立執行緒並在啟動時間傳遞資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>建立執行緒並在啟動時間傳遞資料
建立作業系統處理序時，作業系統會插入該處理程序，包括任何原始的應用程式定義域中執行程式碼的執行緒。 從該點上，應用程式定義域可以建立和終結不一定要建立或終結任何作業系統執行緒。 如果正在執行的程式碼為 managed 程式碼，則<xref:System.Threading.Thread>物件目前的應用程式定義域中的執行緒執行，可取得擷取靜態<xref:System.Threading.Thread.CurrentThread%2A>型別的屬性<xref:System.Threading.Thread>。 本主題說明執行緒的建立，並討論將資料傳遞給執行緒的程序的替代方案。  
  
## <a name="creating-a-thread"></a>建立執行緒  
 建立新<xref:System.Threading.Thread>物件會建立新的 managed 的執行緒。 <xref:System.Threading.Thread>類別具有建構函式採用<xref:System.Threading.ThreadStart>委派或<xref:System.Threading.ParameterizedThreadStart>委派; 委派將包裝的方法，當您呼叫新的執行緒所叫用<xref:System.Threading.Thread.Start%2A>方法。 呼叫<xref:System.Threading.Thread.Start%2A>超過一次會造成<xref:System.Threading.ThreadStateException>擲回。  
  
 <xref:System.Threading.Thread.Start%2A>方法會傳回立即，通常具有實際上會啟動新的執行緒之前。 您可以使用<xref:System.Threading.Thread.ThreadState%2A>和<xref:System.Threading.Thread.IsAlive%2A>屬性來判斷任何時刻，執行緒的狀態，但這些屬性應永遠不會用於同步處理執行緒活動。  
  
> [!NOTE]
>  一旦在執行緒啟動時，不需要保留的參考<xref:System.Threading.Thread>物件。 執行緒會繼續執行，直到執行緒程序的結尾。  
  
 下列程式碼範例會建立兩個新的執行緒來呼叫另一個物件的執行個體和靜態方法。  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a>將資料傳遞給執行緒和執行緒中擷取資料  
 在.NET Framework 2.0 版中，<xref:System.Threading.ParameterizedThreadStart>委派提供了簡易的方式傳遞物件，其中包含資料的執行緒，當您呼叫<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>方法多載。 請參閱 <xref:System.Threading.ParameterizedThreadStart>，以取得程式碼範例。  
  
 使用<xref:System.Threading.ParameterizedThreadStart>委派不以類型安全的方式來傳遞資料，因為<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>方法多載會接受任何物件。 封裝執行緒的程序和協助程式類別中的資料，並使用替代方法是<xref:System.Threading.ThreadStart>委派來執行執行緒的程序。 接下來的兩個程式碼範例會顯示這項技術。  
  
 這兩種情況委派具有傳回值，因為沒有非同步呼叫傳回的資料位置。 若要擷取執行緒方法的結果，您可以使用回呼方法，在第二個程式碼範例所示。  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a>回呼方法以擷取資料  
 下列範例示範從執行緒中擷取資料的回撥方法。 包含資料和執行緒方法的類別的建構函式也接受委派代表的回呼方法。結束執行緒方法之前，它會叫用的回呼委派。  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [執行緒處理](../../../docs/standard/threading/index.md)  
 [使用執行緒和執行緒處理](../../../docs/standard/threading/using-threads-and-threading.md)
