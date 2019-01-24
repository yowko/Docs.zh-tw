---
title: ICorDebugNativeFrame::GetLocalRegisterValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterValue
helpviewer_keywords:
- GetLocalRegisterValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalRegisterValue method [.NET Framework debugging]
ms.assetid: 5ccb74f3-f891-430c-b70a-e370624edde2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9794a44bfb0bd1b4739689359832ba8500c6e2ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539606"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterValue 方法
取得引數或儲存在指定的暫存器，這個原生框架中區域變數的值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `reg`  
 [in]指定的暫存器包含值"CorDebugRegister 」 列舉值。  
  
 `cbSigBlob`  
 [in]整數，指定所參考的二進位中繼資料簽章大小`pvSigBlob`參數。  
  
 `pvSigBlob`  
 [in]A`PCCOR_SIGNATURE`指向的值類型的二進位中繼資料簽章的值。  
  
 `ppValue`  
 [out]「 ICorDebugValue 」 物件，代表儲存在指定的暫存器中擷取的值的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetLocalRegisterValue`方法可以用在原生框架或在 just-in-time (JIT)-編譯框架。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

