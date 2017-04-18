---
title: "如何：將參考加入至類型程式庫 | Microsoft Docs"
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
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：將參考加入至類型程式庫
Visual Studio 會產生內含新增類型程式庫參考時所產生之中繼資料的 interop 組件。  如有提供主要的 Interop 組件，Visual Studio 便會先使用現有的組件，然後再產生新的 Interop 組件。  
  
### 新增 Visual Studio 中之類型程式庫的參考  
  
1.  若 Windows Setup.exe 未在您的電腦上安裝 COM DLL 或 EXE 檔案，請自行安裝。  
  
2.  依序選擇 \[專案\] 及 \[加入參考\]。  
  
3.  在 \[參考管理員\]，選擇 \[COM\]。  
  
4.  從清單中選取類型程式庫，或瀏覽至 .tlb 檔案。  
  
5.  選擇 \[**確定**\]。  
  
6.  在 \[方案總管\] 中，開啟所新增之參考的捷徑功能表，然後選擇 \[屬性\]。  
  
7.  在 \[屬性\] 視窗中，確定 \[內嵌 Interop 類型\] 屬性已設為 \[True\]。  這可讓 Visual Studio 將 COM 類型的類型資訊嵌入您的可執行檔中，免除將主要 Interop 組件部署到應用程式的動作。  
  
> [!NOTE]
>  功能表與對話方塊可能會隨您所使用的 Visual Studio 版本而不同。  
  
### 新增類型程式庫參考供命令列編譯時使用  
  
1.  依 [如何：從類型程式庫產生 Interop 組件](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md) 所述產生 Interop 組件。  
  
2.  使用 [\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md) 或 [\/link](../Topic/-link%20\(Visual%20Basic\).md) 編譯器選項加上 Interop 組件名稱，將 COM 類型的類型資訊嵌入您的可執行檔中。  
  
## 請參閱  
 [匯入類型程式庫做為組件](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [將 COM 元件公開給 .NET Framework](../../../docs/framework/interop/exposing-com-components.md)   
 [逐步解說：從 Microsoft Office 組件內嵌類型資訊](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [逐步解說：從 Managed 組件內嵌類型](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md)   
 [\/link](../Topic/-link%20\(Visual%20Basic\).md)