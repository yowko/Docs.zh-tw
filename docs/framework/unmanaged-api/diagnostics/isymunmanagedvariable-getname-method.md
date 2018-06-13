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
ms.openlocfilehash: 9abbfa14777c5a5f5a77fa91db0fbafee095ba9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429233"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="9d2b7-102">ISymUnmanagedVariable::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="9d2b7-102">ISymUnmanagedVariable::GetName Method</span></span>
<span data-ttu-id="9d2b7-103">取得這個變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="9d2b7-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d2b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d2b7-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d2b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d2b7-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9d2b7-106">[in]緩衝區的長度，`pcchName`參數所指向。</span><span class="sxs-lookup"><span data-stu-id="9d2b7-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9d2b7-107">[out]指標`ULONG32`接收以字元為單位，以包含檔案的名稱，包括 null 結束所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="9d2b7-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="9d2b7-108">[out]儲存名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9d2b7-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d2b7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9d2b7-109">Return Value</span></span>  
 <span data-ttu-id="9d2b7-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d2b7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d2b7-111">需求</span><span class="sxs-lookup"><span data-stu-id="9d2b7-111">Requirements</span></span>  
 <span data-ttu-id="9d2b7-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9d2b7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2b7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d2b7-113">See Also</span></span>  
 [<span data-ttu-id="9d2b7-114">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="9d2b7-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
