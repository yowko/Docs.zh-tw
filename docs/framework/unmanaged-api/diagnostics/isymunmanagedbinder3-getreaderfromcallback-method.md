---
title: ISymUnmanagedBinder3::GetReaderFromCallback 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5767b60fa992b49fdc2a60feb243a26c0e2ea1ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534541"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="d42d2-102">ISymUnmanagedBinder3::GetReaderFromCallback 方法</span><span class="sxs-lookup"><span data-stu-id="d42d2-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="d42d2-103">可讓使用者實作，或可能是提供透過回呼`IID_IDiaReadExeAtRVACallback`或`IID_IDiaReadExeAtOffsetCallback`從記憶體中取得的偵錯資訊。</span><span class="sxs-lookup"><span data-stu-id="d42d2-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d42d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="d42d2-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d42d2-105">參數</span><span class="sxs-lookup"><span data-stu-id="d42d2-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="d42d2-106">[in]中繼資料匯入介面指標。</span><span class="sxs-lookup"><span data-stu-id="d42d2-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="d42d2-107">[in]檔案名稱指標。</span><span class="sxs-lookup"><span data-stu-id="d42d2-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="d42d2-108">[in]加入搜尋路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="d42d2-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="d42d2-109">[in]值為[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)列舉，指定要在進行搜尋的符號讀取器時使用的原則。</span><span class="sxs-lookup"><span data-stu-id="d42d2-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="d42d2-110">[in]回呼函式的指標。</span><span class="sxs-lookup"><span data-stu-id="d42d2-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d42d2-111">[out]設定指標所傳回[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="d42d2-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d42d2-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d42d2-112">Return Value</span></span>  
 <span data-ttu-id="d42d2-113">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="d42d2-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d42d2-114">需求</span><span class="sxs-lookup"><span data-stu-id="d42d2-114">Requirements</span></span>  
 <span data-ttu-id="d42d2-115">**標頭：** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="d42d2-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d42d2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d42d2-116">See also</span></span>
- [<span data-ttu-id="d42d2-117">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="d42d2-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
