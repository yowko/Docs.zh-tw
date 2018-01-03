---
title: "ICorDebugMergedAssemblyRecord::GetVersion 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6a3865a82efec63aa85f4a0eee286bf8b79bd00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="693a2-102">ICorDebugMergedAssemblyRecord::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="693a2-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="693a2-103">取得組件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="693a2-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="693a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="693a2-104">Syntax</span></span>  
  
```  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="693a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="693a2-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="693a2-106">[out] 主要版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="693a2-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="693a2-107">[out] 次要版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="693a2-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="693a2-108">[out] 組建編號的指標。</span><span class="sxs-lookup"><span data-stu-id="693a2-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="693a2-109">[out] 修訂編號的指標。</span><span class="sxs-lookup"><span data-stu-id="693a2-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="693a2-110">備註</span><span class="sxs-lookup"><span data-stu-id="693a2-110">Remarks</span></span>  
 <span data-ttu-id="693a2-111">如需組件版本號碼的相關資訊，請參閱 <xref:System.Version> 類別主題。</span><span class="sxs-lookup"><span data-stu-id="693a2-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="693a2-112">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="693a2-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="693a2-113">需求</span><span class="sxs-lookup"><span data-stu-id="693a2-113">Requirements</span></span>  
 <span data-ttu-id="693a2-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="693a2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="693a2-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="693a2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="693a2-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="693a2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="693a2-117">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="693a2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693a2-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="693a2-118">See Also</span></span>  
 [<span data-ttu-id="693a2-119">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="693a2-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="693a2-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="693a2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
