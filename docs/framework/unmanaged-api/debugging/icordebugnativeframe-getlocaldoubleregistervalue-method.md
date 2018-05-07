---
title: ICorDebugNativeFrame::GetLocalDoubleRegisterValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalDoubleRegisterValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalDoubleRegisterValue method [.NET Framework debugging]
- GetLocalDoubleRegisterValue method [.NET Framework debugging]
ms.assetid: 1f838215-ac8a-434f-8ce6-03021d3098d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9de77f942a1b89b0ab11ef71229e491a5305cafc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a>ICorDebugNativeFrame::GetLocalDoubleRegisterValue 方法
取得引數或儲存在兩個指定的暫存器，針對這個原生框架中區域變數的值。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>參數  
 `highWordReg`  
 [in]指定的暫存器會包含值的 「 高 」 CorDebugRegister 」 列舉值。  
  
 `lowWordReg`  
 [in]值為`CorDebugRegister`列舉，指定包含低序位文字值的暫存器。  
  
 `cbSigBlob`  
 [in]整數，指定所參考的二進位中繼資料簽章的大小`pvSigBlob`參數。  
  
 `pvSigBlob`  
 [in]A`PCCOR_SIGNATURE`實值類型的二進位中繼資料簽章所指向的值。  
  
 `ppValue`  
 [out]代表儲存在指定的暫存器中的擷取的值的"ICorDebugValue 」 物件的位址指標。  
  
## <a name="remarks"></a>備註  
 `GetLocalDoubleRegisterValue`方法可以用在原生框架或在 just-in-time (JIT)-編譯框架。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 
