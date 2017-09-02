---
title: "使用組件和全域組件快取 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "存取控制清單 [.NET Framework]"
  - "ACL [.NET Framework]"
  - "組件 [.NET Framework], 全域組件快取"
  - "GAC (全域組件快取), 好處"
  - "全域組件快取, 好處"
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 使用組件和全域組件快取
如果您想要在數個應用程式之間共用組件，可以將組件安裝在全域組件快取中。  每一部安裝有 Common Language Runtime 的電腦都具有這個電腦程式快取。  全域組件快取會儲存要專門指定給電腦上一些應用程式共用的組件。  組件要求在全域組件快取中必須安裝強式名稱。  
  
> [!NOTE]
>  放置在全域組件快取中的組件必須具有相同的組件名稱和檔名 \(不包括副檔名\)。  例如，使用 myAssembly 名稱的組件的檔名必須是 myAssembly.exe 或 myAssembly.dll。  
  
 您應該只有在需要的時候才將組件安裝到全域組件快取中來共用它們。  基本的指導原則是，除非共用組件確有必要，否則應使組件相依性保持私用 \(Private\)，並將組件置於應用程式目錄中。  除此而外，您不需要將組件安裝到全域組件快取中使它們能讓 COM Interop 或 Unmanaged 程式碼存取。  
  
 可能有下列原因，讓您想要將組件安裝到全域組件快取：  
  
-   共用位置。  
  
     您可以將應用程式使用的組件放入全域組件快取中。  例如，如果所有應用程式都使用位於全域組件快取的組件，您可以將版本規則聲明加入 Machine.config 檔，該檔可將參考重新導向到組件。  
  
-   檔案安全性。  
  
     系統管理員通常會使用存取控制清單 \(ACL\) 來控制撰寫和執行存取，藉此保護 systemroot 目錄。  由於全域組件快取安裝在 systemroot 目錄中，因此它繼承了該目錄的 ACL。  建議使用者只有在具備系統管理員權限時，才能從全域組件快取刪除檔案。  
  
-   並存版本。  
  
     您可以在全域組件快取中維護擁有多個相同名稱、但具有不同版本資訊的組件副本。  
  
-   其他搜尋位置。  
  
     在探測或使用組態檔的基礎碼資訊之前，Common Language Runtime 會檢查符合組件要求的組件的全域組件快取。  
  
 請注意，在有些案例中，您務必不可將組件安裝到全域組件快取中。  如果您將構成應用程式的其中一個組件置於全域組件快取中，那麼您就不能藉由使用 XCOPY 複製應用程式目錄來複製或安裝應用程式。  在這種情況下，您必須也將組件移到全域組件快取中。  
  
## 在本節中  
 [如何：將組件安裝到全域組件快取](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 說明將組譯碼安裝到全域組件快取中方式。  
  
 [如何：檢視全域組件快取的內容](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)  
 解說如何使用 [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 來檢視全域組件快取的內容。  
  
 [如何：從全域組件快取移除組件](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 解說如何使用 [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 從全域組件快取中移除某個組件。  
  
 [使用 Serviced 元件和全域組件快取](../../../docs/framework/app-domains/use-serviced-components-with-the-gac.md)  
 解說為什麼 Serviced 元件 \(Managed COM\+ 元件\) 應該放入全域組件快取中。  
  
## 相關章節  
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)  
 提供建立組件的概觀。  
  
 [全域組件快取](../../../docs/framework/app-domains/gac.md)  
 說明全域組件快取。  
  
 [如何：檢視組件內容](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 解說如何使用 [Ildasm.exe \(IL Disassembler\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢視組件中的 Microsoft Intermediate Language \(MSIL\) 資訊。  
  
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 說明 Common Language Runtime 是如何尋找及載入構成應用程式的組件。  
  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 說明 Managed 應用程式的建置組塊，也就是組件。