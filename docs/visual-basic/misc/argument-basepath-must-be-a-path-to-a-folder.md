---
title: "引數 BasePath 必須是資料夾路徑 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: b180ce60-ad57-41a6-a313-491d86d84cc7
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# 引數 BasePath 必須是資料夾路徑
引數 `BasePath` 必須是由資料夾路徑所組成。 您可能不正確地剖析字串，並提供無法辨識為有效路徑的值。  
  
### 更正這個錯誤  
  
-   檢查您提供給 `BasePath` 的值，確定它是有效的資料夾路徑。  
  
## 請參閱  
 <xref:System.CodeDom.Compiler.TempFileCollection.BasePath%2A>   
 <xref:System.Resources.ResXResourceWriter.BasePath%2A>   
 <xref:System.Resources.ResXResourceReader.BasePath%2A>   
 [如何：剖析檔案路徑](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)