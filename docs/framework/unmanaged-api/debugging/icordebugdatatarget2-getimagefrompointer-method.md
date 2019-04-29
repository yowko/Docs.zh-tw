---
title: ICorDebugDataTarget2::GetImageFromPointer 方法
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dab9183075f563f52a4fc982eda5cb172556554
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782976"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="f7229-102">ICorDebugDataTarget2::GetImageFromPointer 方法</span><span class="sxs-lookup"><span data-stu-id="f7229-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="f7229-103">從模組中的位址傳回模組基底位址和大小。</span><span class="sxs-lookup"><span data-stu-id="f7229-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7229-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7229-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7229-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7229-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="f7229-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組中的位址。</span><span class="sxs-lookup"><span data-stu-id="f7229-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="f7229-107">[out]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="f7229-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="f7229-108">模組大小的指標。</span><span class="sxs-lookup"><span data-stu-id="f7229-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7229-109">備註</span><span class="sxs-lookup"><span data-stu-id="f7229-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7229-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="f7229-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7229-111">需求</span><span class="sxs-lookup"><span data-stu-id="f7229-111">Requirements</span></span>  
 <span data-ttu-id="f7229-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7229-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7229-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7229-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7229-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7229-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7229-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7229-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7229-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7229-116">See also</span></span>

- [<span data-ttu-id="f7229-117">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="f7229-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="f7229-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f7229-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
