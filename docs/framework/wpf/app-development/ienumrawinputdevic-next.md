---
title: "IEnumRAWINPUTDEVIC:Next | Microsoft Docs"
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
  - "Next 方法"
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# IEnumRAWINPUTDEVIC:Next
將接下來的 `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) 結構列舉在列舉值的清單中，將其傳回在 `rgelt`，並隨附 `pceltFetched` 中列舉項目的實際數目。  
  
## 語法  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### 參數  
 `celt`  
  
 \[in\] 傳回 `rgelt` 中的 [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) 結構數目。  
  
 `rgelt`  
  
 \[out\] 要接收所列舉之 RAWINPUTDEVICE 結構的大小 celt \(或更大\) 陣列。  
  
 `pceltFetched`  
  
 \[out\] 指向 `rgelt` 中實際提供項目數的指標。  如果 `rgelt` 是 1，呼叫端就可以傳入 `NULL`。  
  
## 屬性值\/傳回值  
 HRESULT: 如果提供的項目數是 `celt`，則為 S\_OK；否則為 S\_FALSE。