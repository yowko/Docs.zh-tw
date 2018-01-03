---
title: "ICorDebugMergedAssemblyRecord::GetPublicKey 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a47eb051cd9922b8640b8b612ff0ac5882b6a8ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="09ae4-102">ICorDebugMergedAssemblyRecord::GetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="09ae4-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="09ae4-103">取得組件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="09ae4-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ae4-104">語法</span><span class="sxs-lookup"><span data-stu-id="09ae4-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09ae4-105">參數</span><span class="sxs-lookup"><span data-stu-id="09ae4-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="09ae4-106">[in] `pbPublicKey` 陣列中的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="09ae4-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="09ae4-107">[out] 寫入 `pbPublicKey` 陣列之實際位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="09ae4-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="09ae4-108">[out] 包含組件公開金鑰之位元組陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="09ae4-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09ae4-109">備註</span><span class="sxs-lookup"><span data-stu-id="09ae4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09ae4-110">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="09ae4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ae4-111">需求</span><span class="sxs-lookup"><span data-stu-id="09ae4-111">Requirements</span></span>  
 <span data-ttu-id="09ae4-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09ae4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ae4-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09ae4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09ae4-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09ae4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09ae4-115">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ae4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ae4-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="09ae4-116">See Also</span></span>  
 [<span data-ttu-id="09ae4-117">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="09ae4-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="09ae4-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="09ae4-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
