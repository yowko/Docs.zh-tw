---
title: ICorDebugILFrame::EnumerateArguments 方法
ms.date: 03/30/2017
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
ms.openlocfilehash: 9b0bc59b67b5d4b2184733f22616433bf33be616
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703222"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="56553-102">ICorDebugILFrame::EnumerateArguments 方法</span><span class="sxs-lookup"><span data-stu-id="56553-102">ICorDebugILFrame::EnumerateArguments Method</span></span>

<span data-ttu-id="56553-103">取得此框架中引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="56553-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56553-104">語法</span><span class="sxs-lookup"><span data-stu-id="56553-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56553-105">參數</span><span class="sxs-lookup"><span data-stu-id="56553-105">Parameters</span></span>  

 `ppValueEnum`  
 <span data-ttu-id="56553-106">擴展ICorDebugValueEnum 物件位址的指標，該物件為此框架中引數的列舉值。</span><span class="sxs-lookup"><span data-stu-id="56553-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56553-107">備註</span><span class="sxs-lookup"><span data-stu-id="56553-107">Remarks</span></span>  

 <span data-ttu-id="56553-108">`EnumerateArguments` 取得列舉值，這個列舉值可以列出這個 ICorDebugILFrame 物件所表示之呼叫框架中的可用引數。</span><span class="sxs-lookup"><span data-stu-id="56553-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="56553-109">此清單將包含 [vararg](/cpp/windows/vararg) (的引數，也就是) 的引數數目，以及非的引數 `vararg` 。</span><span class="sxs-lookup"><span data-stu-id="56553-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56553-110">需求</span><span class="sxs-lookup"><span data-stu-id="56553-110">Requirements</span></span>  

 <span data-ttu-id="56553-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56553-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56553-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56553-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56553-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56553-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56553-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56553-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
