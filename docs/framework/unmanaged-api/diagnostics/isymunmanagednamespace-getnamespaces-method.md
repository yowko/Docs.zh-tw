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
ms.openlocfilehash: da2906187c02bbc7a35c937663e3fc7db1ebda13
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433893"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="8474a-102">ISymUnmanagedNamespace::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="8474a-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="8474a-103">取得這個命名空間的子系。</span><span class="sxs-lookup"><span data-stu-id="8474a-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8474a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8474a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8474a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8474a-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="8474a-106">在表示 `namespaces` 陣列大小的 `ULONG32`。</span><span class="sxs-lookup"><span data-stu-id="8474a-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="8474a-107">脫銷`ULONG32` 的指標，接收包含命名空間所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="8474a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="8474a-108">脫銷包含命名空間之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="8474a-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8474a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8474a-109">Return Value</span></span>  
 <span data-ttu-id="8474a-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8474a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8474a-111">需求</span><span class="sxs-lookup"><span data-stu-id="8474a-111">Requirements</span></span>  
 <span data-ttu-id="8474a-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8474a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8474a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8474a-113">See also</span></span>

- [<span data-ttu-id="8474a-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="8474a-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
