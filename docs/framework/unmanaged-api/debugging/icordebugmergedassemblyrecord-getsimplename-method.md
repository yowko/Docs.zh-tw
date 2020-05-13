---
title: ICorDebugMergedAssemblyRecord::GetSimpleName 方法
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: f6c6682c8bb23143d308aa4f1a6887b28ea82fcd
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209704"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="4b8a0-102">ICorDebugMergedAssemblyRecord::GetSimpleName 方法</span><span class="sxs-lookup"><span data-stu-id="4b8a0-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="4b8a0-103">取得組件的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="4b8a0-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b8a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b8a0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b8a0-105">參數</span><span class="sxs-lookup"><span data-stu-id="4b8a0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="4b8a0-106">[in] `szName` 緩衝區中的字元數。</span><span class="sxs-lookup"><span data-stu-id="4b8a0-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4b8a0-107">[out] 實際寫入 `szName` 緩衝區的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="4b8a0-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="4b8a0-108">字元陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="4b8a0-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b8a0-109">備註</span><span class="sxs-lookup"><span data-stu-id="4b8a0-109">Remarks</span></span>  
 <span data-ttu-id="4b8a0-110">這個方法會擷取組件的簡單名稱 (例如 "System.Collections")，其中不含副檔名、版本、文化特性或公開金鑰語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4b8a0-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="4b8a0-111">它會對應至 Managed 程式碼中的 <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4b8a0-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b8a0-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="4b8a0-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b8a0-113">需求</span><span class="sxs-lookup"><span data-stu-id="4b8a0-113">Requirements</span></span>  
 <span data-ttu-id="4b8a0-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4b8a0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b8a0-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b8a0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b8a0-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b8a0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b8a0-117">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b8a0-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8a0-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b8a0-118">See also</span></span>

- [<span data-ttu-id="4b8a0-119">ICorDebugMergedAssemblyRecord 介面</span><span class="sxs-lookup"><span data-stu-id="4b8a0-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="4b8a0-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4b8a0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
