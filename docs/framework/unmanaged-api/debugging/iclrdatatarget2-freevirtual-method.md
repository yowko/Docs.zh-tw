---
title: ICLRDataTarget2::FreeVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: 7eda9bfff6de6b386c16ad0a188931d9d3adcb93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793665"
---
# <a name="iclrdatatarget2freevirtual-method"></a>ICLRDataTarget2::FreeVirtual 方法
由 common language runtime （CLR）資料存取服務呼叫，以釋放先前在目標進程的位址空間中配置的記憶體。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `addr`  
 在`CLRDATA_ADDRESS` 值，指定要釋放之記憶體的起始位址。  
  
 `size`  
 在要釋放的記憶體大小（以位元組為單位）。  
  
 `typeFlags`  
 在控制記憶體釋放的旗標。 請參閱 Win32 `VirtualFree` 函數。  
  
## <a name="remarks"></a>備註  
 `FreeVirtual` 方法可做為 Win32 `VirtualFree` 函數的邏輯包裝函式。  
  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl，ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRDataTarget2 介面](iclrdatatarget2-interface.md)
- [AllocVirtual 方法](iclrdatatarget2-allocvirtual-method.md)
