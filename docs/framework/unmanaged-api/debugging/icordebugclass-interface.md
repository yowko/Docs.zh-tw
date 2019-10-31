---
title: ICorDebugClass 介面
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: 5714597b5e5ca2936aad53217ae934684e75585c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125741"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="87d34-102">ICorDebugClass 介面</span><span class="sxs-lookup"><span data-stu-id="87d34-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="87d34-103">表示類型，可以是基本類型或複雜類型 (亦即，使用者定義類型)。</span><span class="sxs-lookup"><span data-stu-id="87d34-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="87d34-104">如果是泛型類型，則 `ICorDebugClass` 表示未具現化的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="87d34-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87d34-105">方法</span><span class="sxs-lookup"><span data-stu-id="87d34-105">Methods</span></span>  
  
|<span data-ttu-id="87d34-106">方法</span><span class="sxs-lookup"><span data-stu-id="87d34-106">Method</span></span>|<span data-ttu-id="87d34-107">描述</span><span class="sxs-lookup"><span data-stu-id="87d34-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87d34-108">GetModule 方法</span><span class="sxs-lookup"><span data-stu-id="87d34-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="87d34-109">取得定義此類別的模組。</span><span class="sxs-lookup"><span data-stu-id="87d34-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="87d34-110">GetStaticFieldValue 方法</span><span class="sxs-lookup"><span data-stu-id="87d34-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="87d34-111">取得指定靜態欄位的值。</span><span class="sxs-lookup"><span data-stu-id="87d34-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="87d34-112">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="87d34-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="87d34-113">取得這個類別的 `TypeDef` 中繼資料 token。</span><span class="sxs-lookup"><span data-stu-id="87d34-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87d34-114">備註</span><span class="sxs-lookup"><span data-stu-id="87d34-114">Remarks</span></span>  
 <span data-ttu-id="87d34-115">`ICorDebugClass` 介面代表未具現化的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="87d34-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="87d34-116">ICorDebugType 介面代表具現化的泛型型別。</span><span class="sxs-lookup"><span data-stu-id="87d34-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="87d34-117">例如，`Hashtable<K, V>` 會以 `ICorDebugClass`表示，而 `Hashtable<Int32, String>` 則會以 `ICorDebugType`表示。</span><span class="sxs-lookup"><span data-stu-id="87d34-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="87d34-118">非泛型型別是由 `ICorDebugClass` 和 `ICorDebugType`表示。</span><span class="sxs-lookup"><span data-stu-id="87d34-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="87d34-119">第二個介面是在 .NET Framework 版本2.0 中引進，以處理類型具現化。</span><span class="sxs-lookup"><span data-stu-id="87d34-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87d34-120">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="87d34-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d34-121">需求</span><span class="sxs-lookup"><span data-stu-id="87d34-121">Requirements</span></span>  
 <span data-ttu-id="87d34-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87d34-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d34-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87d34-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87d34-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87d34-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87d34-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d34-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d34-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="87d34-126">See also</span></span>

- [<span data-ttu-id="87d34-127">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="87d34-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
