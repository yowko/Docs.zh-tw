---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08bf4022f7cd7f85ffe7939c16fd47950e131a77
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471520"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle 方法
取得指定已處理的記憶體回收的 managed 物件的參考指標。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `handle`  
 [in]具有記憶體回收控制代碼的 managed 物件指標。 這個值是<xref:System.IntPtr>物件，並可從擷取<xref:System.Runtime.InteropServices.GCHandle>針對受管理的物件。  
  
 `pOutValue`  
 [out]ICorDebugReferenceValue 物件，表示指定的受管理物件的參考的位址指標。  
  
## <a name="remarks"></a>備註  
 請勿混淆廢棄項目集合的參考值傳回的參考值。  
  
 傳回的參考作用如同一般的參考。 當在中斷點後繼續執行程式碼時，它會停用。 目標物件的存留期間不會受到參考值的存留期。  
  
> [!NOTE]
>  `GetReferenceValueFromGCHandle`方法不會驗證此控制代碼。 因此，`GetReferenceValueFromGCHandle`偵錯工具和正在偵錯，如果傳遞無效的控制代碼的程式碼，方法可能會毀損。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
