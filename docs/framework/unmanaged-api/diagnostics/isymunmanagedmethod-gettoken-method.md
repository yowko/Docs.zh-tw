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
ms.openlocfilehash: 76134a2447cbc40b5c97304540d9907648bc89e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719914"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="3f077-102">ISymUnmanagedMethod::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="3f077-102">ISymUnmanagedMethod::GetToken Method</span></span>

<span data-ttu-id="3f077-103">傳回這個方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3f077-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f077-104">語法</span><span class="sxs-lookup"><span data-stu-id="3f077-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f077-105">參數</span><span class="sxs-lookup"><span data-stu-id="3f077-105">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="3f077-106">擴展的指標， `mdMethodDef` 會接收包含中繼資料所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="3f077-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f077-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3f077-107">Return Value</span></span>  

 <span data-ttu-id="3f077-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3f077-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f077-109">需求</span><span class="sxs-lookup"><span data-stu-id="3f077-109">Requirements</span></span>  

 <span data-ttu-id="3f077-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3f077-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f077-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f077-111">See also</span></span>

- [<span data-ttu-id="3f077-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="3f077-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
