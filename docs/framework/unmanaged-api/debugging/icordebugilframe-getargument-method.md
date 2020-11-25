---
title: ICorDebugILFrame::GetArgument 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: d17179dbeb9564b16c0c95a43502a53a67d3b9b8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703157"
---
# <a name="icordebugilframegetargument-method"></a>ICorDebugILFrame::GetArgument 方法

取得此 Microsoft 中繼語言 (MSIL) 堆疊框架中指定之引數的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a>參數  

 `dwIndex`  
 在這個 MSIL 堆疊框架中的引數索引。  
  
 `ppValue`  
 [out] 代表擷取值之 ICorDebugValue 物件的位置指標。  
  
## <a name="remarks"></a>備註  

 `GetArgument`方法可以在 MSIL 堆疊框架中或在即時 (JIT) 編譯的框架中使用。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
