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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5478a8d3433a8a57dab458c98ea745f32a9ffdf4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721865"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="3ce15-102">ISymUnmanagedNamespace::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="3ce15-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="3ce15-103">取得這個命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="3ce15-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce15-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ce15-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ce15-105">參數</span><span class="sxs-lookup"><span data-stu-id="3ce15-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3ce15-106">[in]A`ULONG32`表示的大小`szName`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3ce15-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3ce15-107">[out]指標`ULONG32`接收大小，以字元為單位，以包含命名空間名稱，包括 null 終止所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="3ce15-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="3ce15-108">[out]包含命名空間名稱之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="3ce15-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ce15-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3ce15-109">Return Value</span></span>  
 <span data-ttu-id="3ce15-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ce15-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ce15-111">需求</span><span class="sxs-lookup"><span data-stu-id="3ce15-111">Requirements</span></span>  
 <span data-ttu-id="3ce15-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3ce15-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce15-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce15-113">See also</span></span>
- [<span data-ttu-id="3ce15-114">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="3ce15-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
