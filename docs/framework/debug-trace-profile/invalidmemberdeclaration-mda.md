---
title: invalidMemberDeclaration MDA
description: 請參閱 invalidMemberDeclaration managed 偵錯工具，這是在不呼叫 managed 方法的情況下，將失敗的 HRESULT 傳回給 COM 時所叫用的協助工具。
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: c8d6c69fc6eb4f5f690b02809fdc492da675c3b1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272549"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA

會啟動 `invalidMemberDeclaration` Managed 偵錯助理 (MDA) 來報告錯誤，這些錯誤發生在決定如何封送處理成員參數為由 COM 所呼叫時。  
  
## <a name="symptoms"></a>徵狀  

 失敗的 HRESULT 會傳回給 COM，而不呼叫 Managed 方法。  
  
## <a name="cause"></a>原因  

 最可能的原因是其中一個參數上不相容的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。  
  
## <a name="resolution"></a>解決方法  

 請在此參數上指定有效的 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性。  
  
## <a name="effect-on-the-runtime"></a>對執行階段的影響  

 此 MDA 對 CLR 沒有影響。  
  
## <a name="output"></a>輸出  

 告知性訊息，包含成員名稱、類型名稱和錯誤訊息。  
  
## <a name="configuration"></a>設定  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [診斷 Managed 偵錯助理的錯誤](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop 封送處理](../interop/interop-marshaling.md)
