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
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1871e6060303ad496e4edb7bed47b9d91ecf71f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="e20cf-102">ICorDebugMergedAssemblyRecord::GetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="e20cf-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="e20cf-103">取得組件的公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e20cf-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e20cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="e20cf-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,   
   [out] ULONG32 *pcbPublicKeyToken,   
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e20cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="e20cf-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="e20cf-106">[in] `pbPublicKeyToken` 陣列中的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="e20cf-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="e20cf-107">[out] 寫入 `pbPublicKeyToken` 陣列之實際位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="e20cf-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="e20cf-108">[out] 包含組件公開金鑰語彙基元之位元組陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="e20cf-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e20cf-109">備註</span><span class="sxs-lookup"><span data-stu-id="e20cf-109">Remarks</span></span>  
 <span data-ttu-id="e20cf-110">組件的公開金鑰語彙基元是其公開金鑰之 SHA1 雜湊的最後 8 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e20cf-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e20cf-111">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="e20cf-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e20cf-112">需求</span><span class="sxs-lookup"><span data-stu-id="e20cf-112">Requirements</span></span>  
 <span data-ttu-id="e20cf-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e20cf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e20cf-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e20cf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e20cf-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e20cf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e20cf-116">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e20cf-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e20cf-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="e20cf-117">See Also</span></span>  
 [<span data-ttu-id="e20cf-118">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="e20cf-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="e20cf-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e20cf-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
