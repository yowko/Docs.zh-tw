---
title: ICorDebugAssembly3::EnumerateContainedAssemblies 方法
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080952"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="2c582-102">ICorDebugAssembly3::EnumerateContainedAssemblies 方法</span><span class="sxs-lookup"><span data-stu-id="2c582-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="2c582-103">取得這個組件所包含之組件的列舉值。</span><span class="sxs-lookup"><span data-stu-id="2c582-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c582-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c582-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c582-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c582-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="2c582-106">[out]ICorDebugAssemblyEnum 介面物件，列舉值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="2c582-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c582-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2c582-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="2c582-108">如果這個`ICorDebugAssembly3`物件是一個容器，否則`S_FALSE`，且列舉是空的。</span><span class="sxs-lookup"><span data-stu-id="2c582-108">if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c582-109">備註</span><span class="sxs-lookup"><span data-stu-id="2c582-109">Remarks</span></span>  
 <span data-ttu-id="2c582-110">需要符號才能列舉所包含的組件。</span><span class="sxs-lookup"><span data-stu-id="2c582-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="2c582-111">如果不存在，則這個方法會傳回 `S_FALSE` 並且不會提供任何有效的列舉值。</span><span class="sxs-lookup"><span data-stu-id="2c582-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c582-112">這個方法僅適用於 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="2c582-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c582-113">需求</span><span class="sxs-lookup"><span data-stu-id="2c582-113">Requirements</span></span>  
 <span data-ttu-id="2c582-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c582-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c582-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c582-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c582-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c582-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2c582-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="2c582-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2c582-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c582-118">See also</span></span>

- [<span data-ttu-id="2c582-119">ICorDebugAssembly3 介面</span><span class="sxs-lookup"><span data-stu-id="2c582-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="2c582-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2c582-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
