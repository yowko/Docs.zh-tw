---
title: 'Icordebugmergedassemblyrecord:: Getculture 方法'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0472a52d0893bfd487cd6daa6548ec1ce0c44a9b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762203"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="91b27-102">Icordebugmergedassemblyrecord:: Getculture 方法</span><span class="sxs-lookup"><span data-stu-id="91b27-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="91b27-103">取得組件的文化特性名稱字串。</span><span class="sxs-lookup"><span data-stu-id="91b27-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91b27-104">語法</span><span class="sxs-lookup"><span data-stu-id="91b27-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91b27-105">參數</span><span class="sxs-lookup"><span data-stu-id="91b27-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="91b27-106">[in] `szCulture` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="91b27-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="91b27-107">[out] 實際上寫入 `szCulture` 緩衝區的字元數。</span><span class="sxs-lookup"><span data-stu-id="91b27-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="91b27-108">[out] 含有文化特性名稱的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="91b27-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91b27-109">備註</span><span class="sxs-lookup"><span data-stu-id="91b27-109">Remarks</span></span>  
 <span data-ttu-id="91b27-110">文化特性名稱是唯一的字串，可識別文化特性，例如 "zh-TW" (適用於繁體中文文化特性) 或「中性」(適用於中性文化特性)。</span><span class="sxs-lookup"><span data-stu-id="91b27-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91b27-111">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="91b27-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91b27-112">需求</span><span class="sxs-lookup"><span data-stu-id="91b27-112">Requirements</span></span>  
 <span data-ttu-id="91b27-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91b27-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91b27-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91b27-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91b27-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91b27-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91b27-116">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91b27-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91b27-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91b27-117">See also</span></span>

- [<span data-ttu-id="91b27-118">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="91b27-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="91b27-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="91b27-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
