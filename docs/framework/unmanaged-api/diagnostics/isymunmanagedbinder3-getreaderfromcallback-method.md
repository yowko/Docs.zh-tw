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
ms.openlocfilehash: d48c2bdd55e487038048f432c5586d49f393118c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706940"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="e24b0-102">ISymUnmanagedBinder3::GetReaderFromCallback 方法</span><span class="sxs-lookup"><span data-stu-id="e24b0-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>

<span data-ttu-id="e24b0-103">允許使用者透過回呼或 `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` 從記憶體中取得 debug 目錄資訊來執行或提供。</span><span class="sxs-lookup"><span data-stu-id="e24b0-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e24b0-104">語法</span><span class="sxs-lookup"><span data-stu-id="e24b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e24b0-105">參數</span><span class="sxs-lookup"><span data-stu-id="e24b0-105">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="e24b0-106">在中繼資料匯入介面的指標。</span><span class="sxs-lookup"><span data-stu-id="e24b0-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="e24b0-107">在檔案名的指標。</span><span class="sxs-lookup"><span data-stu-id="e24b0-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="e24b0-108">在搜尋路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="e24b0-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="e24b0-109">在 [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) 列舉的值，這個值會指定在搜尋符號讀取器時要使用的原則。</span><span class="sxs-lookup"><span data-stu-id="e24b0-109">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="e24b0-110">在回呼函數的指標。</span><span class="sxs-lookup"><span data-stu-id="e24b0-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e24b0-111">擴展設定為傳回之 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="e24b0-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e24b0-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="e24b0-112">Return Value</span></span>  

 <span data-ttu-id="e24b0-113">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e24b0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e24b0-114">需求</span><span class="sxs-lookup"><span data-stu-id="e24b0-114">Requirements</span></span>  

 <span data-ttu-id="e24b0-115">**標頭：** CorSym .idl</span><span class="sxs-lookup"><span data-stu-id="e24b0-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e24b0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e24b0-116">See also</span></span>

- [<span data-ttu-id="e24b0-117">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="e24b0-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
