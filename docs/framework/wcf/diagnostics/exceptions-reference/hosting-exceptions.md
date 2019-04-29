---
title: 裝載例外狀況
ms.date: 03/30/2017
ms.assetid: ad9e14f8-fa17-4d59-b365-fe0e7ec17c98
ms.openlocfilehash: f2bc7d0ca09faa2598990437295d1abf0cff3c45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934728"
---
# <a name="hosting-exceptions"></a>裝載例外狀況
這個主題會列出由裝載所產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|Hosting_AddressIsAbsoluteUri|不允許完整的 URI。 完整的 URI 不允許用於 ServiceHostingEnvironment.EnsureServiceAvailable API。 請使用對應服務的虛擬路徑。|  
|Hosting_BuildProviderCouldNotCreateType|在服務編譯期間無法載入指定的 CLR 類型。 請確認此類型可能是位於應用程式的原始程式檔中已定義\\\App_Code 目錄中，位於 應用程式的已編譯組件中包含\\\bin 目錄，或存在於組件安裝在全域組件快取。 類型名稱需區分大小寫。 這類目錄\\\App_Code 和\\\bin 必須位於應用程式的根目錄。 \\\App_Code 和\\\bin 目錄不可為巢狀子目錄中。|
