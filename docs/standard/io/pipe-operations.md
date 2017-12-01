---
title: ".NET Framework 中的管道作業"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 879e5a73417f9347224bc22b397814b83972751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="pipe-operations-in-the-net-framework"></a>.NET Framework 中的管道作業
管道提供處理序間通訊的方法。 有兩種類型的管道：  
  
-   匿名管道。  
  
     匿名管道提供在本機電腦上的處理序間通訊。 匿名管道需要較少的額外負荷比具名管道，但提供有限的服務。 匿名管道是單向的不能在網路上。 它們僅支援單一伺服器執行個體。 匿名管道可用於其中管道控制代碼可以輕鬆地傳遞給子處理序所建立的父和子處理序或執行緒之間的通訊。  
  
     .NET Framework 中，在您實作使用匿名管道<xref:System.IO.Pipes.AnonymousPipeServerStream>和<xref:System.IO.Pipes.AnonymousPipeClientStream>類別。  
  
     請參閱[How to： 使用匿名管道進行本機處理序間通訊](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)。  
  
-   具名的管道。  
  
     具名的管道提供一個或多個管道用戶端之間的處理序間通訊。 具名的管道可以是單向或雙工。 它們支援訊息為基礎的通訊，且允許多個用戶端可同時連接到使用相同的管道名稱的伺服器處理序。 具名的管道也支援模擬，讓連接處理序在遠端伺服器上使用他們自己的權限。  
  
     在.NET Framework 中，您必須實作具名的管道使用<xref:System.IO.Pipes.NamedPipeServerStream>和<xref:System.IO.Pipes.NamedPipeClientStream>類別。  
  
     請參閱[How to： 使用具名管道進行網路處理序間通訊](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)。  
  
## <a name="see-also"></a>另請參閱  
 [檔案和資料流 I-O](../../../docs/standard/io/index.md)  
 [操作說明：使用匿名管道進行本機處理序間通訊](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [操作說明：使用具名管道進行網路處理序間通訊](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
