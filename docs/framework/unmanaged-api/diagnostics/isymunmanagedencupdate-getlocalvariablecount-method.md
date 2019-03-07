---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a8a56d9655a2754c110c08517229a39011d82c5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482453"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="1bf09-102">ISymUnmanagedENCUpdate::GetLocalVariableCount 方法</span><span class="sxs-lookup"><span data-stu-id="1bf09-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="1bf09-103">取得區域變數的數目。</span><span class="sxs-lookup"><span data-stu-id="1bf09-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf09-104">語法</span><span class="sxs-lookup"><span data-stu-id="1bf09-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bf09-105">參數</span><span class="sxs-lookup"><span data-stu-id="1bf09-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="1bf09-106">[in]方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1bf09-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="1bf09-107">[out]指標`ULONG32`接收大小，以字元為單位，以包含區域變數的數目所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1bf09-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bf09-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1bf09-108">Return Value</span></span>  
 <span data-ttu-id="1bf09-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="1bf09-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bf09-110">需求</span><span class="sxs-lookup"><span data-stu-id="1bf09-110">Requirements</span></span>  
 <span data-ttu-id="1bf09-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1bf09-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf09-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bf09-112">See also</span></span>
- [<span data-ttu-id="1bf09-113">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="1bf09-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
