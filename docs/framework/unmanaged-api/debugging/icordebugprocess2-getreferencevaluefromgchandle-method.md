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
ms.openlocfilehash: 21da325ee58df65ac449464f8292f2ba94d99338
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943300"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle 方法
取得具有垃圾收集控制碼之指定 managed 物件的參考指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>參數  
 `handle`  
 在具有垃圾收集控制碼之 managed 物件的指標。 這個值是<xref:System.IntPtr>物件, 而且可以從受管理物件<xref:System.Runtime.InteropServices.GCHandle>的抓取。  
  
 `pOutValue`  
 脫銷ICorDebugReferenceValue 物件位址的指標, 表示指定之 managed 物件的參考。  
  
## <a name="remarks"></a>備註  
 請勿混淆傳回的參考值與垃圾收集參考值。  
  
 傳回的參考與一般參考的行為類似。 當程式碼在中斷點之後繼續執行時, 就會停用它。 目標物件的存留期不會受到參考值的存留期影響。  
  
> [!NOTE]
> `GetReferenceValueFromGCHandle`方法不會驗證控制碼。 因此, 如果`GetReferenceValueFromGCHandle`傳遞了不正確控制碼, 方法可能會損毀偵錯工具和正在進行調試的程式碼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
