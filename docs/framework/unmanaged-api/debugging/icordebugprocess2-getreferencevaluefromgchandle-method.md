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
ms.openlocfilehash: a5b9d57aab834ba3ca72a2ea8576ec70cd88eb77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713570"
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
 在具有垃圾收集控制碼之 managed 物件的指標。 這個值是一個 <xref:System.IntPtr> 物件，可以從 <xref:System.Runtime.InteropServices.GCHandle> managed 物件的取得。  
  
 `pOutValue`  
 擴展ICorDebugReferenceValue 物件位址的指標，該物件表示指定之 managed 物件的參考。  
  
## <a name="remarks"></a>備註  

 請勿將傳回的參考值與垃圾收集參考值混淆。  
  
 傳回的參考行為類似一般參考。 當程式碼執行在中斷點之後繼續時，就會停用此功能。 目標物件的存留期不會受到參考值的存留期所影響。  
  
> [!NOTE]
> `GetReferenceValueFromGCHandle`方法不會驗證控制碼。 因此， `GetReferenceValueFromGCHandle` 當傳遞的控制碼無效時，方法可能會損毀偵錯工具和正在進行的程式碼。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
