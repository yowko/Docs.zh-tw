---
title: 使用執行緒和執行緒處理
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725a47cae6e3e91cf9e7385427bceece81f3c918
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="using-threads-and-threading"></a>使用執行緒和執行緒處理
本節中的主題將討論受控執行緒的建立和管理、如何將資料傳遞至受控執行緒並取得結果，以及如何終結執行緒和處理 <xref:System.Threading.ThreadAbortException>。  
  
## <a name="in-this-section"></a>本節內容  
 [建立執行緒並在啟動時間傳遞資料](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 討論並示範受控執行緒的建立，包括如何將資料傳遞給至新的執行緒，以及如何取得資料。  
  
 [暫止和繼續執行緒](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 討論暫停和繼續受控執行緒的後果。  
  
 [終結執行緒](../../../docs/standard/threading/destroying-threads.md)  
 討論終結受控執行緒的後果，以及如何處理 <xref:System.Threading.ThreadAbortException>。  
  
 [排程執行緒](../../../docs/standard/threading/scheduling-threads.md)  
 討論執行緒的優先順序，以及它們如何影響執行緒排程。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Threading.Thread>  
 提供 <xref:System.Threading.Thread> 類別的參考文件，不論這個類別來自非受控碼或在受控應用程式中所建立，都代表受控執行緒。  
  
 <xref:System.Threading.ThreadStart>  
 提供 <xref:System.Threading.ThreadStart> 委派的參考文件，這個委派代表無參數的執行緒程序。  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 儘管沒有強式類型，還是會提供一個簡單的方法來將資料傳遞給執行緒程序。  
  
## <a name="related-sections"></a>相關章節  
 [執行緒和執行緒處理](../../../docs/standard/threading/threads-and-threading.md)  
 提供受控執行緒的簡介。
