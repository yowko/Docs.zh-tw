---
title: ICorDebugNativeFrame::GetLocalMemoryValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetLocalMemoryValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type:
- apiref
ms.openlocfilehash: 4c4bfe6a797fc1476ff53a8f2db4f80debc41f6b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212434"
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a>ICorDebugNativeFrame::GetLocalMemoryValue 方法
取得在這個原生框架的指定記憶體位置中儲存之引數或區域變數的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 在`CORDB_ADDRESS`值，指定包含值的記憶體位置。  
  
 `cbSigBlob`  
 在整數，指定參數所參考的二進位中繼資料簽章大小 `pvSigBlob` 。  
  
 `pvSigBlob`  
 在`PCCOR_SIGNATURE`值，指向數值型別的二進位中繼資料簽章。  
  
 `ppValue`  
 脫銷"ICorDebugValue" 物件位址的指標，代表儲存在指定記憶體位置的已抓取值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
