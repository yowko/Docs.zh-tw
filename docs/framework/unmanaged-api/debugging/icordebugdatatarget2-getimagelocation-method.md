---
title: "ICorDebugDataTarget2::GetImageLocation 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d35e35ecf4dfc62575e42a45a861ad685f3f26b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="9bc9d-102">ICorDebugDataTarget2::GetImageLocation 方法</span><span class="sxs-lookup"><span data-stu-id="9bc9d-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="9bc9d-103">從模組的基底位址傳回模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="9bc9d-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc9d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9bc9d-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9bc9d-105">參數</span><span class="sxs-lookup"><span data-stu-id="9bc9d-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="9bc9d-106">[in]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="9bc9d-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9bc9d-107">[in] 要接收模組路徑之緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="9bc9d-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9bc9d-108">[out] 寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="9bc9d-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="9bc9d-109">[out] 模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="9bc9d-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bc9d-110">備註</span><span class="sxs-lookup"><span data-stu-id="9bc9d-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bc9d-111">這個方法僅適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="9bc9d-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bc9d-112">需求</span><span class="sxs-lookup"><span data-stu-id="9bc9d-112">Requirements</span></span>  
 <span data-ttu-id="9bc9d-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9bc9d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bc9d-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bc9d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bc9d-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bc9d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bc9d-116">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bc9d-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc9d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bc9d-117">See Also</span></span>  
 [<span data-ttu-id="9bc9d-118">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="9bc9d-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="9bc9d-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="9bc9d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
