---
title: ISymUnmanagedAsyncMethod::GetAsyncStepInfo 方法
ms.date: 03/30/2017
ms.assetid: 3ef5b4b8-4ac7-4906-849b-f932c5e3db07
ms.openlocfilehash: f9392dae4119e59b4eb0fdb87e2b334b32b77109
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707252"
---
# <a name="isymunmanagedasyncmethodgetasyncstepinfo-method"></a><span data-ttu-id="eb9d6-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="eb9d6-102">ISymUnmanagedAsyncMethod::GetAsyncStepInfo Method</span></span>

<span data-ttu-id="eb9d6-103">請參閱 [DefineAsyncStepInfo 方法](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)。</span><span class="sxs-lookup"><span data-stu-id="eb9d6-103">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb9d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb9d6-104">Syntax</span></span>  
  
```idl  
HRESULT GetAsyncStepInfo(    [in] ULONG32 cStepInfo,    [out] ULONG32 *pcStepInfo,    [in, size_is(cStepInfo)] ULONG32 yieldOffsets[],    [in, size_is(cStepInfo)] ULONG32 breakpointOffset[],    [in, size_is(cStepInfo)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb9d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb9d6-105">Parameters</span></span>  
  
|<span data-ttu-id="eb9d6-106">參數</span><span class="sxs-lookup"><span data-stu-id="eb9d6-106">Parameter</span></span>|<span data-ttu-id="eb9d6-107">描述</span><span class="sxs-lookup"><span data-stu-id="eb9d6-107">Description</span></span>|  
|---------------|-----------------|  
|`cStepInfo`||  
|`pcStepInfo`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="eb9d6-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="eb9d6-108">Return Value</span></span>  

 <span data-ttu-id="eb9d6-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="eb9d6-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb9d6-110">需求</span><span class="sxs-lookup"><span data-stu-id="eb9d6-110">Requirements</span></span>  

 <span data-ttu-id="eb9d6-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="eb9d6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb9d6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb9d6-112">See also</span></span>

- [<span data-ttu-id="eb9d6-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="eb9d6-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
