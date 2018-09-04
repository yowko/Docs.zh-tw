---
title: '.NET Framework 4.7、4.6 和 4.5 移轉手冊 '
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- .NET Framework, migrating applications to
- migration, .NET Framework
ms.assetid: 02d55147-9b3a-4557-a45f-fa936fadae3b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc3796e3e79112b14d45bb410e63656a81d474c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526716"
---
# <a name="migration-guide-to-the-net-framework-47-46-and-45"></a>.NET Framework 4.7、4.6 和 4.5 移轉手冊 
如果您使用舊版的 .NET Framework 建立應用程式，通常可以輕鬆地將它升級到 .NET Framework 4.5 及其小數點版本 (4.5.1 和 4.5.2)、.NET Framework 4.6 及其小數點版本 (4.6.1 和 4.6.2) 或 .NET Framework 4.7 及其小數點版本 (4.7.1 和 4.7.2)。 在 Visual Studio 中開啟專案。 如果您的專案是使用舊版 Visual Studio 所建立，則會自動開啟 [專案相容性] 對話方塊。 如需升級 Visual Studio 專案的詳細資訊，請參閱[移植、移轉及升級 Visual Studio 專案](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)和 [Visual Studio 2017 平台目標及相容性](/visualstudio/productinfo/vs2017-compatibility-vs)。  
  
 不過，.NET Framework 中的某些變更需要變更您的程式碼。 您也可能想要利用 .NET Framework 4.5 及其小數點版本、.NET Framework 4.6 及其小數點版本、.NET Framework 4.7 及其小數點版本中的某些新功能。 針對新版 .NET Framework 對您應用程式所做之這些類型的變更通常稱為「移轉」。 如果您的應用程式不必移轉，您可以在 .NET Framework 4.5 或更新版本中執行它，而不需要重新編譯。  
  
## <a name="migration-resources"></a>移轉資源  
 將您的應用程式從舊版 .NET Framework 移轉至 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1 或 4.7.2 之前，請先檢閱下列文件：  
  
-   請參閱[版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)，了解每個 .NET Framework 版本的基礎 CLR 版本，並檢閱成功設定應用程式目標的方針。  
  
-   檢閱[應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)，了解可能影響應用程式的執行階段和重定目標變更，以及如何處理這些變更。  
  
-   檢閱[類別庫中已淘汰的功能](../../../docs/framework/whats-new/whats-obsolete.md)，以判斷您的程式碼中可能已淘汰的任何類型或成員，以及建議的替代做法。  
  
-   如需想要新增至應用程式之新功能的描述，請參閱[新功能](../../../docs/framework/whats-new/index.md)。  
  
## <a name="see-also"></a>請參閱  
 [應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)  
 [從 .NET Framework 1.1 移轉](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)  
 [版本相容性](../../../docs/framework/migration-guide/version-compatibility.md)  
 [版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)  
 [操作說明：設定應用程式以支援 .NET Framework 4 或 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [新功能](../../../docs/framework/whats-new/index.md)  
 [類別庫中已淘汰的功能](../../../docs/framework/whats-new/whats-obsolete.md)  
 [.NET Framework 版本和組件資訊](https://go.microsoft.com/fwlink/?LinkId=201701)  
 [Microsoft .NET Framework 支援週期原則](https://go.microsoft.com/fwlink/?LinkId=196607)[.NET Framework 4 移轉問題](net-framework-4-migration-issues.md)
