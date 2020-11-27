---
title: invalidIUnknown MDA
description: 請參閱 invalidIUnknown managed 偵錯工具 (MDA) ，這會在不正確 IUnknown 指標從機器碼傳遞給 managed 程式碼時啟動。
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
ms.openlocfilehash: 8e7ca6c9c43c4f507d235c879498b2e831c6eba9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272536"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA

當無效的 `IUnknown` 指標從原生程式碼傳遞至 Managed 程式碼時，會啟動 `invalidIUnknown` Managed 偵錯助理 (MDA)。 查詢 `IUnknown` 介面時，`IUnknown` 無法成功傳回。  
  
## <a name="symptoms"></a>徵狀  

 引數封送處理期間，在封送處理 COM 介面指標時，發生未預期的錯誤。  
  
## <a name="cause"></a>原因  

 對於傳遞至 CLR 的 COM 介面進行了不正確的 `QueryInterface` 實作。  
  
## <a name="resolution"></a>解決方法  

 更正 `QueryInterface` 實作。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  

 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>輸出  

 錯誤的描述。  
  
## <a name="configuration"></a>設定  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [診斷 Managed 偵錯助理的錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
