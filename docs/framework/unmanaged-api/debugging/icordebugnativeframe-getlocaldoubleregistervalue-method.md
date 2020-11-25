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
ms.openlocfilehash: 10f06fb04099ef947711bc7c5641e5a7f1fa36b7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695695"
---
# <a name="icordebugnativeframegetlocaldoubleregistervalue-method"></a>ICorDebugNativeFrame::GetLocalDoubleRegisterValue 方法

取得引數或區域變數的值，此變數會儲存在這個原生框架的兩個指定暫存器中。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetLocalDoubleRegisterValue (  
    [in] CorDebugRegister   highWordReg,  
    [in] CorDebugRegister   lowWordReg,  
    [in] ULONG              cbSigBlob,  
    [in] PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  

 `highWordReg`  
 在"CorDebugRegister" 列舉值，指定包含值的最高文字的暫存器。  
  
 `lowWordReg`  
 在 `CorDebugRegister` 列舉值，指定包含值低字的暫存器。  
  
 `cbSigBlob`  
 在整數，指定參數所參考之二進位中繼資料簽章的大小 `pvSigBlob` 。  
  
 `pvSigBlob`  
 在 `PCCOR_SIGNATURE` 指向值型別之二進位中繼資料簽章的值。  
  
 `ppValue`  
 擴展"ICorDebugValue" 物件位址的指標，代表儲存在指定暫存器中的已抓取值。  
  
## <a name="remarks"></a>備註  

 `GetLocalDoubleRegisterValue`方法可以在原生框架中使用，或在即時 (JIT) 編譯的框架中使用。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
