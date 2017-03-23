---
title: "#pragma (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#pragma"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#pragma 指示詞 [C#]"
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# #pragma (C# 參考)
`#pragma` 會為編譯器提供特殊指示，以供此編譯器所在位置的檔案編譯使用。  編譯器必須要支援此指示。  換句話說，您不能使用 `#pragma` 建立自訂前置處理指示。  Microsoft C\# 編譯器支援下列兩個 `#pragma` 指示：  
  
 [\#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [\#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## 語法  
  
```  
#pragma pragma-name pragma-arguments  
```  
  
#### 參數  
 `pragma-name`  
 已辨認的 Pragma 名稱。  
  
 `pragma-arguments`  
 Pragma 專屬的引數。  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 前置處理器指示詞](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [\#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)   
 [\#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)