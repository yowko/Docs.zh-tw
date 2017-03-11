---
title: "Clipboard format is not valid | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID460"
dev_langs: 
  - "VB"
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Clipboard format is not valid
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定的剪貼簿檔案格式與執行的方法不相容。  可能導致本錯誤的各種原因包括：  
  
-   以 `vbCFText` 或 `vbCFLink` 以外的剪貼簿檔案格式，使用剪貼簿的 `GetText` 或 `SetText` 方法。  
  
-   以 `vbCFBitmap`、`vbCFDIB` 或 `vbCFMetafile` 以外的剪貼簿檔案格式，使用剪貼簿的 `GetData` 或 `SetData` 方法。  
  
-   如果尚未在 Microsoft Windows 中註冊剪貼簿檔案格式時，可以在 Microsoft Windows 為註冊格式所保留的範圍 \(&HC000\-&HFFFF\) 內，以該剪貼簿檔案格式使用 `DataObject` `GetData` 方法或 `SetData` 方法。  
  
### 若要更正這個錯誤  
  
-   請移除無效格式並指定為有效的格式。  
  
## 請參閱  
 [剪貼簿：加入其他格式](../Topic/Clipboard:%20Adding%20Other%20Formats.md)