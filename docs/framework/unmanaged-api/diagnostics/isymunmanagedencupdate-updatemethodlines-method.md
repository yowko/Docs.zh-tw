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
ms.openlocfilehash: 99499b8717f219616b6b368e6393b4b7ca0a79d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699582"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="77aa8-102">ISymUnmanagedENCUpdate::UpdateMethodLines 方法</span><span class="sxs-lookup"><span data-stu-id="77aa8-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>

<span data-ttu-id="77aa8-103">允許更新尚未重新編譯之方法的行資訊，但其行已獨立移動。</span><span class="sxs-lookup"><span data-stu-id="77aa8-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="77aa8-104">允許每個語句的差異。</span><span class="sxs-lookup"><span data-stu-id="77aa8-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77aa8-105">語法</span><span class="sxs-lookup"><span data-stu-id="77aa8-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77aa8-106">參數</span><span class="sxs-lookup"><span data-stu-id="77aa8-106">Parameters</span></span>  

 `mdMethodToken`  
 <span data-ttu-id="77aa8-107">在方法標記的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="77aa8-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="77aa8-108">在 `INT32` 值的陣列，表示方法中每個序列點的差異。</span><span class="sxs-lookup"><span data-stu-id="77aa8-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="77aa8-109">在， `ULONG` 包含參數的大小 `pDeltas` 。</span><span class="sxs-lookup"><span data-stu-id="77aa8-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77aa8-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="77aa8-110">Return Value</span></span>  

 <span data-ttu-id="77aa8-111">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="77aa8-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77aa8-112">需求</span><span class="sxs-lookup"><span data-stu-id="77aa8-112">Requirements</span></span>  

 <span data-ttu-id="77aa8-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="77aa8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77aa8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77aa8-114">See also</span></span>

- [<span data-ttu-id="77aa8-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="77aa8-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
