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
ms.openlocfilehash: 51c06a7f8ea22fc73236131954781d8755274041
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789092"
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual 方法
由 common language runtime （CLR）資料存取服務呼叫，以在此目標進程的位址空間中配置記憶體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a>參數  
 `addr`  
 在`CLRDATA_ADDRESS` 值，指定要配置之記憶體的要求起始位址。  
  
 `size`  
 在要配置的記憶體大小（以位元組為單位）。  
  
 `typeFlags`  
 在控制記憶體配置的旗標。 請參閱 Win32 `VirtualAlloc` 函數。  
  
 `protectFlags`  
 在已配置記憶體的保護屬性。 請參閱 Win32 `VirtualAlloc` 函數。  
  
 `virt`  
 脫銷`CLRDATA_ADDRESS` 值的指標，指定配置之記憶體的實際起始位址。  
  
## <a name="remarks"></a>備註  
 `AllocVirtual` 方法可做為 Win32 `VirtualAlloc` 函數的邏輯包裝函式。  
  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl，ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRDataTarget2 介面](iclrdatatarget2-interface.md)
- [FreeVirtual 方法](iclrdatatarget2-freevirtual-method.md)
