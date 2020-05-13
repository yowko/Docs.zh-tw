---
title: ICorDebugNativeFrame::GetLocalRegisterMemoryValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalRegisterMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue
helpviewer_keywords:
- ICorDebugNativeFrame::GetLocalRegisterMemoryValue method [.NET Framework debugging]
- GetLocalRegisterMemoryValue method [.NET Framework debugging]
ms.assetid: d350f69d-9aff-4f5a-8301-daea22dee2da
topic_type:
- apiref
ms.openlocfilehash: f16150ad7d9ecec4b4aceee5c9266e9a7859f1cb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213292"
---
# <a name="icordebugnativeframegetlocalregistermemoryvalue-method"></a>ICorDebugNativeFrame::GetLocalRegisterMemoryValue 方法
取得引數或區域變數的值，其中的低字和高單字會分別儲存在記憶體位置，並為這個原生框架指定 register。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLocalRegisterMemoryValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CORDB_ADDRESS      lowWordAddress,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `highWordReg`  
 在"CorDebugRegister" 列舉的值，指定包含值高字的暫存器。  
  
 `lowWordAddress`  
 在`CORDB_ADDRESS`值，指定包含值之低字的記憶體位置。  
  
 `cbSigBlob`  
 在整數，指定參數所參考的二進位中繼資料簽章大小 `pvSigBlob` 。  
  
 `pvSigBlob`  
 在`PCCOR_SIGNATURE`值，指向數值型別的二進位中繼資料簽章。  
  
 `ppValue`  
 脫銷"ICorDebugValue" 物件位址的指標，代表儲存在指定的暫存器和記憶體位置的已抓取值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
