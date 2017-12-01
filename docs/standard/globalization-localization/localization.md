---
title: "當地語系化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4aaf2da77a1fab55cbebd6bfa05a2b1c74e5cbbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="localization"></a>當地語系化
當地語系化是轉譯為每個應用程式將支援的文化特性的當地語系化版本的應用程式資源的程序。 您應該完成後才繼續進行當地語系化步驟[當地語系化能力審查](../../../docs/standard/globalization-localization/localizability-review.md)步驟，以確認全球化應用程式已準備好進行當地語系化。  
  
 準備好進行當地語系化的應用程式分成兩個區塊的區塊，其中包含所有的使用者介面項目，包含可執行程式碼的區塊。 使用者介面區塊包含只可當地語系化的使用者介面元素，例如字串、 錯誤訊息、 對話方塊、 功能表、 內嵌的物件，依此類推中性文化特性的資源。 程式碼區塊包含只可供所有支援的文化特性的應用程式程式碼。 通用語言執行平台支援將應用程式的可執行程式碼和其資源的附屬組件資源模型。 如需實作此模型的詳細資訊，請參閱[桌面應用程式中的資源](../../../docs/framework/resources/index.md)。  
  
 每個當地語系化版本的應用程式，加入新的附屬組件，其中包含轉譯成適當的語言為目標的文化特性的當地語系化的使用者介面區塊。 所有文化特性的程式碼區塊應該維持不變。 使用者介面區塊的程式碼區塊的當地語系化版本的組合會產生您的應用程式的當地語系化的版本。  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]提供 Windows Form 資源編輯器 (Winres.exe)，可讓您快速將 Windows Form 當地語系化目標文化特性。 使用此工具的相關資訊，請參閱[Winres.exe （Windows Form 資源編輯器）](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)。  
  
## <a name="see-also"></a>另請參閱  
 [全球化和當地語系化](../../../docs/standard/globalization-localization/index.md)  
 [可當地語系化檢閱](../../../docs/standard/globalization-localization/localizability-review.md)  
 [全球化](../../../docs/standard/globalization-localization/globalization.md)  
 [桌面應用程式中的資源](../../../docs/framework/resources/index.md)
