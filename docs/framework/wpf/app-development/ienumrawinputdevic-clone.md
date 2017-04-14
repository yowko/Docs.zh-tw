---
title: "IEnumRAWINPUTDEVIC:Clone | Microsoft Docs"
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
  - "Clone 方法"
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# IEnumRAWINPUTDEVIC:Clone
建立另一個與目前列舉值相同狀態的未經處理輸入裝置列舉值，以逐一查看同一份清單。  
  
## 語法  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### 參數  
 `ppenum`  
  
 \[out\] 輸出變數的位址，會接收 [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) 介面指標。  如果此方法失敗，則未定義此輸出變數的值。  
  
## 屬性值\/傳回值  
 HRESULT：此方法支援標準傳回值 E\_INVALIDARG、E\_OUTOFMEMORY 和 E\_UNEXPECTED。  
  
## 備註  
 此方法能夠記錄列舉型別序列 \(Enumeration Sequence\) 中的點，以便稍後返回該點。  呼叫端必須與第一個列舉值分開發行這個新的列舉值。