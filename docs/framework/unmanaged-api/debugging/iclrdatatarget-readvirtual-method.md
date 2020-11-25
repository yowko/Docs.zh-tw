---
title: ICLRDataTarget::ReadVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
ms.openlocfilehash: 3455397345451cc0c39cc98a0ea4374eab8350a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703373"
---
# <a name="iclrdatatargetreadvirtual-method"></a>ICLRDataTarget::ReadVirtual 方法

將資料從指定的虛擬記憶體位址讀入指定的緩衝區。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a>參數  

 `address`  
 在儲存虛擬記憶體位址的 CLRDATA_ADDRESS。  
  
 `buffer`  
 擴展接收資料之緩衝區的指標。  
  
 `bytesRequested`  
 在緩衝區的長度。  
  
 `bytesRead`  
 擴展傳回的位元組數目指標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl、ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRDataTarget 介面](iclrdatatarget-interface.md)
