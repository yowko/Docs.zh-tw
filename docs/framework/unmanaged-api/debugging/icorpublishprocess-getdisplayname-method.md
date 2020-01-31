---
title: ICorPublishProcess::GetDisplayName 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
ms.openlocfilehash: 7f2e644340a2ec7fe807830422b927ce811ddcf9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790568"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="3c086-102">ICorPublishProcess::GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="3c086-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="3c086-103">取得此[ICorPublishProcess](icorpublishprocess-interface.md)所參考之進程的可執行檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="3c086-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c086-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c086-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c086-105">參數</span><span class="sxs-lookup"><span data-stu-id="3c086-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3c086-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="3c086-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3c086-107">脫銷`szName` 陣列中傳回的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="3c086-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="3c086-108">脫銷用來儲存可執行檔之名稱的陣列，包括完整路徑。</span><span class="sxs-lookup"><span data-stu-id="3c086-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="3c086-109">名稱是以 null 結束。</span><span class="sxs-lookup"><span data-stu-id="3c086-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c086-110">需求</span><span class="sxs-lookup"><span data-stu-id="3c086-110">Requirements</span></span>  
 <span data-ttu-id="3c086-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c086-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c086-112">**標頭：** CorPub .idl，CorPub。h</span><span class="sxs-lookup"><span data-stu-id="3c086-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3c086-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c086-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c086-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c086-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c086-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c086-115">See also</span></span>

- [<span data-ttu-id="3c086-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="3c086-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
