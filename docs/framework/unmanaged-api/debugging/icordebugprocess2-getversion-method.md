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
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="68549-102">ICorDebugProcess2::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="68549-102">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="68549-103">取得在此進程中執行之 common language runtime （CLR）的版本號碼。</span><span class="sxs-lookup"><span data-stu-id="68549-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="68549-104">語法</span><span class="sxs-lookup"><span data-stu-id="68549-104">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="68549-105">參數</span><span class="sxs-lookup"><span data-stu-id="68549-105">Parameters</span></span>

`version`\
<span data-ttu-id="68549-106">脫銷儲存執行時間版本號碼之 COR_VERSION 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="68549-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="68549-107">備註</span><span class="sxs-lookup"><span data-stu-id="68549-107">Remarks</span></span>

<span data-ttu-id="68549-108">`GetVersion`如果進程中沒有載入任何執行時間，則方法會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="68549-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="68549-109">需求</span><span class="sxs-lookup"><span data-stu-id="68549-109">Requirements</span></span>

<span data-ttu-id="68549-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="68549-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="68549-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68549-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="68549-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68549-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="68549-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68549-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
