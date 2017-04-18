---
title: ".NET Framework 4.6 的應用程式相容性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3fd352-a8ba-4f9a-8250-951f2c994248
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# .NET Framework 4.6 的應用程式相容性
本主題提供 .NET Framework 4.5.2 與 4.6 間之應用程式相容性問題的資訊連結。  問題分為兩類：  
  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)  
 執行階段變更影響在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 下執行並使用特定功能的所有應用程式。  
  
 [重定目標變更](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)  
 重定目標變更會影響以 .NET Framework 4.5、4.5.1、4.5.2 或 4.6 為目標而重新編譯的應用程式。  包括：  
  
-   設計階段環境中的變更。  例如，建置工具可能會發出之前未發出的警告。  
  
-   執行階段環境中的變更。  這些變更只會影響專門以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 為目標的應用程式。  針對舊版 .NET Framework 之應用程式的行為，就像是在這些版本下執行的行為一樣。  
  
 在描述執行階段變更和重定目標變更的主題中，我們依每個項目的預期影響將項目分類如下：  
  
 主要  
 這是影響大量應用程式或需要大幅修改程式碼的重大變更。  
  
 次要  
 這是影響少量應用程式或需要稍微修改程式碼的變更。  
  
 邊緣案例  
 這是在非常特定 \(罕見\) 的情況下影響應用程式的變更。  
  
 透明  
 此變更對應用程式的開發人員或使用者的影響不明顯。  發生此變更的應用程式應該不需要修改。  
  
## 請參閱  
 [版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)   
 [應用程式相容性](../../../docs/framework/migration-guide/application-compatibility.md)   
 [4.5 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.5.1 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)   
 [4.5.2 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-2.md)