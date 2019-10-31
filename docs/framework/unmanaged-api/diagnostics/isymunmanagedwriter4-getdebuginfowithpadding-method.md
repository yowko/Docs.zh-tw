---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 274bf79175bda9e880b1ef3cf8f125a017ad0734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121663"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="6994c-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法</span><span class="sxs-lookup"><span data-stu-id="6994c-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="6994c-103">函式與[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)相同，不同之處在于路徑字串會在結束的 null 字元之後以零填補，讓字串資料成為固定大小的 `MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="6994c-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="6994c-104">只有在路徑字串長度本身小於 `MAX_PATH`時，才會提供填補。</span><span class="sxs-lookup"><span data-stu-id="6994c-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="6994c-105">這可讓您更輕鬆地撰寫與 PE 檔案不同的工具。</span><span class="sxs-lookup"><span data-stu-id="6994c-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6994c-106">語法</span><span class="sxs-lookup"><span data-stu-id="6994c-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6994c-107">參數</span><span class="sxs-lookup"><span data-stu-id="6994c-107">Parameters</span></span>  
  
|<span data-ttu-id="6994c-108">參數</span><span class="sxs-lookup"><span data-stu-id="6994c-108">Parameter</span></span>|<span data-ttu-id="6994c-109">描述</span><span class="sxs-lookup"><span data-stu-id="6994c-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="6994c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="6994c-110">Return Value</span></span>  
 <span data-ttu-id="6994c-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="6994c-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6994c-112">需求</span><span class="sxs-lookup"><span data-stu-id="6994c-112">Requirements</span></span>  
 <span data-ttu-id="6994c-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6994c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6994c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="6994c-114">See also</span></span>

- [<span data-ttu-id="6994c-115">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="6994c-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
