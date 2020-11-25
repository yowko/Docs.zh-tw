---
title: ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法
ms.date: 03/30/2017
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
ms.openlocfilehash: f5bb5f069060baa9d553d72ccf6274bbc70c2575
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707200"
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a><span data-ttu-id="a2853-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset 方法</span><span class="sxs-lookup"><span data-stu-id="a2853-102">ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset Method</span></span>

<span data-ttu-id="a2853-103">請參閱 [DefineCatchHandlerILOffset 方法](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a2853-103">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2853-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2853-104">Syntax</span></span>  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2853-105">參數</span><span class="sxs-lookup"><span data-stu-id="a2853-105">Parameters</span></span>  
  
|<span data-ttu-id="a2853-106">參數</span><span class="sxs-lookup"><span data-stu-id="a2853-106">Parameter</span></span>|<span data-ttu-id="a2853-107">描述</span><span class="sxs-lookup"><span data-stu-id="a2853-107">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="a2853-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="a2853-108">Return Value</span></span>  

 <span data-ttu-id="a2853-109">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="a2853-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2853-110">需求</span><span class="sxs-lookup"><span data-stu-id="a2853-110">Requirements</span></span>  

 <span data-ttu-id="a2853-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="a2853-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2853-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2853-112">See also</span></span>

- [<span data-ttu-id="a2853-113">ISymUnmanagedAsyncMethod 介面</span><span class="sxs-lookup"><span data-stu-id="a2853-113">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
