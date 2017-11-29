---
title: "ICLRDataTarget3::GetExceptionRecord 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8c9ac4ecc0cffda4038129b1244b81501e9a1f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>ICLRDataTarget3::GetExceptionRecord 方法
由通用語言執行平台 (CLR) 資料存取服務呼叫，用於擷取與目標處理序相關聯的例外狀況記錄。 例如，針對傾印目標，這會是相當於透過例外狀況記錄`ExceptionParam`引數[MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) Windows Debug Help Library (DbgHelp) 中的函式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>參數  
 `bufferSize`  
 [in] 輸入緩衝區大小 (位元組)。 這必須等於`sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`。  
  
 `bufferUsed`  
 [out] `ULONG32` 類型的指標，此類型會接收實際寫入緩衝區的位元組數目。  
  
 `buffer`  
 [out] 接收例外狀況記錄複本之記憶體緩衝區的指標。 例外狀況記錄會當成[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)型別。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。 `HRESULT` 程式碼可以包括 (但不限於) 下列項目：  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|`S_OK`|方法成功。 例外狀況記錄已複製到輸出緩衝區。|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|沒有與目標相關聯的例外狀況記錄。|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|輸入緩衝區大小等於 `sizeof(MINIDUMP_EXCEPTION)`。|  
  
## <a name="remarks"></a>備註  
 [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)是 dbghelp.h 及 imagehlp.h 中 Windows SDK 中所定義的結構。  
  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl、 ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRDataTarget3 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [GetExceptionContextRecord 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [GetExceptionThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
