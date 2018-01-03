---
title: "ICorDebugMergedAssemblyRecord::GetCulture 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7963d311707d12aa697c606605f9a34b6f65d1eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="5d1ee-102">ICorDebugMergedAssemblyRecord::GetCulture 方法</span><span class="sxs-lookup"><span data-stu-id="5d1ee-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="5d1ee-103">取得組件的文化特性名稱字串。</span><span class="sxs-lookup"><span data-stu-id="5d1ee-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d1ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d1ee-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d1ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d1ee-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="5d1ee-106">[in] `szCulture` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="5d1ee-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="5d1ee-107">[out] 實際上寫入 `szCulture` 緩衝區的字元數。</span><span class="sxs-lookup"><span data-stu-id="5d1ee-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="5d1ee-108">[out] 含有文化特性名稱的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="5d1ee-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d1ee-109">備註</span><span class="sxs-lookup"><span data-stu-id="5d1ee-109">Remarks</span></span>  
 <span data-ttu-id="5d1ee-110">文化特性名稱是唯一的字串，可識別文化特性，例如 "zh-TW" (適用於繁體中文文化特性) 或「中性」(適用於中性文化特性)。</span><span class="sxs-lookup"><span data-stu-id="5d1ee-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d1ee-111">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="5d1ee-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d1ee-112">需求</span><span class="sxs-lookup"><span data-stu-id="5d1ee-112">Requirements</span></span>  
 <span data-ttu-id="5d1ee-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d1ee-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d1ee-114">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d1ee-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d1ee-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d1ee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d1ee-116">**.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d1ee-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d1ee-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="5d1ee-117">See Also</span></span>  
 [<span data-ttu-id="5d1ee-118">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="5d1ee-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="5d1ee-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5d1ee-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
