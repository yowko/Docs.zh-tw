---
title: "裝載例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b296578efb6eb9b1e6372dbad647fdea22dbaddf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-exceptions"></a>裝載例外狀況
這個主題會列出由裝載所產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|不允許完整的 URI。 完整的 URI 不允許用於 ServiceHostingEnvironment.EnsureServiceAvailable API。 請使用對應服務的虛擬路徑。|  
|Hosting_BuildProviderCouldNotCreateType|在服務編譯期間無法載入指定的 CLR 類型。 請確認此類型可以是位於應用程式的原始程式檔中已定義\\\App_Code 目錄中，應用程式中找到編譯的組件中包含\\\bin 目錄，或出現在中安裝的組件全域組件快取。 類型名稱需區分大小寫。 例如，目錄\\\App_Code 和\\\bin 必須位於應用程式的根目錄。 \\\App_Code 和\\\bin 目錄不可為巢狀子目錄中。|
