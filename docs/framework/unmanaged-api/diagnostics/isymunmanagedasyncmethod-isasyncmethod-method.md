---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod 方法
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 049f8e4d04498b70533134c01765af2d996d86dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499102"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a>ISymUnmanagedAsyncMethod::IsAsyncMethod 方法
檢查方法是否非同步處理的資訊。  
  
 如果此方法傳回`FALSE`則是在此介面中呼叫任何其他方法無效。 將所有傳回`E_UNEXPECTED`在此情況下。  
  
## <a name="syntax"></a>語法  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a>傳回值  
 傳回 `HRESULT`。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl CorSym.h  
  
## <a name="see-also"></a>另請參閱
- [ISymUnmanagedAsyncMethod 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
