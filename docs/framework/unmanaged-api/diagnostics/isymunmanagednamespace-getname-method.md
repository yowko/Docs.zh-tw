---
title: ISymUnmanagedNamespace::GetName 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: 84b2f1226c84713483499c7ff777838058cb0f95
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615107"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="6258c-102">ISymUnmanagedNamespace::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="6258c-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="6258c-103">取得這個命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="6258c-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6258c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6258c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6258c-105">參數</span><span class="sxs-lookup"><span data-stu-id="6258c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6258c-106">在`ULONG32`，表示緩衝區的大小 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="6258c-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6258c-107">脫銷的指標， `ULONG32` 接收包含命名空間名稱所需的緩衝區大小（以字元為單位），包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="6258c-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="6258c-108">脫銷包含命名空間名稱之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="6258c-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6258c-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6258c-109">Return Value</span></span>  
 <span data-ttu-id="6258c-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6258c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6258c-111">需求</span><span class="sxs-lookup"><span data-stu-id="6258c-111">Requirements</span></span>  
 <span data-ttu-id="6258c-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6258c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6258c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6258c-113">See also</span></span>

- [<span data-ttu-id="6258c-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="6258c-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
