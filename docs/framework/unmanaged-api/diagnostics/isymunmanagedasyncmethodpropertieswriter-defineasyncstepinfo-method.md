---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ebd4bb1d674a27785ccbe5460a65fed764638ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435873"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="48a5b-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="48a5b-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="48a5b-103">定義一組非同步等候作業目前的方法。</span><span class="sxs-lookup"><span data-stu-id="48a5b-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="48a5b-104">每個 yield 位移符合 await 傳回的指示，用來識別潛在的利潤。</span><span class="sxs-lookup"><span data-stu-id="48a5b-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="48a5b-105">每個`breakpointMethod` / `breakpointOffset`組告訴我們其中非同步作業會繼續 （這可能是在不同的方法。</span><span class="sxs-lookup"><span data-stu-id="48a5b-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48a5b-106">語法</span><span class="sxs-lookup"><span data-stu-id="48a5b-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48a5b-107">參數</span><span class="sxs-lookup"><span data-stu-id="48a5b-107">Parameters</span></span>  
  
|<span data-ttu-id="48a5b-108">參數</span><span class="sxs-lookup"><span data-stu-id="48a5b-108">Parameter</span></span>|<span data-ttu-id="48a5b-109">描述</span><span class="sxs-lookup"><span data-stu-id="48a5b-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="48a5b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="48a5b-110">Return Value</span></span>  
 <span data-ttu-id="48a5b-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="48a5b-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48a5b-112">需求</span><span class="sxs-lookup"><span data-stu-id="48a5b-112">Requirements</span></span>  
 <span data-ttu-id="48a5b-113">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="48a5b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a5b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48a5b-114">See Also</span></span>  
 [<span data-ttu-id="48a5b-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="48a5b-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
