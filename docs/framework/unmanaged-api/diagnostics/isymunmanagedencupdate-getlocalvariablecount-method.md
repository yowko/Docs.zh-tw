---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f068b4cae3832802ab53404d35a5a30673cd967d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561851"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="93522-102">ISymUnmanagedENCUpdate::GetLocalVariableCount 方法</span><span class="sxs-lookup"><span data-stu-id="93522-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="93522-103">取得區域變數的數目。</span><span class="sxs-lookup"><span data-stu-id="93522-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93522-104">語法</span><span class="sxs-lookup"><span data-stu-id="93522-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93522-105">參數</span><span class="sxs-lookup"><span data-stu-id="93522-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="93522-106">[in]方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="93522-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="93522-107">[out]指標`ULONG32`接收大小，以字元為單位，以包含區域變數的數目所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="93522-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93522-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="93522-108">Return Value</span></span>  
 <span data-ttu-id="93522-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="93522-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93522-110">需求</span><span class="sxs-lookup"><span data-stu-id="93522-110">Requirements</span></span>  
 <span data-ttu-id="93522-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="93522-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93522-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93522-112">See also</span></span>
- [<span data-ttu-id="93522-113">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="93522-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
