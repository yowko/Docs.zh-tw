---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 59e3a95a4d2573263600da60b4f852caa361138e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129203"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="a81a0-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="a81a0-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="a81a0-103">在目前方法中定義非同步 await 作業的群組。</span><span class="sxs-lookup"><span data-stu-id="a81a0-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="a81a0-104">每個產生位移都會符合 await 的傳回指示，以識別潛在的收益。</span><span class="sxs-lookup"><span data-stu-id="a81a0-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="a81a0-105">每個 `breakpointMethod`/`breakpointOffset` 組會告訴我們，非同步作業將繼續在不同方法中執行的位置。</span><span class="sxs-lookup"><span data-stu-id="a81a0-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a81a0-106">語法</span><span class="sxs-lookup"><span data-stu-id="a81a0-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a81a0-107">參數</span><span class="sxs-lookup"><span data-stu-id="a81a0-107">Parameters</span></span>  
  
|<span data-ttu-id="a81a0-108">參數</span><span class="sxs-lookup"><span data-stu-id="a81a0-108">Parameter</span></span>|<span data-ttu-id="a81a0-109">描述</span><span class="sxs-lookup"><span data-stu-id="a81a0-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="a81a0-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="a81a0-110">Return Value</span></span>  
 <span data-ttu-id="a81a0-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="a81a0-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a81a0-112">需求</span><span class="sxs-lookup"><span data-stu-id="a81a0-112">Requirements</span></span>  
 <span data-ttu-id="a81a0-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="a81a0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a81a0-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="a81a0-114">See also</span></span>

- [<span data-ttu-id="a81a0-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="a81a0-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)
