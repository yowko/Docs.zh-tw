---
title: "IEnumRAWINPUTDEVIC:Skip | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Skip 方法"
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# IEnumRAWINPUTDEVIC:Skip
指示列舉值略過列舉型別 \(Enumeration\) 中的下一個 `celt` 項目，使 [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) 的下一個呼叫不會傳回這些項目。  
  
## 語法  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### 參數  
 `celt`  
  
 \[in\] 要略過的項目數。  
  
## 屬性值\/傳回值  
 HRESULT：如果提供的項目數為 `celt` 則為 S\_OK，否則為 S\_FALSE。