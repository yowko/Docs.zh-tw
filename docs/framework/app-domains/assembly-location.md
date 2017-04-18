---
title: "組件位置 | Microsoft Docs"
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
  - "組件 [.NET Framework], 位置"
  - "尋找組件"
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# 組件位置
組件的位置可決定當 Common Language Runtime 被參考時是否能找到執行階段的位置，並可決定組件是否可供其他組件共用。  您可以在下列位置部署組件：  
  
-   應用程式目錄或子目錄  
  
     這是部署組件時最常用的位置。  應用程式根目錄的子目錄可以語言或文化特性做為基礎。  如果組件擁有文化特性屬性資訊，則該組件必須位於以該文化特性名稱為名的應用程式目錄下的子目錄中。  
  
-   全域組件快取  
  
     此為機器程式碼快取，該快取與 Common Language Runtime 的安裝位置相同。  在多數情況下，如果您想要與多個應用程式共用組件，請將它部署到全域組件快取中。  
  
-   在 HTTP 伺服器上  
  
     部署在 HTTP 伺服器上的組件必須使用強式名稱；請指向應用程式檔案的程式碼基底區段中的組件。  
  
## 請參閱  
 [建立組件](../../../docs/framework/app-domains/create-assemblies.md)   
 [全域組件快取](../../../docs/framework/app-domains/gac.md)   
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)