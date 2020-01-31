---
title: ICorDebugMergedAssemblyRecord::GetPublicKey 方法
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: c8c6e9adcb9d29f5e234dd1b8dfd351fac575301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793110"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="e1331-102">ICorDebugMergedAssemblyRecord::GetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="e1331-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="e1331-103">取得組件的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="e1331-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1331-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1331-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1331-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1331-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="e1331-106">[in] `pbPublicKey` 陣列中的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="e1331-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="e1331-107">[out] 寫入 `pbPublicKey` 陣列之實際位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="e1331-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="e1331-108">[out] 包含組件公開金鑰之位元組陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="e1331-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1331-109">備註</span><span class="sxs-lookup"><span data-stu-id="e1331-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1331-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="e1331-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1331-111">需求</span><span class="sxs-lookup"><span data-stu-id="e1331-111">Requirements</span></span>  
 <span data-ttu-id="e1331-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1331-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1331-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1331-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1331-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1331-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1331-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1331-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1331-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="e1331-116">See also</span></span>

- [<span data-ttu-id="e1331-117">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="e1331-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="e1331-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e1331-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
