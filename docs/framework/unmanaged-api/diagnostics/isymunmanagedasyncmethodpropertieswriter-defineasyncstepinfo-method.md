---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: defd38798453c8b82ec23605d12d41e5b90aaabc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352902"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="fd047-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="fd047-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="fd047-103">定義一組非同步等候目前的方法中的作業。</span><span class="sxs-lookup"><span data-stu-id="fd047-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="fd047-104">每個 yield 位移符合 await 傳回指示，用來識別潛在的暫止。</span><span class="sxs-lookup"><span data-stu-id="fd047-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="fd047-105">每個`breakpointMethod` / `breakpointOffset`組告訴我們非同步作業會繼續這可能位於不同的方法。</span><span class="sxs-lookup"><span data-stu-id="fd047-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd047-106">語法</span><span class="sxs-lookup"><span data-stu-id="fd047-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd047-107">參數</span><span class="sxs-lookup"><span data-stu-id="fd047-107">Parameters</span></span>  
  
|<span data-ttu-id="fd047-108">參數</span><span class="sxs-lookup"><span data-stu-id="fd047-108">Parameter</span></span>|<span data-ttu-id="fd047-109">描述</span><span class="sxs-lookup"><span data-stu-id="fd047-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="fd047-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd047-110">Return Value</span></span>  
 <span data-ttu-id="fd047-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="fd047-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd047-112">需求</span><span class="sxs-lookup"><span data-stu-id="fd047-112">Requirements</span></span>  
 <span data-ttu-id="fd047-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fd047-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd047-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd047-114">See also</span></span>
- [<span data-ttu-id="fd047-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="fd047-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
