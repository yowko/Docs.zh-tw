---
title: ISymUnmanagedNamespace::GetNamespaces 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 039dab1b4ca86cb26de739e74b152f108f074c43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426168"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="75dda-102">ISymUnmanagedNamespace::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="75dda-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="75dda-103">取得這個命名空間的子系。</span><span class="sxs-lookup"><span data-stu-id="75dda-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75dda-104">語法</span><span class="sxs-lookup"><span data-stu-id="75dda-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75dda-105">參數</span><span class="sxs-lookup"><span data-stu-id="75dda-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="75dda-106">[in]A`ULONG32`指出的大小`namespaces`陣列。</span><span class="sxs-lookup"><span data-stu-id="75dda-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="75dda-107">[out]指標`ULONG32`接收以字元為單位，包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="75dda-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="75dda-108">[out]包含命名空間緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="75dda-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75dda-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="75dda-109">Return Value</span></span>  
 <span data-ttu-id="75dda-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="75dda-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75dda-111">需求</span><span class="sxs-lookup"><span data-stu-id="75dda-111">Requirements</span></span>  
 <span data-ttu-id="75dda-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="75dda-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75dda-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75dda-113">See Also</span></span>  
 [<span data-ttu-id="75dda-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="75dda-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
