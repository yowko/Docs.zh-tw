---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法
ms.date: 03/30/2017
ms.assetid: f738a6ed-7cd9-4106-a5cd-355481e5771c
ms.openlocfilehash: 5a501cca16f06e7ccd5da9f65a213c6b24c1092c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441782"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefineasyncstepinfo-method"></a><span data-ttu-id="65f65-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="65f65-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineAsyncStepInfo Method</span></span>
<span data-ttu-id="65f65-103">在目前方法中定義非同步 await 作業的群組。</span><span class="sxs-lookup"><span data-stu-id="65f65-103">Define a group of async await operations in the current method.</span></span>  
  
 <span data-ttu-id="65f65-104">每個產生位移都會符合 await 的傳回指示，以識別潛在的收益。</span><span class="sxs-lookup"><span data-stu-id="65f65-104">Each yield offset matches an await's return instruction, identifying a potential yield.</span></span> <span data-ttu-id="65f65-105">每一組 `breakpointMethod` / `breakpointOffset` 都會告訴我們，非同步作業將繼續在不同方法中執行的位置。</span><span class="sxs-lookup"><span data-stu-id="65f65-105">Each `breakpointMethod`/`breakpointOffset` pair tells us where the asynchronous operation will resume which could be in a different method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65f65-106">語法</span><span class="sxs-lookup"><span data-stu-id="65f65-106">Syntax</span></span>  
  
```idl  
HRESULT DefineAsyncStepInfo(    [in] ULONG32 count,    [in, size_is(count)] ULONG32 yieldOffsets[],    [in, size_is(count)] ULONG32 breakpointOffset[],     [in, size_is(count)] mdToken breakpointMethod[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65f65-107">參數</span><span class="sxs-lookup"><span data-stu-id="65f65-107">Parameters</span></span>  
  
|<span data-ttu-id="65f65-108">參數</span><span class="sxs-lookup"><span data-stu-id="65f65-108">Parameter</span></span>|<span data-ttu-id="65f65-109">說明</span><span class="sxs-lookup"><span data-stu-id="65f65-109">Description</span></span>|  
|---------------|-----------------|  
|`count`||  
|`yieldOffsets`||  
|`breakpointOffset`||  
|`breakpointMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="65f65-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="65f65-110">Return Value</span></span>  
 <span data-ttu-id="65f65-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="65f65-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65f65-112">需求</span><span class="sxs-lookup"><span data-stu-id="65f65-112">Requirements</span></span>  
 <span data-ttu-id="65f65-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="65f65-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65f65-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65f65-114">See also</span></span>

- [<span data-ttu-id="65f65-115">ISymUnmanagedAsyncMethodPropertiesWriter 介面</span><span class="sxs-lookup"><span data-stu-id="65f65-115">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)
