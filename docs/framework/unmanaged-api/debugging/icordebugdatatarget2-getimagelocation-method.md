---
title: ICorDebugDataTarget2::GetImageLocation 方法
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: 185b6a4979491a323f6eb15ab08a06f87fabc8d3
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976456"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="bda29-102">ICorDebugDataTarget2::GetImageLocation 方法</span><span class="sxs-lookup"><span data-stu-id="bda29-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="bda29-103">從模組的基底位址傳回模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="bda29-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bda29-104">語法</span><span class="sxs-lookup"><span data-stu-id="bda29-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bda29-105">參數</span><span class="sxs-lookup"><span data-stu-id="bda29-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="bda29-106">在[CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="bda29-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bda29-107">[in] 要接收模組路徑之緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="bda29-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="bda29-108">[out] 寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="bda29-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="bda29-109">[out] 模組的路徑。</span><span class="sxs-lookup"><span data-stu-id="bda29-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bda29-110">備註</span><span class="sxs-lookup"><span data-stu-id="bda29-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bda29-111">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="bda29-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bda29-112">需求</span><span class="sxs-lookup"><span data-stu-id="bda29-112">Requirements</span></span>  
 <span data-ttu-id="bda29-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bda29-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bda29-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bda29-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bda29-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bda29-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bda29-116">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bda29-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda29-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bda29-117">See also</span></span>

- [<span data-ttu-id="bda29-118">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="bda29-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="bda29-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bda29-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
