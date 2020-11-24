---
title: 偵錯結構
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: bf84f8ddb1e86da3b9d0e4326584e61304640558
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676266"
---
# <a name="debugging-structures"></a>偵錯結構

本節說明偵錯 API 所使用的 Unmanaged 結構。

## <a name="in-this-section"></a>本節內容

 [CLRDATA_ADDRESS_RANGE 結構](clrdata-address-range-structure.md) 定義位址範圍。

 [CLRDATA_IL_ADDRESS_MAP 結構](clrdata-il-address-map-structure.md) 定義 IL 至位址對應

 [CLR_DEBUGGING_VERSION 結構](clr-debugging-version-structure.md) 將 common language runtime (CLR) 的產品版本定義為用於偵錯工具。

 [CodeChunkInfo 結構](codechunkinfo-structure.md) 代表記憶體中的單一程式碼區塊。

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) 包含執行緒框架中目前作用中之函式的相關資訊。

 [COR_ARRAY_LAYOUT 結構](cor-array-layout-structure.md) 提供記憶體中陣列物件配置的相關資訊。

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) 包含用來將 Microsoft 中繼語言 (MSIL) 程式碼對應至機器碼的位移。

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) 包含程式碼範圍的位移資訊。

 [COR_FIELD 結構](cor-field-structure.md) 提供物件中之欄位的相關資訊。

 [COR_GC_REFERENCE 結構](cor-gc-reference-structure.md) 包含要進行垃圾收集之物件的相關資訊。

 [COR_HEAPINFO 結構](cor-heapinfo-structure.md) 提供垃圾收集堆積的一般資訊，包括是否可列舉。

 [COR_HEAPOBJECT 結構](cor-heapobject-structure.md) 提供 managed 堆積上物件的相關資訊。

 [COR_IL_MAP](cor-il-map-structure.md) 指定函數的相對位移中的變更。

 [COR_SEGMENT 結構](cor-segment-structure.md) 包含 managed 堆積中之記憶體區域的相關資訊。

 [COR_TYPEID 結構](cor-typeid-structure.md) 包含類型識別碼。

 [COR_TYPE_LAYOUT 結構](cor-type-layout-structure.md) 提供記憶體中物件配置的相關資訊。

 [COR_VERSION](cor-version-structure.md) 儲存通用語言執行時間的標準四部分版本號碼。

 [CorDebugBlockingObject 結構](cordebugblockingobject-structure.md) 定義封鎖執行緒的物件，以及封鎖執行緒的原因。

 [CorDebugEHClause 結構](cordebugehclause-structure.md) 表示例外狀況處理 (EH) 子句，適用于一段指定的中繼語言 (IL) 。

 [CorDebugExceptionObjectStackFrame 結構](cordebugexceptionobjectstackframe-structure.md) 表示來自例外狀況物件的堆疊框架資訊。

 [CorDebugGuidToTypeMapping 結構](cordebugguidtotypemapping-structure.md) 將 Windows 執行階段 GUID 對應至其相對應的 [ICorDebugType](icordebugtype-interface.md) 物件。

 [DacpGetModuleAddress 結構](dacpgetmoduleaddress-structure.md) 定義模組位址要求的容器。

 [DacpMethodDescData 結構](dacpmethoddescdata-structure.md) 定義方法執行時間資訊的傳輸緩衝區。

 [Dacpmethoddata 結構](dacpmoduledata-structure.md) 定義模組執行時間資訊的傳輸緩衝區。

 [DacpReJitData 結構](dacprejitdata-structure.md) 定義指定分析工具檢測方法的基本資訊。

 [StackTrace_SimpleCoNtext 結構](stacktrace-simplecontext-structure.md) 提供可用於取代完整結構的簡單內容 `CONTEXT` 。

## <a name="related-sections"></a>相關章節

 [偵錯 Coclass](debugging-coclasses.md)

 [偵錯介面](debugging-interfaces.md)

 [偵錯全域靜態函式](debugging-global-static-functions.md)

 [偵錯列舉](debugging-enumerations.md)

 [偵錯](index.md)
