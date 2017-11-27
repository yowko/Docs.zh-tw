---
title: "ICorDebugILFrame::EnumerateArguments 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.EnumerateArguments
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf345f3fa684b57a33e3452916535b1cd7db3c8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="8d81b-102">ICorDebugILFrame::EnumerateArguments 方法</span><span class="sxs-lookup"><span data-stu-id="8d81b-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="8d81b-103">在這個框架中取得的引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="8d81b-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d81b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d81b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d81b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d81b-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="8d81b-106">[out]ICorDebugValueEnum 物件是這個框架中的引數的列舉的位址指標。</span><span class="sxs-lookup"><span data-stu-id="8d81b-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d81b-107">備註</span><span class="sxs-lookup"><span data-stu-id="8d81b-107">Remarks</span></span>  
 <span data-ttu-id="8d81b-108">`EnumerateArguments`取得可以列出此 ICorDebugILFrame 物件所代表的呼叫框架中提供的引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="8d81b-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="8d81b-109">清單中會包含引數，會[vararg](/cpp/windows/vararg) （也就是引數數目可變） 的引數以及`vararg`。</span><span class="sxs-lookup"><span data-stu-id="8d81b-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d81b-110">需求</span><span class="sxs-lookup"><span data-stu-id="8d81b-110">Requirements</span></span>  
 <span data-ttu-id="8d81b-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d81b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d81b-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d81b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d81b-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d81b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d81b-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d81b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
