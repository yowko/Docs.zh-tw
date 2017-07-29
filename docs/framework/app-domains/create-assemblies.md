---
title: "建立組件 | Microsoft Docs"
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
  - "組件 [.NET Framework], 建立"
  - "組件 [.NET Framework], 多檔案"
  - "多檔案組件"
  - "單一檔案組件"
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 建立組件
您可以使用整合式開發環境 \(IDE\) \(例如 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]\) 或是 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 所提供的編譯器和工具來建立單一檔案或多檔案的組件。  最簡易的組件即為具有簡式名稱、且已載入單一應用程式定義域的單一檔案。  這個組件無法由應用程式目錄以外的其他組件存取，而且無法進行版本檢查。  如果要解除安裝由組件所組成的應用程式，您只要刪除該應用程式所在的目錄即可。  對許多開發人員而言，他們只需要具有這些功能的組件便可完成部署應用程式。  
  
 您可以從數個程式碼模組和資訊檔建立多檔案組件。  您也可以建立可由多重應用程式共用的組件。  共用組件必須具有強式名稱，並可部署在全域組件快取中。  
  
 當您將程式碼模組和資源分組成為組件時，您將根據下列因素可使用數個選項：  
  
-   版本控制  
  
     擁有相同版本資訊的群組模組。  
  
-   部署  
  
     支援您部署模型的群組程式碼模組和資源。  
  
-   重覆使用  
  
     群組模組，如果該群組模組因某些原因而同時邏輯式使用。  例如，由型別和類別組成、且不常用來進行程式維護的組件將可放入相同的組件中。  此外，您應將要用來與多重應用程式共用的型別分組成為組件，而該組件則應使用強式名稱簽名。  
  
-   安全性  
  
     群組模組，需要相同的安全性使用權限且含有型別。  
  
-   範圍  
  
     含有型別的群組模組，其可視性應限制為相同的組件。  
  
 當您將 Common Language Runtime 組件變成 Unmanaged COM 應用程式時，您必須注意某些特殊考量。  如需使用 Unmanaged 程式碼的詳細資訊，請參閱[將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)。  
  
## 請參閱  
 [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md)   
 [如何：建置單一檔案組件](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)   
 [如何：建置多檔案組件](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [多檔案組件](../../../docs/framework/app-domains/multifile-assemblies.md)