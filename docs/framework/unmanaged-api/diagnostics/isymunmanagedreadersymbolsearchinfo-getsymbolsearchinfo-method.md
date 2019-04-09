---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 519fa1b2c2866a6906d833251e18d86b7b43d525
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153721"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="e27e3-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo 方法</span><span class="sxs-lookup"><span data-stu-id="e27e3-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="e27e3-103">取得符號搜尋資訊。</span><span class="sxs-lookup"><span data-stu-id="e27e3-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e27e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="e27e3-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e27e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="e27e3-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="e27e3-106">[in]A`ULONG32`表示的大小`rgpSearchInfo`。</span><span class="sxs-lookup"><span data-stu-id="e27e3-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="e27e3-107">[out]指標`ULONG32`接收包含搜尋資訊所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="e27e3-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="e27e3-108">[out]設定指標所傳回[ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e27e3-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e27e3-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e27e3-109">Return Value</span></span>  
 <span data-ttu-id="e27e3-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e27e3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e27e3-111">需求</span><span class="sxs-lookup"><span data-stu-id="e27e3-111">Requirements</span></span>  
 <span data-ttu-id="e27e3-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e27e3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27e3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e27e3-113">See also</span></span>

- [<span data-ttu-id="e27e3-114">ISymUnmanagedReaderSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e27e3-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
