---
title: ICorDebugMergedAssemblyRecord::GetSimpleName 方法
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 99ba27171e129e8725c3e0555a6991ef08b893da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178711"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="c5916-102">ICorDebugMergedAssemblyRecord::GetSimpleName 方法</span><span class="sxs-lookup"><span data-stu-id="c5916-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="c5916-103">取得組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="c5916-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5916-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5916-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5916-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5916-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c5916-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="c5916-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c5916-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="c5916-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="c5916-108">字元陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="c5916-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5916-109">備註</span><span class="sxs-lookup"><span data-stu-id="c5916-109">Remarks</span></span>  
 <span data-ttu-id="c5916-110">這個方法會擷取組件的簡單名稱 (例如 "System.Collections")，其中不含副檔名、版本、文化特性或公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c5916-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="c5916-111">它會對應至 Managed 程式碼中的 <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="c5916-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5916-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="c5916-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5916-113">需求</span><span class="sxs-lookup"><span data-stu-id="c5916-113">Requirements</span></span>  
 <span data-ttu-id="c5916-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5916-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5916-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5916-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5916-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5916-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5916-117">**.NET 框架版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5916-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5916-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5916-118">See also</span></span>

- [<span data-ttu-id="c5916-119">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="c5916-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="c5916-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c5916-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
