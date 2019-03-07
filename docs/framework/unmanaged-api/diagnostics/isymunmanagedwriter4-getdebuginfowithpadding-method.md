---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cfa82ae8bbc87a884887f826d947c2d3f2c5341
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473522"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="86d1b-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法</span><span class="sxs-lookup"><span data-stu-id="86d1b-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="86d1b-103">函數一樣[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)不同之處在於路徑字串以下列結束的 null 字元，讓字串資料的固定的大小的零來填補`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="86d1b-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="86d1b-104">如果路徑字串的長度本身是只指定填補小於`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="86d1b-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="86d1b-105">這可讓您更輕鬆地撰寫工具類型的差異 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="86d1b-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d1b-106">語法</span><span class="sxs-lookup"><span data-stu-id="86d1b-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d1b-107">參數</span><span class="sxs-lookup"><span data-stu-id="86d1b-107">Parameters</span></span>  
  
|<span data-ttu-id="86d1b-108">參數</span><span class="sxs-lookup"><span data-stu-id="86d1b-108">Parameter</span></span>|<span data-ttu-id="86d1b-109">描述</span><span class="sxs-lookup"><span data-stu-id="86d1b-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="86d1b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="86d1b-110">Return Value</span></span>  
 <span data-ttu-id="86d1b-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="86d1b-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86d1b-112">需求</span><span class="sxs-lookup"><span data-stu-id="86d1b-112">Requirements</span></span>  
 <span data-ttu-id="86d1b-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="86d1b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d1b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86d1b-114">See also</span></span>
- [<span data-ttu-id="86d1b-115">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="86d1b-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
