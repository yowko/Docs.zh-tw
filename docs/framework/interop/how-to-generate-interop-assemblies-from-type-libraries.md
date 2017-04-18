---
title: "如何：從類型程式庫產生 Interop 組件 | Microsoft Docs"
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
  - "COM Interop, 匯入類型程式庫"
  - "匯入類型程式庫"
  - "Interop 組件, 產生"
  - "類型程式庫"
  - "類型程式庫匯入工具"
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：從類型程式庫產生 Interop 組件
[型別程式庫匯入工具 \(Tlbimp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 是一種命令列工具，可以將 COM 型別程式庫中包含的 Coclass 和介面轉換為中繼資料。  這個工具會自動為型別資訊建立 Interop 組件和命名空間。  當類別的中繼資料成為可用之後，Managed 用戶端就可以建立 COM 型別的執行個體並且呼叫它的方法，就如同它是 .NET 執行個體一樣。  Tlbimp.exe 會一次將整個型別程式庫轉換為中繼資料，而且不能為型別程式庫中定義的型別子集產生型別資訊。  
  
### 若要從型別程式庫產生 Interop 組件  
  
1.  使用下列命令：  
  
     **tlbimp** \<*type\-library\-file*\>  
  
     新增 **\/out:** 參數會產生已變更名稱的 Interop 組件，例如 LOANLib.dll。  變更 Interop 組件的名稱有助於和原始 COM DLL 區別，且可避免因為重複名稱而產生的問題。  
  
## 範例  
 下列命令會在 `Loanlib` 命名空間中產生 Loanlib.dll 組件。  
  
```  
tlbimp Loanlib.dll  
```  
  
 下列命令會產生已變更名稱 \(LOANLib.dll\) 的 Interop 組件。  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## 請參閱  
 [匯入類型程式庫做為組件](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [將 COM 元件公開給 .NET Framework](../../../docs/framework/interop/exposing-com-components.md)