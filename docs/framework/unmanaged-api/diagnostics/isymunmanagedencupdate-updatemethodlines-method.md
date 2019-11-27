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
ms.openlocfilehash: 9aace77c4b3549c033433d4c305b07daa1f7a8c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448989"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="8db8e-102">ISymUnmanagedENCUpdate::UpdateMethodLines 方法</span><span class="sxs-lookup"><span data-stu-id="8db8e-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="8db8e-103">允許更新尚未重新編譯之方法的行資訊，但其行已獨立移動。</span><span class="sxs-lookup"><span data-stu-id="8db8e-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="8db8e-104">允許每個語句的差異。</span><span class="sxs-lookup"><span data-stu-id="8db8e-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8db8e-105">語法</span><span class="sxs-lookup"><span data-stu-id="8db8e-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8db8e-106">參數</span><span class="sxs-lookup"><span data-stu-id="8db8e-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="8db8e-107">在方法 token 的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8db8e-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="8db8e-108">在`INT32` 值的陣列，表示方法中每個序列點的差異。</span><span class="sxs-lookup"><span data-stu-id="8db8e-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="8db8e-109">在包含 `pDeltas` 參數大小的 `ULONG`。</span><span class="sxs-lookup"><span data-stu-id="8db8e-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8db8e-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="8db8e-110">Return Value</span></span>  
 <span data-ttu-id="8db8e-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8db8e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8db8e-112">需求</span><span class="sxs-lookup"><span data-stu-id="8db8e-112">Requirements</span></span>  
 <span data-ttu-id="8db8e-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8db8e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db8e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8db8e-114">See also</span></span>

- [<span data-ttu-id="8db8e-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="8db8e-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
