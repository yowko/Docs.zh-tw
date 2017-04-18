---
title: "當地語系化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式開發 [.NET Framework], 當地語系化"
  - "程式碼區塊"
  - "文化特性, 當地語系化"
  - "全域應用程式, 當地語系化"
  - "全球化 [.NET Framework], 當地語系化"
  - "國際應用程式 [.NET Framework], 當地語系化"
  - "當地語系化 [.NET Framework], 關於當地語系化"
  - "當地語系化資源"
  - "使用者介面區塊"
  - "世界性的應用程式, 當地語系化"
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 當地語系化
當地語系化是轉譯針對應用程式支援的所有文化特性，將應用程式資源為當地語系化版本的程序。  您必須在完成[可當地語系化檢閱](../../../docs/standard/globalization-localization/localizability-review.md)步驟，驗證全球化應用程式已準備進行當地語系化之後，才能前進到當地語系化步驟。  
  
 準備好執行當地語系化的應用程式被分成兩個區塊，一個是含有所有使用者介面項目的區塊，另一個則含有可執行碼。  使用者介面區塊含有可當地語系化的使用者介面項目，例如中性文化特性的字串、錯誤訊息、對話方塊、功能表、內嵌物件資源 \(Embedded Object\) 資源等等。  程式碼區塊中則僅含有所有支援文化特性所使用的應用程式碼。  Common Language Runtime 支援附屬組件支援模型，後者分隔應用程式的可執行碼和其資源。  如需實作此模型的詳細資訊，請參閱[桌面應用程式中的資源](../../../docs/framework/resources/index.md)。  
  
 針對應用程式的每一個當地語系化版本，加入新的附屬應用程式組件，其中包含轉譯為適用於目標文化特性語言的當地語系化使用者介面區塊。  所有文化特性碼區塊應維持不變。  使用者介面區塊的當地語系化版本和程式碼區塊組合可產生您應用程式的當地語系化版本。  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供 Windows Form 資源編輯器 \(Winres.exe\)，可讓您將 Windows Form 快速當地語系化為目標文化特性。  如需使用此工具的詳細資訊，請參閱 [Winres.exe \(Windows Forms Resource Editor\)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)。  
  
## 請參閱  
 [全球化和當地語系化](../../../docs/standard/globalization-localization/index.md)   
 [可當地語系化檢閱](../../../docs/standard/globalization-localization/localizability-review.md)   
 [全球化](../../../docs/standard/globalization-localization/globalization.md)   
 [桌面應用程式中的資源](../../../docs/framework/resources/index.md)