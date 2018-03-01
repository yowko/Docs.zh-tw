---
title: "ICorDebugILFrame::EnumerateArguments 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 474118abc505928d16737d792a619e75f1209344
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="074b4-102">ICorDebugILFrame::EnumerateArguments 方法</span><span class="sxs-lookup"><span data-stu-id="074b4-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="074b4-103">在這個框架中取得的引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="074b4-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="074b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="074b4-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="074b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="074b4-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="074b4-106">[out]ICorDebugValueEnum 物件是這個框架中的引數的列舉的位址指標。</span><span class="sxs-lookup"><span data-stu-id="074b4-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="074b4-107">備註</span><span class="sxs-lookup"><span data-stu-id="074b4-107">Remarks</span></span>  
 <span data-ttu-id="074b4-108">`EnumerateArguments`取得可以列出此 ICorDebugILFrame 物件所代表的呼叫框架中提供的引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="074b4-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="074b4-109">清單中會包含引數，會[vararg](/cpp/windows/vararg) （也就是引數數目可變） 的引數以及`vararg`。</span><span class="sxs-lookup"><span data-stu-id="074b4-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="074b4-110">需求</span><span class="sxs-lookup"><span data-stu-id="074b4-110">Requirements</span></span>  
 <span data-ttu-id="074b4-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="074b4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="074b4-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="074b4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="074b4-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="074b4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="074b4-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="074b4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
