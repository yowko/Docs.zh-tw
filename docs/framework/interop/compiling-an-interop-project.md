---
title: "編譯 Interop 專案 | Microsoft Docs"
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
  - "COM Interop, 編譯"
  - "COM Interop, 公開 COM 元件"
  - "編譯 Interop 專案"
  - "將 COM 元件公開給 .NET Framework"
  - "與 Unmanaged 程式碼的互通, 編譯"
  - "與 Unmanaged 程式碼的互通, 公開 COM 元件"
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# 編譯 Interop 專案
參考一個或多個含有匯入 COM 型別之組件的 COM Interop 專案，其編譯方式也是和任何其他 Managed 專案一樣。  您可以在 Visual Studio 之類的開發環境中參考 Interop 組件，也可以在使用命令列編譯器時參考它們。  不論是哪一種情況，Interop 組件必須與其他專案檔案位於同一個目錄中，才能正確地編譯。  
  
 有兩種方式可參考 Interop 組件：  
  
-   內嵌 Interop 型別：從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]和 [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] 開始，您就可以指示編譯器將 Interop 組件的型別資訊內嵌至可執行檔中。  這是建議使用的技巧。  
  
-   部署 Interop 組件：您可以建立 Interop 組件的標準參考。  在這種情況下，Interop 組件必須隨您的應用程式一起部署。  
  
 [Using COM Types in Managed Code](http://msdn.microsoft.com/zh-tw/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)將詳細討論這兩種技術之間的差異。  
  
 [逐步解說：從 Microsoft Office 組件內嵌類型資訊](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md) 和[逐步解說：從 Managed 組件內嵌類型](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md) 將示範如何使用 Visual Studio 來內嵌 Interop 型別。  
  
 若要使用命令列編譯器來參考 Interop 組件並將型別資訊內嵌在可執行檔中，請使用 [\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md) 或 [\/link](../Topic/-link%20\(Visual%20Basic\).md) 編譯器參數並指定 Interop 組件的名稱。  
  
> [!NOTE]
>  雖然 Visual C\+\+ 應用程式無法內嵌型別資訊，不過它們可以與可內嵌的應用程式或增益集互通。  
  
 若要編譯包括主要 Interop 組件的應用程式 \(已部署組件時\)，請使用 **\/reference** 編譯器參數並指定 Interop 組件的名稱。  
  
## 請參閱  
 [將 COM 元件公開給 .NET Framework](../../../docs/framework/interop/exposing-com-components.md)   
 [語言獨立性以及與語言無關的元件](../../../docs/standard/language-independence-and-language-independent-components.md)   
 [Using COM Types in Managed Code](http://msdn.microsoft.com/zh-tw/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)   
 [逐步解說：從 Microsoft Office 組件內嵌類型資訊](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [逐步解說：從 Managed 組件內嵌類型](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [匯入類型程式庫做為組件](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)