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
ms.openlocfilehash: f7905b3ee83378ed1a27501b082dbfca01d6436c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688060"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="f4dbc-102">ISymUnmanagedENCUpdate::UpdateMethodLines 方法</span><span class="sxs-lookup"><span data-stu-id="f4dbc-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="f4dbc-103">允許更新的方法，具有未重新編譯，但其中的行已獨立的行資訊。</span><span class="sxs-lookup"><span data-stu-id="f4dbc-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="f4dbc-104">允許每個陳述式的差異。</span><span class="sxs-lookup"><span data-stu-id="f4dbc-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4dbc-105">語法</span><span class="sxs-lookup"><span data-stu-id="f4dbc-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4dbc-106">參數</span><span class="sxs-lookup"><span data-stu-id="f4dbc-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="f4dbc-107">[in]方法的語彙基元的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f4dbc-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="f4dbc-108">[in]陣列`INT32`值，表示在方法中的每個序列點的差異。</span><span class="sxs-lookup"><span data-stu-id="f4dbc-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="f4dbc-109">[in]A`ULONG`包含大小`pDeltas`參數。</span><span class="sxs-lookup"><span data-stu-id="f4dbc-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4dbc-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4dbc-110">Return Value</span></span>  
 <span data-ttu-id="f4dbc-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f4dbc-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4dbc-112">需求</span><span class="sxs-lookup"><span data-stu-id="f4dbc-112">Requirements</span></span>  
 <span data-ttu-id="f4dbc-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f4dbc-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4dbc-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4dbc-114">See also</span></span>
- [<span data-ttu-id="f4dbc-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="f4dbc-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
