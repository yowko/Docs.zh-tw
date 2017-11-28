---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e305ca13e419a40e9838a46a61fe7a435b7ce56
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="70609-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="70609-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="70609-103">定義一組非同步等候作業目前的方法。</span><span class="sxs-lookup"><span data-stu-id="70609-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="70609-104">每個 yield 位移符合 await 傳回的指示，用來識別潛在的利潤。</span><span class="sxs-lookup"><span data-stu-id="70609-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="70609-105">每個`breakpointMethod` / `breakpointOffset`組告訴我們其中非同步作業會繼續 （這可能是在不同的方法。</span><span class="sxs-lookup"><span data-stu-id="70609-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume,(which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70609-106">語法</span><span class="sxs-lookup"><span data-stu-id="70609-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70609-107">參數</span><span class="sxs-lookup"><span data-stu-id="70609-107">Parameters</span></span>  
  
|<span data-ttu-id="70609-108">參數</span><span class="sxs-lookup"><span data-stu-id="70609-108">Parameter</span></span>|<span data-ttu-id="70609-109">說明</span><span class="sxs-lookup"><span data-stu-id="70609-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="70609-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="70609-110">Return Value</span></span>  
 <span data-ttu-id="70609-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="70609-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70609-112">需求</span><span class="sxs-lookup"><span data-stu-id="70609-112">Requirements</span></span>  
 <span data-ttu-id="70609-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="70609-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70609-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70609-114">See Also</span></span>  
 [<span data-ttu-id="70609-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="70609-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
