---
title: ICorDebugSymbolProvider::GetCodeRange 方法
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: dbe042641cadae182efac30502a70631be359bbe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791645"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="82260-102">ICorDebugSymbolProvider::GetCodeRange 方法</span><span class="sxs-lookup"><span data-stu-id="82260-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="82260-103">提供方法中的相對虛擬位址 (RVA)，以取得方法起始位址和大小。</span><span class="sxs-lookup"><span data-stu-id="82260-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82260-104">語法</span><span class="sxs-lookup"><span data-stu-id="82260-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82260-105">參數</span><span class="sxs-lookup"><span data-stu-id="82260-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="82260-106">[in] 方法中的相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="82260-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="82260-107">[out] 方法的起始位址指標。</span><span class="sxs-lookup"><span data-stu-id="82260-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="82260-108">方法程式碼大小的指標 (方法的程式碼位元組數)。</span><span class="sxs-lookup"><span data-stu-id="82260-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82260-109">備註</span><span class="sxs-lookup"><span data-stu-id="82260-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82260-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="82260-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82260-111">需求</span><span class="sxs-lookup"><span data-stu-id="82260-111">Requirements</span></span>  
 <span data-ttu-id="82260-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82260-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82260-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82260-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82260-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82260-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82260-115">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82260-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82260-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="82260-116">See also</span></span>

- [<span data-ttu-id="82260-117">ICorDebugSymbolProvider 介面</span><span class="sxs-lookup"><span data-stu-id="82260-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="82260-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="82260-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
