---
title: "ICorDebugType2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType2
helpviewer_keywords: ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d44514586a2e91dad3486b6dc04c26946148885
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="46c21-102">ICorDebugType2 介面</span><span class="sxs-lookup"><span data-stu-id="46c21-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="46c21-103">擴充 ICorDebugType 介面擷取類型識別項的基底類型或複雜 （使用者定義） 的型別。</span><span class="sxs-lookup"><span data-stu-id="46c21-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46c21-104">方法</span><span class="sxs-lookup"><span data-stu-id="46c21-104">Methods</span></span>  
  
|<span data-ttu-id="46c21-105">方法</span><span class="sxs-lookup"><span data-stu-id="46c21-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="46c21-106">GetTypeID 方法</span><span class="sxs-lookup"><span data-stu-id="46c21-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="46c21-107">取得[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)此類型。</span><span class="sxs-lookup"><span data-stu-id="46c21-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46c21-108">備註</span><span class="sxs-lookup"><span data-stu-id="46c21-108">Remarks</span></span>  
 <span data-ttu-id="46c21-109">這個介面是 ICorDebugType 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="46c21-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46c21-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="46c21-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46c21-111">範例</span><span class="sxs-lookup"><span data-stu-id="46c21-111">Example</span></span>  
 <span data-ttu-id="46c21-112">下列程式碼片段說明如何使用[ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="46c21-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="46c21-113">需求</span><span class="sxs-lookup"><span data-stu-id="46c21-113">Requirements</span></span>  
 <span data-ttu-id="46c21-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46c21-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46c21-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46c21-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46c21-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46c21-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46c21-117">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46c21-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c21-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="46c21-118">See Also</span></span>  
 [<span data-ttu-id="46c21-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="46c21-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
