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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ec6e25452a40ae67570badde8a883878d103f95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187393"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="0b85b-102">ISymUnmanagedMethod::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="0b85b-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="0b85b-103">傳回此方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0b85b-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b85b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b85b-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b85b-105">參數</span><span class="sxs-lookup"><span data-stu-id="0b85b-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="0b85b-106">[out]指標`mdMethodDef`接收大小，以字元為單位，以包含中繼資料所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0b85b-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b85b-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="0b85b-107">Return Value</span></span>  
 <span data-ttu-id="0b85b-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="0b85b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b85b-109">需求</span><span class="sxs-lookup"><span data-stu-id="0b85b-109">Requirements</span></span>  
 <span data-ttu-id="0b85b-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0b85b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b85b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b85b-111">See also</span></span>

- [<span data-ttu-id="0b85b-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="0b85b-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
