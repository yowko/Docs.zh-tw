---
title: ".NET Framework 4.6 和 4.5 移轉手冊  | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework，移轉應用程式至"
  - "移轉，.NET Framework"
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
caps.latest.revision: 56
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# .NET Framework 4.6 和 4.5 移轉手冊 
如果您使用舊版的 .NET Framework 建立應用程式，通常可以輕鬆地將它升級到 .NET Framework 4.5、4.5.1 或 4.6。 在 Visual Studio 中開啟專案。 如果您的專案是使用舊版所建立，則 \[**專案相容性**\] 對話方塊會自動開啟。 如需升級 Visual Studio 2013 專案的詳細資訊，請參閱[如何：升級以舊版 Visual Studio 建立的專案](http://msdn.microsoft.com/library/vstudio/ms185327\(v=vs.100\).aspx) 和 [移植、移轉和升級 Visual Studio 專案](../Topic/Porting,%20Migrating,%20and%20Upgrading%20Visual%20Studio%20Projects.md)。  
  
 不過，.NET Framework 中的某些變更需要變更您的程式碼。 您可能也會想要利用 .NET Framework 4.5、其單點發行版本或 .NET Framework 4.6 中的某些新功能。 針對新版本的 .NET Framework 對您的應用程式所做的這種類型的變更通常稱為「*移轉*」\(Migration\)。 如果您的應用程式不必移轉，您可以在 .NET Framework 4.5 或更新版本中執行而不需重新編譯。  
  
## 移轉資源  
 將您的應用程式從舊版 .NET Framework 移轉至 4.5、4.5.1 或 4.5.2 版之前，請先檢閱下列文件：  
  
-   請參閱 [版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)，了解每個 .NET Framework 版本的基礎 CLR 版本，並檢閱成功鎖定目標應用程式的方針。  
  
-   檢閱 [應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)，了解可能影響應用程式的執行階段和重定目標變更，以及如何處理這些變更。  
  
-   檢閱 [類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)，以判斷您的程式碼中可能已過時的任何型別或成員以及建議的替代方法。  
  
-   如需應用程式想要加入的新功能說明，請參閱 [新功能](../../../docs/framework/whats-new/index.md)。  
  
## 請參閱  
 [4.5.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)   
 [4.5 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [從 .NET Framework 1.1 移轉](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)   
 [版本相容性](../../../docs/framework/migration-guide/version-compatibility.md)   
 [版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [HOW TO：設定應用程式以支援 .NET Framework 4 或 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)   
 [新功能](../../../docs/framework/whats-new/index.md)   
 [類別庫中的過時功能](../../../docs/framework/whats-new/whats-obsolete.md)   
 [.NET framework 版本和組件資訊](http://go.microsoft.com/fwlink/?LinkId=201701)   
 [Microsoft .NET Framework 支援週期原則](http://go.microsoft.com/fwlink/?LinkId=196607)