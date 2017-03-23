---
title: "#pragma 總和檢查碼 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#pragma checksum"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#pragma checksum [C#]"
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# #pragma 總和檢查碼 (C# 參考)
產生原始程式檔 \(Source File\) 的總和檢查碼 \(Checksum\)，以協助對 [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] 頁面進行偵錯。  
  
## 語法  
  
```  
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### 參數  
 `"filename"`  
 監視變更或更新時所需的檔案名稱。  
  
 `"{guid}"`  
 檔案的全域唯一識別項 \(Globally Unique Identifier，GUID\)。  
  
 `"checksum_bytes"`  
 代表總和檢查碼之位元組的十六進位數字字串。  這必須是偶數的十六進位數字。  奇數數字會導致編譯時期警告，而且會忽略指示詞。  
  
## 備註  
 Visual Studio 偵錯工具會使用總和檢查碼，以確保它一定會找到正確的原始檔。  編譯器會計算原始程式檔的總和檢查碼，然後將輸出發至程式資料庫檔案 \(Program Database File，PDB\)。  接著偵錯工具會使用 PDB 來比對為原始程式檔計算的總和檢查碼 \(Checksum\)。  
  
 由於計算出來的總和檢查碼是針對產生的原始程式檔，而不是 .aspx 檔，因此這個辦法不適用於 [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] 專案。  為了解決這個問題，`#pragma checksum` 提供 [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] 頁面的總和檢查碼支援。  
  
 當您在 [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] 建立 [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] 專案時，所產生的原始程式碼會包含 .aspx 檔的總和檢查碼，而原始檔便是由此 .aspx 檔產生。  接著編譯器將此資訊寫入 PDB 檔案中。  
  
 如果編譯器在檔案中沒有遇到 `#pragma checksum` 指示詞，它會計算出總和檢查碼並將此值寫入 PDB 檔案。  
  
## 範例  
  
```  
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)