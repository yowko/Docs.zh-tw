---
title: ICorDebugProcess2::GetVersion 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
ms.openlocfilehash: 391b848d3b3f66f6af6bf3adbefb6e94d526e748
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213500"
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion 方法

取得在此進程中執行之 common language runtime （CLR）的版本號碼。

## <a name="syntax"></a>語法

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a>參數

`version`\
脫銷儲存執行時間版本號碼之 COR_VERSION 結構的指標。

## <a name="remarks"></a>備註

`GetVersion`如果進程中沒有載入任何執行時間，則方法會傳回錯誤碼。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorDebug.idl、CorDebug.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
