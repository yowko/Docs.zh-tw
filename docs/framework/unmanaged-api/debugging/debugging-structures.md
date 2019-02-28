---
title: 偵錯結構
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50db519410b9513725c3dc10637421ba8bb37ec
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965224"
---
# <a name="debugging-structures"></a>偵錯結構

本節說明偵錯 API 所使用的 Unmanaged 結構。

## <a name="in-this-section"></a>本節內容
 [CLRDATA_ADDRESS_RANGE 結構](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md)定義的位址範圍。

 [CLRDATA_IL_ADDRESS_MAP 結構](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md)IL 定義位址對應

 [CLR_DEBUGGING_VERSION 結構](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)定義以進行偵錯的 common language runtime (CLR) 的產品版本。

 [CodeChunkInfo 結構](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)代表單一的記憶體中的程式碼區塊。

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md)包含目前使用中執行緒的框架的函式的相關資訊。

 [COR_ARRAY_LAYOUT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)提供記憶體中陣列物件配置資訊。

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md)包含原生程式碼的程式碼用來對應的 Microsoft intermediate language (MSIL) 位移。

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md)包含程式碼範圍的位移的資訊。

 [COR_FIELD 結構](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)提供物件中欄位的相關資訊。

 [COR_GC_REFERENCE 結構](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)包含要進行記憶體回收之物件的相關資訊。

 [COR_HEAPINFO 結構](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)提供記憶體回收堆積，包括其是否可列舉的一般資訊。

 [COR_HEAPOBJECT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)managed 堆積上提供物件的相關資訊。

 [COR_IL_MAP](cor-il-map-structure.md)函式相關位移中指定的變更。

 [COR_SEGMENT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)包含 managed 堆積中的記憶體區域的相關資訊。

 [COR_TYPEID 結構](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)包含型別識別項。

 [COR_TYPE_LAYOUT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)提供記憶體中物件配置資訊。

 [COR_VERSION](cor-version-structure.md)儲存通用語言執行平台的標準四部分版本號碼。

 [CorDebugBlockingObject 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)定義執行緒和執行緒封鎖的原因的原因封鎖的物件。

 [CorDebugEHClause 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)表示給定的中繼語言 (IL) 片段的例外狀況處理 (EH) 子句。

 [CorDebugExceptionObjectStackFrame 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)代表堆疊框架資訊的例外狀況物件。

 [CorDebugGuidToTypeMapping 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)Maps[!INCLUDE[wrt](../../../../includes/wrt-md.md)]至其相對應的 GUID [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)物件。

 [DacpGetModuleAddress 結構](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md)定義模組位址要求的容器。

 [DacpMethodDescData 結構](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md)定義方法的執行階段資訊的傳輸緩衝區。

 [DacpModuleData 結構](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md)定義模組的執行階段資訊的傳輸緩衝區。

 [DacpReJitData 結構](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md)定義指定的程式碼剖析工具檢測方法的基本資訊。

 [StackTrace_SimpleContext 結構](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)提供的簡單的內容，可用來代替完整`CONTEXT`結構。

## <a name="related-sections"></a>相關章節

 [偵錯 Coclass](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
