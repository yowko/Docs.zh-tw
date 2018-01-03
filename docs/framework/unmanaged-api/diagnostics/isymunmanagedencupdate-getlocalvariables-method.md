---
title: "ISymUnmanagedENCUpdate::GetLocalVariables 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.GetLocalVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eefd64441221a7e6e00689d6be272540f9c2423c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="f453b-102">ISymUnmanagedENCUpdate::GetLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="f453b-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="f453b-103">取得區域變數。</span><span class="sxs-lookup"><span data-stu-id="f453b-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f453b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f453b-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f453b-105">參數</span><span class="sxs-lookup"><span data-stu-id="f453b-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="f453b-106">[in]方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f453b-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="f453b-107">[in]A`ULONG`指出的大小`rgLocals`參數。</span><span class="sxs-lookup"><span data-stu-id="f453b-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="f453b-108">[out]傳回的陣列的<!--zz<xref:ISymUnmanagedVariable>-->`ISymUnmanagedVariable`執行個體。</span><span class="sxs-lookup"><span data-stu-id="f453b-108">[out] The returned array of <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable`  instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="f453b-109">[out]指標`ULONG`大小`rgLocals`包含區域變數所需要的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f453b-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f453b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f453b-110">Return Value</span></span>  
 <span data-ttu-id="f453b-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f453b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f453b-112">需求</span><span class="sxs-lookup"><span data-stu-id="f453b-112">Requirements</span></span>  
 <span data-ttu-id="f453b-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f453b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f453b-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f453b-114">See Also</span></span>  
 [<span data-ttu-id="f453b-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="f453b-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
