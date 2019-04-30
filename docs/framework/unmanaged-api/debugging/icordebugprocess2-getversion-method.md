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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07f3be81431201a4bb6011ea9b8f973061d3d101
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948862"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="71ff4-102">ICorDebugProcess2::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="71ff4-102">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="71ff4-103">取得 common language runtime (CLR) 在此程序中執行的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="71ff4-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="71ff4-104">語法</span><span class="sxs-lookup"><span data-stu-id="71ff4-104">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="71ff4-105">參數</span><span class="sxs-lookup"><span data-stu-id="71ff4-105">Parameters</span></span>

`version`\
<span data-ttu-id="71ff4-106">[out]儲存的執行階段的版本號碼 COR_VERSION 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="71ff4-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="71ff4-107">備註</span><span class="sxs-lookup"><span data-stu-id="71ff4-107">Remarks</span></span>

<span data-ttu-id="71ff4-108">`GetVersion`方法傳回錯誤碼，如果沒有執行階段已載入處理序中。</span><span class="sxs-lookup"><span data-stu-id="71ff4-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="71ff4-109">需求</span><span class="sxs-lookup"><span data-stu-id="71ff4-109">Requirements</span></span>

<span data-ttu-id="71ff4-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71ff4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="71ff4-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71ff4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="71ff4-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71ff4-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="71ff4-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71ff4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
