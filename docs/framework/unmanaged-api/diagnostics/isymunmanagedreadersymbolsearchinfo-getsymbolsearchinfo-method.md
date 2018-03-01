---
title: "ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ecddc85ba473b4cff20331013b283ad12cf9bbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="fd1ef-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo 方法</span><span class="sxs-lookup"><span data-stu-id="fd1ef-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="fd1ef-103">取得符號搜尋資訊。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd1ef-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd1ef-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd1ef-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd1ef-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="fd1ef-106">[in]A`ULONG32`指出的大小`rgpSearchInfo`。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="fd1ef-107">[out]指標`ULONG32`包含搜尋資訊時所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="fd1ef-108">[out]設定的指標所傳回[ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd1ef-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd1ef-109">Return Value</span></span>  
 <span data-ttu-id="fd1ef-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="fd1ef-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd1ef-111">需求</span><span class="sxs-lookup"><span data-stu-id="fd1ef-111">Requirements</span></span>  
 <span data-ttu-id="fd1ef-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fd1ef-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd1ef-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="fd1ef-113">See Also</span></span>  
 [<span data-ttu-id="fd1ef-114">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fd1ef-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
