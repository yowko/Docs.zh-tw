---
title: "How to: Validate File Names and Paths in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "file names, validating"
  - "strings [Visual Basic], validating"
  - "Boolean values"
  - "paths, validating"
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Validate File Names and Paths in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

這個範例會傳回 `Boolean` 值，指出字串是否表示檔案名稱或路徑。  驗證作業會檢查名稱是否包含檔案系統所不允許的字元。  
  
## 範例  
 [!CODE [VbVbcnRegEx#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbcnRegEx#4)]  
  
 這個範例不會檢查名稱的冒號位置是否正確、目錄是否沒有名稱，或名稱長度是否超過系統所定義的最大長度。  它也不會檢查應用程式是否具有使用權限可以存取具有指定之名稱的檔案系統資源。  
  
## 請參閱  
 <xref:System.IO.Path.GetInvalidPathChars%2A>   
 [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)