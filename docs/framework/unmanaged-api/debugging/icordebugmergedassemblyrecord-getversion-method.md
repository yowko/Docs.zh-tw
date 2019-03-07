---
title: ICorDebugMergedAssemblyRecord::GetVersion 方法
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 762ac20c376f4161aa9c053f6e5213ba24c792ba
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499760"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="1c082-102">ICorDebugMergedAssemblyRecord::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="1c082-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="1c082-103">取得組件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="1c082-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c082-104">語法</span><span class="sxs-lookup"><span data-stu-id="1c082-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c082-105">參數</span><span class="sxs-lookup"><span data-stu-id="1c082-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="1c082-106">[out] 主要版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="1c082-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="1c082-107">[out] 次要版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="1c082-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="1c082-108">[out] 組建編號的指標。</span><span class="sxs-lookup"><span data-stu-id="1c082-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="1c082-109">[out] 修訂編號的指標。</span><span class="sxs-lookup"><span data-stu-id="1c082-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c082-110">備註</span><span class="sxs-lookup"><span data-stu-id="1c082-110">Remarks</span></span>  
 <span data-ttu-id="1c082-111">如需組件版本號碼的相關資訊，請參閱 <xref:System.Version> 類別主題。</span><span class="sxs-lookup"><span data-stu-id="1c082-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c082-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="1c082-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c082-113">需求</span><span class="sxs-lookup"><span data-stu-id="1c082-113">Requirements</span></span>  
 <span data-ttu-id="1c082-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c082-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c082-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c082-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c082-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c082-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c082-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c082-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c082-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c082-118">See also</span></span>
- [<span data-ttu-id="1c082-119">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="1c082-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="1c082-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1c082-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
