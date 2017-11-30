---
title: "使用執行緒和執行緒處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80eb4c3bb98acdd1f83dbf5bcf57b2f7b295742b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-threads-and-threading"></a>使用執行緒和執行緒處理
本節中的主題討論的建立和管理的 managed 的執行緒、 如何將資料傳遞至 managed 執行緒，並取得結果，以及如何終結執行緒和處理<xref:System.Threading.ThreadAbortException>。  
  
## <a name="in-this-section"></a>本章節內容  
 [建立執行緒並在啟動時間傳遞資料](../../../docs/standard/threading/creating-threads-and-passing-data-at-start-time.md)  
 討論並示範如何建立 managed 執行緒，包括如何將資料傳遞給新執行緒，以及如何取得資料。  
  
 [暫止和繼續執行緒](../../../docs/standard/threading/pausing-and-resuming-threads.md)  
 討論暫停和繼續 managed 的執行緒的後果。  
  
 [終結執行緒](../../../docs/standard/threading/destroying-threads.md)  
 討論的終結 managed 的執行緒，以及如何處理後果<xref:System.Threading.ThreadAbortException>。  
  
 [排程執行緒](../../../docs/standard/threading/scheduling-threads.md)  
 討論執行緒的優先順序，以及它們如何影響執行緒排程。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Threading.Thread>  
 提供參考文件<xref:System.Threading.Thread>類別，其代表 managed 的執行緒，還是來自 unmanaged 程式碼中的受管理的應用程式所建立。  
  
 <xref:System.Threading.ThreadStart>  
 提供參考文件<xref:System.Threading.ThreadStart>委派，表示無參數的執行緒程序。  
  
 <xref:System.Threading.ParameterizedThreadStart>  
 提供簡單的方法，將資料傳遞給執行緒的程序，雖然沒有強型別。  
  
## <a name="related-sections"></a>相關章節  
 [執行緒和執行緒處理](../../../docs/standard/threading/threads-and-threading.md)  
 提供 managed 執行緒的簡介。
