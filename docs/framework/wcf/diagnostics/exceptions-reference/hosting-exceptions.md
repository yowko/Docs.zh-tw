---
title: "裝載例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# 裝載例外狀況
這個主題會列出由裝載所產生的所有例外狀況。  
  
## 例外狀況清單  
  
|資源程式碼|資源字串|  
|-----------|----------|  
|Hosting\_AddressIsAbsoluteUri|不允許完整的 URI。完整的 URI 不允許用於 ServiceHostingEnvironment.EnsureServiceAvailable API。請使用對應服務的虛擬路徑。|  
|Hosting\_BuildProviderCouldNotCreateType|在服務編譯期間無法載入指定的 CLR 類型。請確認此類型已在位於應用程式之 \\\\App\_Code 目錄 \(包含在位於應用程式之 \\\\bin 目錄的編譯組件中\) 的來源檔案中定義，或存在於全域組件快取中安裝的組件。類型名稱需區分大小寫。如 \\\\App\_Code 和 \\\\bin 等目錄必須位於應用程式的根目錄中。\\\\App\_Code 和 \\\\bin 目錄不可巢狀包含在子目錄中。|