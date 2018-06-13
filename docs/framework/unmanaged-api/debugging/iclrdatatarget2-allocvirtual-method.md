---
title: ICLRDataTarget2::AllocVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46532592057f4fa6d9883d46dcef2f8f9e5f7228
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406340"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual 方法
呼叫由 common language runtime (CLR) 資料存取服務此目標處理序的位址空間中配置記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `addr`  
 [in]A`CLRDATA_ADDRESS`值，指定所要求的起始位址配置的記憶體。  
  
 `size`  
 [in]以位元組為單位配置的記憶體大小。  
  
 `typeFlags`  
 [in]控制記憶體配置的旗標。 請參閱 Win32`VirtualAlloc`函式。  
  
 `protectFlags`  
 [in]配置的記憶體保護屬性。 請參閱 Win32`VirtualAlloc`函式。  
  
 `virt`  
 [out]指標`CLRDATA_ADDRESS`值，指定配置的記憶體的實際開始位址。  
  
## <a name="remarks"></a>備註  
 `AllocVirtual`方法做為 Win32 的邏輯包裝函數`VirtualAlloc`函式。  
  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl、 ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRDataTarget2 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [FreeVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
