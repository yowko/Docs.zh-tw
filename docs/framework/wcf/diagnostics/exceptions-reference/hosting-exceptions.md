---
title: 裝載例外狀況
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: 342420f10ed53e4f4786ed9506cfde5fbfcfc957
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263330"
---
# <a name="hosting-exceptions"></a>裝載例外狀況

這個主題會列出由裝載所產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|不允許完整的 URI。 完整的 URI 不允許用於 ServiceHostingEnvironment.EnsureServiceAvailable API。 請使用對應服務的虛擬路徑。|  
|Hosting_BuildProviderCouldNotCreateType|在服務編譯期間無法載入指定的 CLR 類型。 確認此類型定義于位於應用程式 \ App_Code 目錄的原始程式檔中 \\ ，該檔案包含在應用程式的 \bin 目錄中的已編譯元件中 \\ ，或存在於全域組件快取中安裝的元件。 類型名稱需區分大小寫。 目錄（例如 \\ \ App_Code 和 \\ \bin）必須位於應用程式的根目錄中。 \\\ App_Code 和 \\ \bin 目錄不能嵌套在子目錄中。|
