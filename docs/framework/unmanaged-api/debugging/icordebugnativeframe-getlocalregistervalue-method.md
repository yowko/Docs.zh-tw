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
ms.openlocfilehash: 97d79f70097bef7768316907887cea2c38dd81e1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212824"
---
# <a name="icordebugnativeframegetlocalregistervalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterValue 方法
取得儲存在這個原生框架之指定暫存器中的引數或區域變數的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLocalRegisterValue (  
    [in]  CorDebugRegister   reg,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `reg`  
 在"CorDebugRegister" 列舉的值，指定包含值的暫存器。  
  
 `cbSigBlob`  
 在整數，指定參數所參考的二進位中繼資料簽章大小 `pvSigBlob` 。  
  
 `pvSigBlob`  
 在`PCCOR_SIGNATURE`值，指向數值型別的二進位中繼資料簽章。  
  
 `ppValue`  
 脫銷"ICorDebugValue" 物件位址的指標，代表儲存在指定之暫存器中的已抓取值。  
  
## <a name="remarks"></a>備註  
 `GetLocalRegisterValue`方法可以在原生框架或即時（JIT）編譯的框架中使用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
