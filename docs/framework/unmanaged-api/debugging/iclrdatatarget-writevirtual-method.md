---
title: ICLRDataTarget::WriteVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
ms.openlocfilehash: 4382d3c9f69df2808f8cd0aaf7f8eaf19bc9891e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793669"
---
# <a name="iclrdatatargetwritevirtual-method"></a>ICLRDataTarget::WriteVirtual 方法
將資料從指定的緩衝區寫入指定的虛擬記憶體位址。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]   
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 在儲存虛擬記憶體位址的 CLRDATA_ADDRESS。  
  
 `buffer`  
 在儲存要寫入之資料的緩衝區指標。  
  
 `bytesRequested`  
 在要寫入的位元組數目。  
  
 `bytesWritten`  
 脫銷寫入的實際位元組數的指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl，ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRDataTarget 介面](iclrdatatarget-interface.md)
