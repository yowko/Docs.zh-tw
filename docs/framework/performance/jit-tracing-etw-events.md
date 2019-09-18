---
title: JIT 追蹤 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- JIT tracing events [.NET Framework]
- ETW, JIT tracing events (CLR)
ms.assetid: 926adde2-c123-452e-bf4f-4b977bf06ffb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 145a53363c9d7aca622ee0b1ccb2700e5984397d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046419"
---
# <a name="jit-tracing-etw-events"></a>JIT 追蹤 ETW 事件
<a name="top"></a> 這些事件會收集 just-in-time (JIT) 內嵌和 JIT tail 呼叫成功或失敗的相關資訊。  
  
 JIT 追蹤事件包含下列兩種類別：  
  
- [JIT 內嵌事件](#jit_inlining_events)  
  
- [JIT Tail 呼叫事件](#jit_tail_call_events)  
  
<a name="jit_inlining_events"></a>   
## <a name="jit-inlining-events"></a>JIT 內嵌事件  
  
### <a name="methodjitinliningfailed-event"></a>MethodJitInliningFailed 事件  
 下表說明關鍵字和層級。 (如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|詳細資訊 (5)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`MethodJitInliningFailed`|186|JIT 內嵌失敗。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|正在編譯之方法的命名空間。|  
|MethodBeingCompiledName|win:UnicodeString|正在編譯之方法的名稱。|  
|MethodBeingCompiledNameSignature|win:UnicodeString|正在編譯之方法的簽章。|  
|InlinerNamespace|win:UnicodeString|JIT 編譯器正在嘗試產生其程式碼之方法的命名空間。|  
|InlinerName|win:UnicodeString|編譯器正在嘗試產生其程式碼之方法的名稱。 如果編譯器嘗試內嵌程式碼到 `MethodBeingCompiledName` ，而非產生 `MethodBeingCompiledName` 的呼叫，則這可能與 `InlinerName`不同。|  
|InlinerNameSignature|win:UnicodeString|內嵌者的簽章。|  
|InlineeNamespace|win:UnicodeString|被內嵌者的命名空間。|  
|InlineeName|win:UnicodeString|編譯器嘗試要內嵌的方法 (而非產生呼叫)。|  
|InlineeNameSignature|win:UnicodeString|被內嵌者的簽章。|  
|FailAlways|win:Boolean|對 JIT 編譯器的提示，對於被內嵌者的內嵌一律將會失敗。|  
|FailReason|win:UnicodeString|INLINE_NEVER 表示先前的內嵌嘗試決定了內嵌因為某些原因永遠不會成功，否則則為自由形式文字。|  
|ClrInstanceID|win:UnicodeString|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
### <a name="methodjitinliningsucceeded-event"></a>MethodJitInliningSucceeded 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|詳細資訊 (5)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`MethodJitInliningSucceeded`|185|方法內嵌已成功。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|正在編譯之方法的命名空間。|  
|MethodBeingCompiledName|win:UnicodeString|正在編譯之方法的名稱。|  
|MethodBeingCompiledNameSignature|win:UnicodeString|正在編譯之方法的簽章。|  
|InlinerNamespace|win:UnicodeString|JIT 編譯器正在嘗試產生其程式碼之方法的命名空間。|  
|InlinerName|win:UnicodeString|編譯器正在嘗試產生其程式碼之方法的名稱。 如果編譯器嘗試內嵌程式碼到 `MethodBeingCompiledName` ，而非產生 `MethodBeingCompiledName` 的呼叫，則這可能與 `InlinerName`不同。|  
|InlinerNameSignature|win:UnicodeString|內嵌者的簽章。|  
|InlineeNamespace|win:UnicodeString|被內嵌者的命名空間。|  
|InlineeName|win:UnicodeString|編譯器嘗試要內嵌的方法 (而非產生呼叫)。|  
|InlineeNameSignature|win:UnicodeString|被內嵌者的簽章。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
 [回到頁首](#top)  
  
<a name="jit_tail_call_events"></a>   
## <a name="jit-tail-call-events"></a>JIT Tail 呼叫事件  
  
### <a name="methodjittailcallfailed-event"></a>MethodJITTailCallFailed 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|詳細資訊 (5)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallFailed`|189|方法 tail 呼叫失敗。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|正在編譯之方法的命名空間。|  
|MethodBeingCompiledName|win:UnicodeString|正在編譯之方法的名稱。|  
|MethodBeingCompiledNameSignature|win:UnicodeString|正在編譯之方法的簽章。|  
|CallerNamespace|win:UnicodeString|JIT 編譯器正在嘗試產生其程式碼之方法的命名空間。|  
|CallerName|win:UnicodeString|編譯器正在嘗試產生其程式碼之方法的名稱。|  
|CallerNameSignature|win:UnicodeString|呼叫者的簽章。|  
|CalleeNamespace|win:UnicodeString|被呼叫者的命名空間。|  
|CalleeName|win:UnicodeString|編譯器嘗試要 tail 呼叫的方法 (而非產生呼叫)。|  
|CalleeNameSignature|win:UnicodeString|被呼叫者的簽章。|  
|TailPrefix|win:Boolean|Tail 呼叫的前置詞|  
|FailReason|win:UnicodeString|Tail 呼叫失敗的原因。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
### <a name="methodjittailcallsucceeded-event"></a>MethodJITTailCallSucceeded 事件  
 下表說明關鍵字和層級。  
  
|引發事件的關鍵字|層級|  
|-----------------------------------|-----------|  
|`JITTracingKeyword` (0x10)|詳細資訊 (5)|  
  
 下表說明事件資訊。  
  
|Event - 事件|事件 ID|引發的時機|  
|-----------|--------------|-----------------|  
|`MethodJitTailCallSucceeded`|188|方法 tail 呼叫成功。|  
  
 下表說明事件資料。  
  
|欄位名稱|資料類型|描述|  
|----------------|---------------|-----------------|  
|MethodBeingCompiledNameSpace|win:UnicodeString|正在編譯之方法的命名空間。|  
|MethodBeingCompiledName|win:UnicodeString|正在編譯之方法的名稱。|  
|MethodBeingCompiledNameSignature|win:UnicodeString|正在編譯之方法的簽章。|  
|CallerNamespace|win:UnicodeString|JIT 編譯器正在嘗試產生其程式碼之方法的命名空間。|  
|CallerName|win:UnicodeString|編譯器正在嘗試產生其程式碼之方法的名稱。|  
|CallerNameSignature|win:UnicodeString|呼叫者的簽章。|  
|CalleeNamespace|win:UnicodeString|被呼叫者的命名空間。|  
|CalleeName|win:UnicodeString|編譯器嘗試要 tail 呼叫的方法 (而非產生呼叫)。|  
|CalleeNameSignature|win:UnicodeString|被呼叫者的簽章。|  
|TailPrefix|win:Boolean|Tail 呼叫的前置詞。|  
|TailCallType|win:UnicodeString|Tail 呼叫的類型。|  
|ClrInstanceID|win:UInt16|CLR 或 CoreCLR 執行個體的唯一 ID。|  
  
## <a name="see-also"></a>另請參閱

- [CLR ETW 事件](clr-etw-events.md)
