---
title: ICLRDataTarget::GetPointerSize 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 749ec14af7bffee87afbe5c0705a6ddf68da5fd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatargetgetpointersize-method"></a>ICLRDataTarget::GetPointerSize 方法
取得大小，以位元組為單位，目標處理序會使用與指標類型。 這個方法是由通用語言執行階段資料存取服務呼叫。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pointerSize`  
 [out]整數值，指定的大小，以位元組為單位，在目標處理序上之指標的指標。  
  
## <a name="remarks"></a>備註  
 此方法是由偵錯應用程式的作者來實作。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData.idl、 ClrData.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRDataTarget 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
