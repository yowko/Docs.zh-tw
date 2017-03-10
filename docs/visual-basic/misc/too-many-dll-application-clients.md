---
title: "太多 DLL 應用程式用戶端 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID47"
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# 太多 DLL 應用程式用戶端
[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 的動態連結程式庫 \(DLL\) 只能容納有限數目的主應用程式所存取。 您的應用程式及其他 [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 主機應用程式 \(其中有些可能由您的應用程式存取\) 全都同時嘗試存取 [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] DLL。  
  
### 更正這個錯誤  
  
-   請減少存取 [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 的開放應用程式數目。  
  
## 請參閱  
 [Error Types](../../visual-basic/programming-guide/language-features/error-types.md)