---
title: ICorDebugReferenceValue::DereferenceStrong 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.DereferenceStrong
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::DereferenceStrong
helpviewer_keywords:
- ICorDebugReferenceValue::DereferenceStrong method [.NET Framework debugging]
- DereferenceStrong method [.NET Framework debugging]
ms.assetid: 723482d1-d1a1-410a-a405-677eeb04e2bf
topic_type:
- apiref
ms.openlocfilehash: e96d7c6fcb25a05deb7301e36b76b528a7982760
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376014"
---
# <a name="icordebugreferencevaluedereferencestrong-method"></a>ICorDebugReferenceValue::DereferenceStrong 方法
`DereferenceStrong`未執行。 請不要呼叫此方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DereferenceStrong (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
