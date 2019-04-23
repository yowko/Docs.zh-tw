---
title: ISymUnmanagedENCUpdate::UpdateMethodLines 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd1f101e2e9cf9baeb28290c7607ccab3d8d7440
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178915"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="b0307-102">ISymUnmanagedENCUpdate::UpdateMethodLines 方法</span><span class="sxs-lookup"><span data-stu-id="b0307-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="b0307-103">允許更新的方法，具有未重新編譯，但其中的行已獨立的行資訊。</span><span class="sxs-lookup"><span data-stu-id="b0307-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="b0307-104">允許每個陳述式的差異。</span><span class="sxs-lookup"><span data-stu-id="b0307-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0307-105">語法</span><span class="sxs-lookup"><span data-stu-id="b0307-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0307-106">參數</span><span class="sxs-lookup"><span data-stu-id="b0307-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="b0307-107">[in]方法的語彙基元的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b0307-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="b0307-108">[in]陣列`INT32`值，表示在方法中的每個序列點的差異。</span><span class="sxs-lookup"><span data-stu-id="b0307-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="b0307-109">[in]A`ULONG`包含大小`pDeltas`參數。</span><span class="sxs-lookup"><span data-stu-id="b0307-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0307-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="b0307-110">Return Value</span></span>  
 <span data-ttu-id="b0307-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0307-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0307-112">需求</span><span class="sxs-lookup"><span data-stu-id="b0307-112">Requirements</span></span>  
 <span data-ttu-id="b0307-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b0307-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0307-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0307-114">See also</span></span>

- [<span data-ttu-id="b0307-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="b0307-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
