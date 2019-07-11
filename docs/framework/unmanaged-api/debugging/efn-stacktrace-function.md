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
ms.openlocfilehash: 687fdd0735e6cb0f3a727c8a2da3cf33bffb6a39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738977"
---
# <a name="efnstacktrace-function"></a>\_EFN\_StackTrace 函式
提供 Managed 堆疊追蹤以及 `CONTEXT` 記錄之陣列的文字表示，再各提供一個文字表示給 Unmanaged 和 Managed 程式碼之間的每個轉換。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
  
## <a name="parameters"></a>參數  
 `Client`  
 [in]正在進行偵錯用戶端。  
  
 `wszTextOut`  
 [out]堆疊追蹤的文字表示。  
  
 `puiTextLength`  
 [out]中的字元數的指標`wszTextOut`。  
  
 `pTransitionContexts`  
 [out]轉換內容的陣列。  
  
 `puiTransitionContextCount`  
 [out]陣列中的轉換內容的數目指標。  
  
 `uiSizeOfContext`  
 [in]內容結構的大小。  
  
 `Flags`  
 [in]設定為 0 或 SOS_STACKTRACE_SHOWADDRESSES (0x01) 可顯示的 ebp 暫存器和 enter 堆疊指標 (ESP) 前面每`module!functionname`列。  
  
## <a name="remarks"></a>備註  
 `_EFN_StackTrace`結構可以從 WinDbg 的程式設計介面中呼叫。 使用參數，如下所示：  
  
- 如果`wszTextOut`為 null 並`puiTextLength`是不是 null，則函數會傳回字串長度，以`puiTextLength`。  
  
- 如果`wszTextOut`是不是 null，函式會儲存在文字`wszTextOut`最多所指示位置`puiTextLength`。 它會傳回成功有沒有足夠的空間中的緩衝區或傳回 E_OUTOFMEMORY 如果緩衝區不夠長。  
  
- 如果函式的轉換部分則會忽略`pTransitionContexts`和`puiTransitionContextCount`都是 null。 在此情況下，函式提供文字輸出只包含函式名稱的呼叫的端。  
  
- 如果`pTransitionContexts`為 null 並`puiTransitionContextCount`是不是 null，函式會傳回所需的內容中的項目數目`puiTransitionContextCount`。  
  
- 如果`pTransitionContexts`是不是 null，函式會將其視為一個陣列的長度為結構`puiTransitionContextCount`。 結構的大小由提供`uiSizeOfContext`，而且必須是大小[SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)或`CONTEXT`架構。  
  
- `wszTextOut` 會寫入格式如下：  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- 如果十六進位的位移 0x0，不會寫入位移。  
  
- 如果沒有任何 managed 程式碼的執行緒上目前內容中，函數會傳回 SOS_E_NOMANAGEDCODE。  
  
- `Flags`參數是 0 或若要查看每個前方的 EBP 和 ESP SOS_STACKTRACE_SHOWADDRESSES`module!functionname`列。 根據預設，它可以是 0。  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** SOS_Stacktrace.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯全域靜態函式](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
