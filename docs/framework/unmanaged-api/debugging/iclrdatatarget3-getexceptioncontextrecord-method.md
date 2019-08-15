---
title: ICLRDataTarget3::GetExceptionContextRecord 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07065b15f449c2bcb84df7bbdcce65d61de007ee
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038340"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::GetExceptionContextRecord 方法
由通用語言執行平台 (CLR) 資料存取服務呼叫，用於擷取與目標處理序相關聯的內容記錄。 例如, 針對傾印目標, 這等同于透過`ExceptionParam`引數傳遞至 Windows Debug Help Library (DbgHelp) 中[MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump)函數的內容記錄。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>參數  
 `bufferSize`  
 [in] 輸入緩衝區大小 (位元組)。 這必須夠大，以容納內容記錄。  
  
 `bufferUsed`  
 [out] `ULONG32` 類型的指標，此類型會接收實際寫入緩衝區的位元組數目。  
  
 `buffer`  
 [out] 接收內容記錄複本之記憶體緩衝區的指標。 例外狀況記錄會以[內容](/windows/win32/api/winnt/ns-winnt-arm64_nt_context)類型的形式傳回。  
  
## <a name="return-value"></a>傳回值  
 如果成功，傳回值為 `S_OK`，如果失敗，則傳回失敗 `HRESULT` 程式碼。 `HRESULT` 程式碼可以包括 (但不限於) 下列項目：  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|`S_OK`|方法成功。 內容記錄已複製到輸出緩衝區。|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|沒有與目標相關聯的內容記錄。|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|輸入緩衝區大小不夠大，無法容納內容記錄。|  
  
## <a name="remarks"></a>備註  
 「內容」 ( [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) ) 是在 Windows SDK 所提供的標頭中定義的平臺特定結構。  
  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl, ClrData。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget3 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [GetExceptionRecord 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [GetExceptionThreadID 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
