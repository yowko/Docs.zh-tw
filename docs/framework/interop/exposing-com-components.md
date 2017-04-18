---
title: "將 COM 元件公開給 .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM Interop, 公開 COM 元件"
  - "將 COM 元件公開給 .NET Framework"
  - "與 Unmanaged 程式碼的互通, 公開 COM 元件"
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 將 COM 元件公開給 .NET Framework
這個章節將摘要將現有 COM 元件公開給 Managed 程式碼所需的處理序。  如需撰寫與 .NET Framework 緊密整合之 COM 服務的詳細資訊，請參閱[互通的設計考量](http://msdn.microsoft.com/zh-tw/b59637f6-fe35-40d6-ae72-901e7a707689)。  
  
 現有 COM 元件在 Managed 程式碼中是珍貴的資源，可做為中介層 \(Middle Tier\) 商務應用程式或做為隔離的功能。  理想的元件具有主要 Interop 組件，並且密切遵守 COM 訂定的程式設計標準。  
  
#### 將 COM 元件公開給 .NET Framework  
  
1.  [匯入型別程式庫做為組件](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
  
     Common Language Runtime 需要所有型別的中繼資料 \(Metadata\)，包括 COM 型別。  有幾種方式可以取得含有匯入為中繼資料之 COM 型別的組件。  
  
2.  [在 Managed 程式碼中使用 COM 型別](http://msdn.microsoft.com/zh-tw/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
  
     您可以檢查 COM 型別、啟動執行個體和在 COM 物件上叫用方法，就和您在任何 Managed 型別上所進行的方式一樣。  
  
3.  [編譯 Interop 專案](../../../docs/framework/interop/compiling-an-interop-project.md)  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 提供數種符合 Common Language Specification \(CLS\) 之語言的編譯器，其中包括 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C\# 和 C\+\+。  
  
4.  [部署 Interop 應用程式](../../../docs/framework/interop/deploying-an-interop-application.md)  
  
     Interop 應用程式最適合部署為全域組件快取 \(GAC\) 中[具有強式名稱的](../../../docs/framework/app-domains/strong-named-assemblies.md)簽署組件。  
  
## 請參閱  
 [與 Unmanaged 程式碼互通](../../../docs/framework/interop/index.md)   
 [Design Considerations for Interoperation](http://msdn.microsoft.com/zh-tw/b59637f6-fe35-40d6-ae72-901e7a707689)   
 [COM Interop 範例：.NET 用戶端與 COM 伺服器](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)   
 [語言獨立性以及與語言無關的元件](../../../docs/standard/language-independence-and-language-independent-components.md)   
 [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)