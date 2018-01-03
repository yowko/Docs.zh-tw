---
title: "ISymUnmanagedENCUpdate::UpdateMethodLines 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.UpdateMethodLines
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e8ffecba62b6531c852e6510013ba56b9258b64
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="e9e76-102">ISymUnmanagedENCUpdate::UpdateMethodLines 方法</span><span class="sxs-lookup"><span data-stu-id="e9e76-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="e9e76-103">允許更新的方法，具有未重新編譯，但其中的行已獨立的行資訊。</span><span class="sxs-lookup"><span data-stu-id="e9e76-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="e9e76-104">允許每個陳述式的差異。</span><span class="sxs-lookup"><span data-stu-id="e9e76-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e76-105">語法</span><span class="sxs-lookup"><span data-stu-id="e9e76-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9e76-106">參數</span><span class="sxs-lookup"><span data-stu-id="e9e76-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="e9e76-107">[in]方法語彙基元的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e9e76-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="e9e76-108">[in]陣列`INT32`值，表示在方法中的每個序列點的差異。</span><span class="sxs-lookup"><span data-stu-id="e9e76-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="e9e76-109">[in]A`ULONG`包含大小`pDeltas`參數。</span><span class="sxs-lookup"><span data-stu-id="e9e76-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9e76-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="e9e76-110">Return Value</span></span>  
 <span data-ttu-id="e9e76-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9e76-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9e76-112">需求</span><span class="sxs-lookup"><span data-stu-id="e9e76-112">Requirements</span></span>  
 <span data-ttu-id="e9e76-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e9e76-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e76-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9e76-114">See Also</span></span>  
 [<span data-ttu-id="e9e76-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="e9e76-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
