---
title: "排程執行緒"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e1fb7d61b8e250884b2c57cad8c5106bc77787a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="scheduling-threads"></a>排程執行緒
每個執行緒有指派給它的執行緒優先順序。 Common language runtime 中建立的執行緒一開始會被指派優先權**ThreadPriority.Normal**。 執行階段外部建立的執行緒會保留它們進入 managed 的環境之前，原本的優先權。 您可以取得或設定與任何執行緒的優先權**Thread.Priority**屬性。  
  
 執行緒都會排定執行會依據其優先順序。 即使在執行階段內執行的執行緒，所有執行緒會由作業系統都指派處理器時間配量。 用來決定執行緒執行的順序的排程演算法的詳細資料會隨著每個作業系統。 在某些作業系統上，具有最高優先權執行緒可以執行） （屬於執行緒一定會排定執行第一次。 如果優先權相同的多個執行緒都可供，排程器不斷循環的執行緒的優先權，讓每個執行緒執行所在的固定的時間配量。 為具有較高優先順序的執行緒可執行，則不會執行較低優先權的執行緒。 當有沒有其他可執行的執行緒在指定的優先順序時，排程器將移到下一個較低的優先順序，並排程上執行的該優先順序的執行緒。 如果高優先順序的執行緒成為可執行，會佔用較低優先順序的執行緒，高優先順序的執行緒，允許一次重新執行。 在頂端，作業系統也可以調整執行緒的優先順序動態前景與背景之間移動應用程式的使用者介面。 其他作業系統可能會選擇使用不同的排程演算法。  
  
## <a name="see-also"></a>另請參閱  
 [使用執行緒和執行緒處理](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Windows 中的 Managed 和 Unmanaged 執行緒處理](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
