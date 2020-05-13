---
title: ICorDebugNativeFrame::GetIP 方法
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: 53576ca938074fb7e5974a96bb53a84cb6ed67ab
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213591"
---
# <a name="icordebugnativeframegetip-method"></a>ICorDebugNativeFrame::GetIP 方法
取得目前設定指令指標的原生程式碼位移位置。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a>參數  
 `pnOffset`  
 脫銷機器碼中位移位置的指標。  
  
## <a name="remarks"></a>備註  
 如果這個 "ICorDebugNativeFrame" 所代表的堆疊框架是作用中，則位移就是下一個要執行之指令的位址。 如果這個堆疊框架不在作用中，則位移是重新開機堆疊框架時，要執行的下一個指令的位址。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
