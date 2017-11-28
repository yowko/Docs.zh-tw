---
title: "使用 Serviced 元件和全域組件快取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45fd02c4f87d33766741e6fd023f9b40b9964d63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>使用 Serviced 元件和全域組件快取
Serviced 元件 (Managed 程式碼 COM+ 元件) 都應該放在全域組件快取中。 在某些情況下，通用語言執行平台和 COM + 服務可以處理不在全域組件快取中的 Serviced 元件；但在其他案例中則不能。 下列案例可說明這種情況：  
  
-   若是 COM+ 伺服器應用程式中的 Serviced 元件，由於 Dllhost.exe 的執行位置不在包含 Serviced 元件的相同目錄中，因此含有元件的組件必須位於全域組件快取中。  
  
-   若是 COM+ 程式庫應用程式中的 Serviced 元件，執行階段和 COM+ 服務可以搜尋目前的目錄，以解析含有元件的組件參考。 在這種情況下，組件就不需要位於全域組件快取中。  
  
-   若是 ASP.NET 應用程式中的 Serviced 元件，情況又不同。 如果您將包含 Serviced 元件的組件放置在應用程式基底的 bin 目錄中，並使用隨選的註冊，則系統會將組件陰影複製到下載快取，因為 ASP.NET 會使用執行階段的陰影功能。  
  
## <a name="see-also"></a>另請參閱  
 [使用組件和全域組件快取](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (全域組件快取工具)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
