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
ms.openlocfilehash: 8eef973c4c054b704b7c3f798e5dc1aa455dda96
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707769"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="def54-102">ISymUnmanagedNamespace::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="def54-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>

<span data-ttu-id="def54-103">取得這個命名空間的子系。</span><span class="sxs-lookup"><span data-stu-id="def54-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="def54-104">語法</span><span class="sxs-lookup"><span data-stu-id="def54-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="def54-105">參數</span><span class="sxs-lookup"><span data-stu-id="def54-105">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="def54-106">在 `ULONG32` ，指出陣列的大小 `namespaces` 。</span><span class="sxs-lookup"><span data-stu-id="def54-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="def54-107">擴展的指標， `ULONG32` 會接收包含命名空間所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="def54-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="def54-108">擴展包含命名空間之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="def54-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="def54-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="def54-109">Return Value</span></span>  

 <span data-ttu-id="def54-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="def54-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="def54-111">需求</span><span class="sxs-lookup"><span data-stu-id="def54-111">Requirements</span></span>  

 <span data-ttu-id="def54-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="def54-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def54-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="def54-113">See also</span></span>

- [<span data-ttu-id="def54-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="def54-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
