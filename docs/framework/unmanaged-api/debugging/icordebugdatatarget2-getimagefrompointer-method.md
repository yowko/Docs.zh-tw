---
title: ICorDebugDataTarget2::GetImageFromPointer 方法
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: f316ddb04cdaad2f528e8fac0a970ca6263ebd8f
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976469"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="c7046-102">ICorDebugDataTarget2::GetImageFromPointer 方法</span><span class="sxs-lookup"><span data-stu-id="c7046-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="c7046-103">從模組中的位址傳回模組基底位址和大小。</span><span class="sxs-lookup"><span data-stu-id="c7046-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7046-104">語法</span><span class="sxs-lookup"><span data-stu-id="c7046-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7046-105">參數</span><span class="sxs-lookup"><span data-stu-id="c7046-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="c7046-106">[CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md)值，表示模組中的位址。</span><span class="sxs-lookup"><span data-stu-id="c7046-106">A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="c7046-107">脫銷[CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md)值，表示模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="c7046-107">[out] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="c7046-108">模組大小的指標。</span><span class="sxs-lookup"><span data-stu-id="c7046-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7046-109">備註</span><span class="sxs-lookup"><span data-stu-id="c7046-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7046-110">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="c7046-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7046-111">需求</span><span class="sxs-lookup"><span data-stu-id="c7046-111">Requirements</span></span>  
 <span data-ttu-id="c7046-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7046-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7046-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7046-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7046-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7046-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7046-115">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7046-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7046-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7046-116">See also</span></span>

- [<span data-ttu-id="c7046-117">ICorDebugDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="c7046-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="c7046-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c7046-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
