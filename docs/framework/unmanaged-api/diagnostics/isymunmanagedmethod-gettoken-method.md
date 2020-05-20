---
title: ISymUnmanagedMethod::GetToken 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
ms.openlocfilehash: 0803f0b55f19b779f5b6608a9f8200d2b085b504
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615153"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="82171-102">ISymUnmanagedMethod::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="82171-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="82171-103">傳回這個方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="82171-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82171-104">語法</span><span class="sxs-lookup"><span data-stu-id="82171-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82171-105">參數</span><span class="sxs-lookup"><span data-stu-id="82171-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="82171-106">脫銷的指標， `mdMethodDef` 接收包含中繼資料所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="82171-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82171-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="82171-107">Return Value</span></span>  
 <span data-ttu-id="82171-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="82171-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82171-109">需求</span><span class="sxs-lookup"><span data-stu-id="82171-109">Requirements</span></span>  
 <span data-ttu-id="82171-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="82171-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82171-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82171-111">See also</span></span>

- [<span data-ttu-id="82171-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="82171-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
