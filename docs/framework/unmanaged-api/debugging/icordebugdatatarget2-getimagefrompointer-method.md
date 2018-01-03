---
title: "ICorDebugDataTarget2::GetImageFromPointer 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfe25a90fb2084c1f58eff5b42e24b15decb0163
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="976b5-102">ICorDebugDataTarget2::GetImageFromPointer 方法</span><span class="sxs-lookup"><span data-stu-id="976b5-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="976b5-103">從模組中的位址傳回模組基底位址和大小。</span><span class="sxs-lookup"><span data-stu-id="976b5-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="976b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="976b5-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="976b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="976b5-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="976b5-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示在模組中的位址。</span><span class="sxs-lookup"><span data-stu-id="976b5-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="976b5-107">[out]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="976b5-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="976b5-108">模組大小的指標。</span><span class="sxs-lookup"><span data-stu-id="976b5-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="976b5-109">備註</span><span class="sxs-lookup"><span data-stu-id="976b5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="976b5-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="976b5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="976b5-111">需求</span><span class="sxs-lookup"><span data-stu-id="976b5-111">Requirements</span></span>  
 <span data-ttu-id="976b5-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="976b5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="976b5-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="976b5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="976b5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="976b5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="976b5-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="976b5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="976b5-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="976b5-116">See Also</span></span>  
 [<span data-ttu-id="976b5-117">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="976b5-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="976b5-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="976b5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
