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
ms.openlocfilehash: 23aa619d666f2e0b9eb67ab4cf8d4f92761865d3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415321"
---
# <a name="debugging-structures"></a>偵錯結構
本節說明偵錯 API 所使用的 Unmanaged 結構。  
  
## <a name="in-this-section"></a>本節內容  
 [CLR_DEBUGGING_VERSION 結構](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 定義用來偵錯之工具通用語言執行平台 (CLR) 的產品版本。  
  
 [CodeChunkInfo 結構 1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 代表記憶體中的單一程式碼區塊。  
  
 [CorDebugBlockingObject 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 定義封鎖執行緒的物件，以及封鎖執行緒的原因。  
  
 [CorDebugEHClause 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 代表給定之中繼語言 (IL) 片段的例外狀況處理 (EH) 子句。  
  
 [CorDebugExceptionObjectStackFrame 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 代表例外狀況物件所產生的堆疊框架資訊。  
  
 [CorDebugExceptionObjectStackFrame 結構](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Maps [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID 至其相對應[ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)物件。  
  
 COR_ACTIVE_FUNCTION  
 包含目前執行緒框架中正在作用的函式相關資訊。  
  
 [COR_ARRAY_LAYOUT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 提供記憶體中陣列物件配置的相關資訊。  
  
 COR_DEBUG_IL_TO_NATIVE_MAP  
 包含用來將 Microsoft 中繼語言 (MSIL) 程式碼對應至機器碼的位移。  
  
 COR_DEBUG_STEP_RANGE  
 包含程式碼範圍的位移資訊。  
  
 [COR_FIELD 結構](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 提供物件中欄位的相關資訊。  
  
 [COR_GC_REFERENCE 結構](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 包含要進行記憶體回收之物件的相關資訊。  
  
 [COR_HEAPINFO 結構](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 提供記憶體回收堆積的一般相關資訊，包括其是否可以列舉。  
  
 [COR_HEAPOBJECT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 提供 Managed 堆積上的物件相關資訊。  
  
 COR_IL_MAP  
 指定函式相關位移中的變更。  
  
 [COR_SEGMENT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 包含 Managed 堆積中記憶體區域的相關資訊。  
  
 [COR_TYPEID 結構](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 包含類型識別項。  
  
 [COR_TYPE_LAYOUT 結構](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 提供記憶體中物件配置的相關資訊。  
  
 COR_VERSION  
 儲存通用語言執行平台的標準四部分版本號碼。  
  
 [StackTrace_SimpleContext 結構](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 提供可用來代替完整 `CONTEXT` 結構的簡單內容。

 [CLRDATA_ADDRESS_RANGE 結構](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md)定義的位址範圍。
 
 [CLRDATA_IL_ADDRESS_MAP 結構](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md)IL 定義位址對應
 
 [DacpGetModuleAddress 結構](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md)定義模組位址要求的容器。

  
## <a name="related-sections"></a>相關章節  
 [偵錯 Coclass](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
