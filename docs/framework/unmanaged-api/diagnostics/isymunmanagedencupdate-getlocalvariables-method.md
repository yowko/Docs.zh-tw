---
title: ISymUnmanagedENCUpdate::GetLocalVariables 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: 5e5bf097a4b1e366fff807595b22c4696a91cf43
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614548"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="92844-102">ISymUnmanagedENCUpdate::GetLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="92844-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="92844-103">取得本機變數。</span><span class="sxs-lookup"><span data-stu-id="92844-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92844-104">語法</span><span class="sxs-lookup"><span data-stu-id="92844-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92844-105">參數</span><span class="sxs-lookup"><span data-stu-id="92844-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="92844-106">在方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="92844-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="92844-107">在`ULONG`，表示參數的大小 `rgLocals` 。</span><span class="sxs-lookup"><span data-stu-id="92844-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="92844-108">脫銷[ISymUnmanagedVariable](isymunmanagedvariable-interface.md)實例的傳回陣列。</span><span class="sxs-lookup"><span data-stu-id="92844-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="92844-109">脫銷的指標 `ULONG` ，接收 `rgLocals` 包含區域變數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="92844-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92844-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="92844-110">Return Value</span></span>  
 <span data-ttu-id="92844-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="92844-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92844-112">需求</span><span class="sxs-lookup"><span data-stu-id="92844-112">Requirements</span></span>  
 <span data-ttu-id="92844-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="92844-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92844-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92844-114">See also</span></span>

- [<span data-ttu-id="92844-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="92844-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)
