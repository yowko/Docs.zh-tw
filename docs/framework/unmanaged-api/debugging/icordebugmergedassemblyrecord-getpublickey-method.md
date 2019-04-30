---
title: 'Icordebugmergedassemblyrecord:: Getpublickey 方法'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 610e46d5cb550a266c5558c49239d1818c1e85de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988113"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="ff6fb-102">Icordebugmergedassemblyrecord:: Getpublickey 方法</span><span class="sxs-lookup"><span data-stu-id="ff6fb-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="ff6fb-103">取得組件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="ff6fb-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff6fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff6fb-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff6fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff6fb-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="ff6fb-106">[in] `pbPublicKey` 陣列中的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="ff6fb-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="ff6fb-107">[out] 寫入 `pbPublicKey` 陣列之實際位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="ff6fb-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="ff6fb-108">[out] 包含組件公開金鑰之位元組陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="ff6fb-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff6fb-109">備註</span><span class="sxs-lookup"><span data-stu-id="ff6fb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff6fb-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="ff6fb-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff6fb-111">需求</span><span class="sxs-lookup"><span data-stu-id="ff6fb-111">Requirements</span></span>  
 <span data-ttu-id="ff6fb-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff6fb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff6fb-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff6fb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff6fb-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff6fb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff6fb-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff6fb-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6fb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff6fb-116">See also</span></span>

- [<span data-ttu-id="ff6fb-117">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="ff6fb-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="ff6fb-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ff6fb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
