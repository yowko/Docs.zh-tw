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
ms.openlocfilehash: 5f44d50f6736e0698fd876eedab78dbf41434af4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426312"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="24e64-102">ISymUnmanagedBinder3::GetReaderFromCallback 方法</span><span class="sxs-lookup"><span data-stu-id="24e64-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="24e64-103">可讓使用者實作，或可能是提供透過回呼`IID_IDiaReadExeAtRVACallback`或`IID_IDiaReadExeAtOffsetCallback`取得偵錯資訊從記憶體。</span><span class="sxs-lookup"><span data-stu-id="24e64-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24e64-104">語法</span><span class="sxs-lookup"><span data-stu-id="24e64-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24e64-105">參數</span><span class="sxs-lookup"><span data-stu-id="24e64-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="24e64-106">[in]中繼資料匯入介面指標。</span><span class="sxs-lookup"><span data-stu-id="24e64-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="24e64-107">[in]指向的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="24e64-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="24e64-108">[in]加入搜尋路徑中的指標。</span><span class="sxs-lookup"><span data-stu-id="24e64-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="24e64-109">[in]值為[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)列舉，指定要進行搜尋的符號讀取器時使用的原則。</span><span class="sxs-lookup"><span data-stu-id="24e64-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="24e64-110">[in]回呼函式的指標。</span><span class="sxs-lookup"><span data-stu-id="24e64-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="24e64-111">[out]設定的指標所傳回[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="24e64-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24e64-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="24e64-112">Return Value</span></span>  
 <span data-ttu-id="24e64-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="24e64-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24e64-114">需求</span><span class="sxs-lookup"><span data-stu-id="24e64-114">Requirements</span></span>  
 <span data-ttu-id="24e64-115">**標頭：** 於 CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="24e64-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e64-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24e64-116">See Also</span></span>  
 [<span data-ttu-id="24e64-117">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="24e64-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
