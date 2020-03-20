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
ms.openlocfilehash: 77e801b048709949c384f642fc0d0ecb5d7eb512
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178391"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="1cff2-102">ICorPublishProcess::GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="1cff2-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="1cff2-103">獲取此[ICorPublishProcess](icorpublishprocess-interface.md)引用的進程的可執行檔的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="1cff2-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cff2-104">語法</span><span class="sxs-lookup"><span data-stu-id="1cff2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cff2-105">參數</span><span class="sxs-lookup"><span data-stu-id="1cff2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="1cff2-106">[in] `szName` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="1cff2-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1cff2-107">[出]`szName`陣列中返回的寬字元數。</span><span class="sxs-lookup"><span data-stu-id="1cff2-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="1cff2-108">[出]用於存儲可執行檔的名稱（包括完整路徑）的陣列。</span><span class="sxs-lookup"><span data-stu-id="1cff2-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="1cff2-109">名稱為 null 終止。</span><span class="sxs-lookup"><span data-stu-id="1cff2-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cff2-110">需求</span><span class="sxs-lookup"><span data-stu-id="1cff2-110">Requirements</span></span>  
 <span data-ttu-id="1cff2-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1cff2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cff2-112">**標題：** 科爾普布.idl， 科爾普布.h</span><span class="sxs-lookup"><span data-stu-id="1cff2-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="1cff2-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cff2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cff2-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cff2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cff2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cff2-115">See also</span></span>

- [<span data-ttu-id="1cff2-116">ICorPublishProcess 介面</span><span class="sxs-lookup"><span data-stu-id="1cff2-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
