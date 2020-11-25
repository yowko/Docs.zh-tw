---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: f8c77e44183fd92704aa91ca1cfd7e3fa68aa27f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719615"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="2d8ca-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="2d8ca-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>

<span data-ttu-id="2d8ca-103">在目前方法中定義非同步 await 作業的群組。</span><span class="sxs-lookup"><span data-stu-id="2d8ca-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="2d8ca-104">每個 yield 位移都符合 await 的傳回指令，以識別潛在的 yield。</span><span class="sxs-lookup"><span data-stu-id="2d8ca-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="2d8ca-105">每一組 `breakpointMethod` / `breakpointOffset` 都會告訴我們，非同步作業會在不同的方法中繼續執行。</span><span class="sxs-lookup"><span data-stu-id="2d8ca-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d8ca-106">語法</span><span class="sxs-lookup"><span data-stu-id="2d8ca-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d8ca-107">參數</span><span class="sxs-lookup"><span data-stu-id="2d8ca-107">Parameters</span></span>  
  
|<span data-ttu-id="2d8ca-108">參數</span><span class="sxs-lookup"><span data-stu-id="2d8ca-108">Parameter</span></span>|<span data-ttu-id="2d8ca-109">描述</span><span class="sxs-lookup"><span data-stu-id="2d8ca-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="2d8ca-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d8ca-110">Return Value</span></span>  

 <span data-ttu-id="2d8ca-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="2d8ca-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d8ca-112">需求</span><span class="sxs-lookup"><span data-stu-id="2d8ca-112">Requirements</span></span>  

 <span data-ttu-id="2d8ca-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="2d8ca-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d8ca-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d8ca-114">See also</span></span>

- [<span data-ttu-id="2d8ca-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="2d8ca-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
