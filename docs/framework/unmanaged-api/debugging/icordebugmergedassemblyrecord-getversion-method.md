---
title: ICorDebugMergedAssemblyRecord::GetVersion 方法
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36cf8647b3caafeaae2db3c2fd53471496e922fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109535"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="3409f-102">ICorDebugMergedAssemblyRecord::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="3409f-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="3409f-103">取得組件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="3409f-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3409f-104">語法</span><span class="sxs-lookup"><span data-stu-id="3409f-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3409f-105">參數</span><span class="sxs-lookup"><span data-stu-id="3409f-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="3409f-106">[out] 主要版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="3409f-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="3409f-107">[out] 次要版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="3409f-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="3409f-108">[out] 組建編號的指標。</span><span class="sxs-lookup"><span data-stu-id="3409f-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="3409f-109">[out] 修訂編號的指標。</span><span class="sxs-lookup"><span data-stu-id="3409f-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3409f-110">備註</span><span class="sxs-lookup"><span data-stu-id="3409f-110">Remarks</span></span>  
 <span data-ttu-id="3409f-111">如需組件版本號碼的相關資訊，請參閱 <xref:System.Version> 類別主題。</span><span class="sxs-lookup"><span data-stu-id="3409f-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3409f-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="3409f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3409f-113">需求</span><span class="sxs-lookup"><span data-stu-id="3409f-113">Requirements</span></span>  
 <span data-ttu-id="3409f-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3409f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3409f-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3409f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3409f-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3409f-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3409f-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="3409f-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3409f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3409f-118">See also</span></span>

- [<span data-ttu-id="3409f-119">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="3409f-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="3409f-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3409f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
