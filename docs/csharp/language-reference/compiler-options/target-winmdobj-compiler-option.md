---
title: "/target:winmdobj (C# 編譯器選項) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /target:winmdobj (C# 編譯器選項)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

如果您使用 **\/target:winmdobj** 編譯器選項，編譯器會建立一個可轉換成 Windows 執行階段二進位檔案 \(.winmd\) 的中繼 .winmdobj 檔案。  除了 Managed 語言程式之外，JavaScript 和 C\+\+ 程式也可以使用 .winmd 檔案。  
  
## 語法  
  
```  
/target:winmdobj  
```  
  
## 備註  
 **winmdobj** 設定對編譯器發出訊號，表示需要中繼模組。  Visual Studio 將 C\# 類別庫編譯為 .winmdobj 檔案，做為回應。  然後 .winmdobj 檔案可以透過 <xref:Microsoft.Build.Tasks.WinMDExp> 匯出工具產生 Windows 中繼資料 \(.winmd\) 檔案。  .winmd 檔案包含原始類別庫的程式碼，以及 JavaScript 或 C\+\+ 和 Windows 執行階段所使用的 WinMD 中繼資料。  
  
 使用 **\/target:winmdobj** 編譯器選項所編譯之檔案的輸出，其設計目的只做為 WimMDExp 匯出工具的輸入使用，並不能直接參考 .winmdobj 檔案本身。  
  
 除非您使用 [\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔名稱，否則將會以第一個輸入檔名稱命名。  不需要 [Main](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) 方法。  
  
 如果您在命令提示字元指定 \/target:winmdobj 選項，直到下一個 **\/out** 或 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 選項之前所有的檔案都會用來建立 Windows 程式。  
  
### 若要在 Visual Studio IDE 中為 Windows 市集應用程式設定這個編譯器選項  
  
1.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**屬性**\]。  
  
2.  選擇 \[**應用程式**\] 索引標籤。  
  
3.  在 \[**輸出類型**\] 清單中，選擇 \[**WinMD 檔案**\]。  
  
     \[**WinMD 檔案**\] 選項僅適用於 [!INCLUDE[win8_appname_long](../../../csharp/language-reference/compiler-options/includes/win8_appname_long_md.md)]應用程式範本。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## 範例  
 下列命令會將 `filename.cs` 編譯到中繼 .winmdobj 檔案。  
  
```  
csc /target:winmdobj filename.cs  
```  
  
## 請參閱  
 [\/target \(Specify Output File Format\)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)