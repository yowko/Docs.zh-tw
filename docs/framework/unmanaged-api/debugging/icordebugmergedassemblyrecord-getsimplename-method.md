---
title: ICorDebugMergedAssemblyRecord::GetSimpleName 方法
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c5499b63e5201fbf42ece07f4f3eff52129e09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417488"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="efaa2-102">ICorDebugMergedAssemblyRecord::GetSimpleName 方法</span><span class="sxs-lookup"><span data-stu-id="efaa2-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="efaa2-103">取得組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="efaa2-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efaa2-104">語法</span><span class="sxs-lookup"><span data-stu-id="efaa2-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efaa2-105">參數</span><span class="sxs-lookup"><span data-stu-id="efaa2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="efaa2-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="efaa2-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="efaa2-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="efaa2-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="efaa2-108">字元陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="efaa2-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efaa2-109">備註</span><span class="sxs-lookup"><span data-stu-id="efaa2-109">Remarks</span></span>  
 <span data-ttu-id="efaa2-110">這個方法會擷取組件的簡單名稱 (例如 "System.Collections")，其中不含副檔名、版本、文化特性或公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="efaa2-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="efaa2-111">它會對應至 Managed 程式碼中的 <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="efaa2-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efaa2-112">本方法只適用於 .NET 原生。</span><span class="sxs-lookup"><span data-stu-id="efaa2-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efaa2-113">需求</span><span class="sxs-lookup"><span data-stu-id="efaa2-113">Requirements</span></span>  
 <span data-ttu-id="efaa2-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="efaa2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efaa2-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efaa2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efaa2-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efaa2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efaa2-117">**.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efaa2-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efaa2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efaa2-118">See Also</span></span>  
 [<span data-ttu-id="efaa2-119">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="efaa2-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="efaa2-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="efaa2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
