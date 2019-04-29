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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16e91a0c748e5b148e79dc73cf213b03c68c5021
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939720"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="22350-102">ISymUnmanagedENCUpdate::GetLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="22350-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="22350-103">取得本機變數。</span><span class="sxs-lookup"><span data-stu-id="22350-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22350-104">語法</span><span class="sxs-lookup"><span data-stu-id="22350-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22350-105">參數</span><span class="sxs-lookup"><span data-stu-id="22350-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="22350-106">[in]方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="22350-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="22350-107">[in]A`ULONG`表示的大小`rgLocals`參數。</span><span class="sxs-lookup"><span data-stu-id="22350-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="22350-108">[out]傳回的陣列[ISymUnmanagedVariable](isymunmanagedvariable-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="22350-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="22350-109">[out]指標`ULONG`接收大小的`rgLocals`包含區域變數所需要的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="22350-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22350-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="22350-110">Return Value</span></span>  
 <span data-ttu-id="22350-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="22350-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22350-112">需求</span><span class="sxs-lookup"><span data-stu-id="22350-112">Requirements</span></span>  
 <span data-ttu-id="22350-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="22350-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22350-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22350-114">See also</span></span>

- [<span data-ttu-id="22350-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="22350-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
