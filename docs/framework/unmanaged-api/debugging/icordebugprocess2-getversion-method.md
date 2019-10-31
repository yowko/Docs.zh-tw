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
ms.openlocfilehash: 5f618f6779f6931785bba18f70fb1ac9baf46753
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137197"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="5ef83-102">ICorDebugProcess2::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="5ef83-102">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="5ef83-103">取得在此進程中執行之 common language runtime （CLR）的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="5ef83-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ef83-104">語法</span><span class="sxs-lookup"><span data-stu-id="5ef83-104">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="5ef83-105">參數</span><span class="sxs-lookup"><span data-stu-id="5ef83-105">Parameters</span></span>

`version`\
<span data-ttu-id="5ef83-106">脫銷儲存執行時間版本號碼之 COR_VERSION 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="5ef83-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ef83-107">備註</span><span class="sxs-lookup"><span data-stu-id="5ef83-107">Remarks</span></span>

<span data-ttu-id="5ef83-108">如果進程中沒有載入任何執行時間，則 `GetVersion` 方法會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="5ef83-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ef83-109">需求</span><span class="sxs-lookup"><span data-stu-id="5ef83-109">Requirements</span></span>

<span data-ttu-id="5ef83-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5ef83-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5ef83-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ef83-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="5ef83-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ef83-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5ef83-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ef83-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
