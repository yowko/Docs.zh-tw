---
title: "如何：參考 COM 的 .NET 類型 | Microsoft Docs"
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
  - "COM Interop, 參考 .NET 類型"
  - "匯入類型程式庫"
  - "與 Unmanaged 程式碼的互通, 匯入類型程式庫"
  - "與 Unmanaged 程式碼的互通, 參考 .NET 類型"
  - "參考 .NET 類型"
  - "類型程式庫"
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：參考 COM 的 .NET 類型
從用戶端和伺服端程式碼的觀點，COM 和 .NET Framework 之間的差異大部分是無形的。  Microsoft Visual Basic 用戶端可以在物件瀏覽器中檢視 .NET 物件，公開物件方法和語法、屬性和欄位，就像它是任何其他 COM 物件一樣。  
  
 對於 C\+\+ 用戶端而言，匯入型別程式庫的處理序稍微要複雜一些，不過您還是使用同樣的工具將中繼資料匯出到 COM 型別程式庫。  若要從 Unmanaged C\+\+ 用戶端參考 .NET 物件成員，請使用 **\#import** 指示詞參考 TLB 檔案 \(使用 Tlbexp.exe 產生\)。  在 C\+\+ 中參考型別程式庫時，必須指定 **raw\_interfaces\_only** 選項，或匯入基底類別程式庫 Mscorlib.tlb 中的定義。  
  
### 匯入程式庫  
  
-   在 **\#import** 指示詞中指定 **raw\_interfaces\_only** 選項。  例如：  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     \-或\-  
  
-   包含 Mscorlib.tlb 的 \#import 指示詞。  例如：  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## 請參閱  
 [將 .NET Framework 元件公開給 COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [向 COM 註冊組件](../../../docs/framework/interop/registering-assemblies-with-com.md)   
 [Calling a .NET Object](http://msdn.microsoft.com/zh-tw/40c9626c-aea6-4bad-b8f0-c1de462efd33)   
 [Deploying an Application for COM Access](http://msdn.microsoft.com/zh-tw/fb63564c-c1b9-4655-a094-a235625882ce)