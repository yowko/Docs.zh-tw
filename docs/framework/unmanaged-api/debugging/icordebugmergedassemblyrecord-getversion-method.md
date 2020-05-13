---
title: ICorDebugMergedAssemblyRecord::GetVersion 方法
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: cad71080c86e92beb318722db86011b09ce02e91
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207630"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="fbfa6-102">ICorDebugMergedAssemblyRecord::GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="fbfa6-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="fbfa6-103">取得組件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="fbfa6-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbfa6-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbfa6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbfa6-105">參數</span><span class="sxs-lookup"><span data-stu-id="fbfa6-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="fbfa6-106">[out] 主要版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="fbfa6-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="fbfa6-107">[out] 次要版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="fbfa6-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="fbfa6-108">[out] 組建編號的指標。</span><span class="sxs-lookup"><span data-stu-id="fbfa6-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="fbfa6-109">[out] 修訂編號的指標。</span><span class="sxs-lookup"><span data-stu-id="fbfa6-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbfa6-110">備註</span><span class="sxs-lookup"><span data-stu-id="fbfa6-110">Remarks</span></span>  
 <span data-ttu-id="fbfa6-111">如需組件版本號碼的相關資訊，請參閱 <xref:System.Version> 類別主題。</span><span class="sxs-lookup"><span data-stu-id="fbfa6-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbfa6-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="fbfa6-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbfa6-113">需求</span><span class="sxs-lookup"><span data-stu-id="fbfa6-113">Requirements</span></span>  
 <span data-ttu-id="fbfa6-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbfa6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbfa6-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fbfa6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fbfa6-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbfa6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbfa6-117">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbfa6-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbfa6-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbfa6-118">See also</span></span>

- [<span data-ttu-id="fbfa6-119">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="fbfa6-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="fbfa6-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="fbfa6-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
