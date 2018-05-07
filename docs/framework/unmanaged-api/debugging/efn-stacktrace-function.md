---
title: _EFN_StackTrace 函式
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39a249108d10e5dc382775378e2d6b84bba87356
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace 函式
提供 Managed 堆疊追蹤以及 `CONTEXT` 記錄之陣列的文字表示，再各提供一個文字表示給 Unmanaged 和 Managed 程式碼之間的每個轉換。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
#### <a name="parameters"></a>參數  
 `Client`  
 [in]用戶端進行偵錯。  
  
 `wszTextOut`  
 [out]堆疊追蹤的文字表示。  
  
 `puiTextLength`  
 [out]中的字元數的指標`wszTextOut`。  
  
 `pTransitionContexts`  
 [out]切換內容的陣列。  
  
 `puiTransitionContextCount`  
 [out]陣列中的轉換內容數目指標。  
  
 `uiSizeOfContext`  
 [in]內容結構的大小。  
  
 `Flags`  
 [in]若要顯示的 ebp 暫存器和 enter 堆疊指標 (ESP) 中的前面每個設定為 0 或 SOS_STACKTRACE_SHOWADDRESSES (0x01)`module!functionname`列。  
  
## <a name="remarks"></a>備註  
 `_EFN_StackTrace`結構可以呼叫從 WinDbg 程式設計介面。 使用參數，如下所示：  
  
-   如果`wszTextOut`為 null 和`puiTextLength`是不是 null，則函數會傳回的字串長度`puiTextLength`。  
  
-   如果`wszTextOut`是不是 null，函式將文字儲存在`wszTextOut`最多所指示位置`puiTextLength`。 它會傳回成功有沒有足夠的空間中的緩衝區或傳回 E_OUTOFMEMORY 如果緩衝區不夠長。  
  
-   如果函式的轉換部分則會忽略`pTransitionContexts`和`puiTransitionContextCount`都是 null。 在此情況下，函式提供函數名稱的文字輸出的呼叫的端。  
  
-   如果`pTransitionContexts`為 null 和`puiTransitionContextCount`是不是 null，此函數會傳回所需內容的項目數`puiTransitionContextCount`。  
  
-   如果`pTransitionContexts`是不是 null，函式會將它視為一個陣列的長度為結構`puiTransitionContextCount`。 結構大小由提供`uiSizeOfContext`，而且必須是大小[SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)或`CONTEXT`架構。  
  
-   `wszTextOut` 採用下列格式：  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   如果 0x0 十六進位的位移，不會寫入位移。  
  
-   如果沒有任何 managed 程式碼的執行緒上目前內容中，函數會傳回 SOS_E_NOMANAGEDCODE。  
  
-   `Flags`參數是 0 或若要查看 EBP 及 ESP 前面每個 SOS_STACKTRACE_SHOWADDRESSES`module!functionname`列。 根據預設，它可以是 0。  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
