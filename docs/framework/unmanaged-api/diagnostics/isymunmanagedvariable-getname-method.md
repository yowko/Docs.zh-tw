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
ms.openlocfilehash: 8298e7240052bdd859dbe414281d8e78984342e8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778250"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="7b639-102">ISymUnmanagedVariable::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="7b639-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="7b639-103">取得這個變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="7b639-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b639-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b639-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b639-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b639-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="7b639-106">[in]緩衝區的長度，`pcchName`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="7b639-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7b639-107">[out]指標`ULONG32`接收大小，以字元為單位，以存放的名稱，包括 null 終止的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7b639-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="7b639-108">[out]儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7b639-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7b639-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7b639-109">Return Value</span></span>  
 <span data-ttu-id="7b639-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b639-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b639-111">需求</span><span class="sxs-lookup"><span data-stu-id="7b639-111">Requirements</span></span>  
 <span data-ttu-id="7b639-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7b639-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b639-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b639-113">See also</span></span>

- [<span data-ttu-id="7b639-114">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="7b639-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
