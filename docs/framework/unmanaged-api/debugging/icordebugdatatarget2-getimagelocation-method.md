---
title: ICorDebugDataTarget2::GetImageLocation 方法
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7acf08262c73df00a96cfb5c244cdfc352e51ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080472"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="5fdd6-102">ICorDebugDataTarget2::GetImageLocation 方法</span><span class="sxs-lookup"><span data-stu-id="5fdd6-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="5fdd6-103">從模組的基底位址傳回模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fdd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fdd6-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fdd6-105">參數</span><span class="sxs-lookup"><span data-stu-id="5fdd6-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="5fdd6-106">[in]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5fdd6-107">[in] 要接收模組路徑之緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5fdd6-108">[out] 寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5fdd6-109">[out] 模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fdd6-110">備註</span><span class="sxs-lookup"><span data-stu-id="5fdd6-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fdd6-111">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fdd6-112">需求</span><span class="sxs-lookup"><span data-stu-id="5fdd6-112">Requirements</span></span>  
 <span data-ttu-id="5fdd6-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5fdd6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fdd6-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fdd6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fdd6-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fdd6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fdd6-116">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fdd6-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fdd6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fdd6-117">See also</span></span>

- [<span data-ttu-id="5fdd6-118">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="5fdd6-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="5fdd6-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5fdd6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
