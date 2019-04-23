---
title: 組件位置
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c638531bd54f14c7e4b04a093deaec729db404ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129632"
---
# <a name="assembly-location"></a>組件位置
組件的位置可判斷 Common Language Runtime 是否可以在參考時找到它，也可以判斷是否可以與其他組件共用組件。 您可以在下列位置中部署組件：  
  
-   應用程式的目錄或子目錄。  
  
     這是部署組件的最常用位置。 應用程式根目錄的子目錄可以根據語言或文化特性。 如果組件具有文化特性屬性中的資訊，則必須在具有該文化特性名稱之應用程式目錄下的子目錄中。  
  
-   全域組件快取。  
  
     這是只要安裝 Common Language Runtime 的位置就會安裝的全機器程式碼快取。 在大部分情況下，如果您想要與多個應用程式共用組件，則應該將它部署到全域組件快取。  
  
-   在 HTTP 伺服器上。  
  
     HTTP 伺服器上部署的組件必須具有強式名稱；您指向應用程式組態檔的程式碼基底區段中的組件。  
  
## <a name="see-also"></a>另請參閱

- [建立組件](../../../docs/framework/app-domains/create-assemblies.md)
- [全域組件快取](../../../docs/framework/app-domains/gac.md)
- [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)
