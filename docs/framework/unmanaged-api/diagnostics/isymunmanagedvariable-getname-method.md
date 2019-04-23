---
title: ISymUnmanagedVariable::GetName 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e863640e18ca64de084331327e0fa39468b54b60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176237"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="c1aa8-102">ISymUnmanagedVariable::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="c1aa8-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="c1aa8-103">取得這個變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1aa8-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1aa8-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1aa8-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1aa8-105">參數</span><span class="sxs-lookup"><span data-stu-id="c1aa8-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c1aa8-106">[in]緩衝區的長度，`pcchName`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="c1aa8-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c1aa8-107">[out]指標`ULONG32`接收大小，以字元為單位，以存放的名稱，包括 null 終止的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c1aa8-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="c1aa8-108">[out]儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c1aa8-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1aa8-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c1aa8-109">Return Value</span></span>  
 <span data-ttu-id="c1aa8-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="c1aa8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1aa8-111">需求</span><span class="sxs-lookup"><span data-stu-id="c1aa8-111">Requirements</span></span>  
 <span data-ttu-id="c1aa8-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c1aa8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1aa8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1aa8-113">See also</span></span>

- [<span data-ttu-id="c1aa8-114">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="c1aa8-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
