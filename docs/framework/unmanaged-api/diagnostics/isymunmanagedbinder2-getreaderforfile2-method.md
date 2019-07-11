---
title: ISymUnmanagedBinder2::GetReaderForFile2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db917820de92b2e347385afc5217c0ca190825cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776829"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="2f933-102">ISymUnmanagedBinder2::GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="2f933-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="2f933-103">提供中繼資料介面和檔案名稱，傳回的正確[ISymUnmanagedReader](isymunmanagedreader-interface.md)會讀取偵錯符號的模組相關聯的介面。</span><span class="sxs-lookup"><span data-stu-id="2f933-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="2f933-104">這個方法會提供更廣泛的搜尋的程式資料庫 (PDB) 檔，比[isymunmanagedbinder:: Getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2f933-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f933-105">語法</span><span class="sxs-lookup"><span data-stu-id="2f933-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f933-106">參數</span><span class="sxs-lookup"><span data-stu-id="2f933-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="2f933-107">[in]中繼資料匯入介面指標。</span><span class="sxs-lookup"><span data-stu-id="2f933-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="2f933-108">[in]檔案名稱指標。</span><span class="sxs-lookup"><span data-stu-id="2f933-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="2f933-109">[in]加入搜尋路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="2f933-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="2f933-110">[in]值為[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)列舉，指定要在進行搜尋的符號讀取器時使用的原則。</span><span class="sxs-lookup"><span data-stu-id="2f933-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2f933-111">[out]設定指標所傳回[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="2f933-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f933-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="2f933-112">Return Value</span></span>  
 <span data-ttu-id="2f933-113">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="2f933-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f933-114">需求</span><span class="sxs-lookup"><span data-stu-id="2f933-114">Requirements</span></span>  
 <span data-ttu-id="2f933-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2f933-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f933-116">備註</span><span class="sxs-lookup"><span data-stu-id="2f933-116">Remarks</span></span>  
 <span data-ttu-id="2f933-117">這個版本的方法可以搜尋模組旁邊以外的區域中的 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="2f933-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="2f933-118">搜尋原則可以控制結合[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="2f933-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="2f933-119">比方說，`AllowReferencePathAccess | AllowSymbolServerAccess`尋找 PDB 旁的可執行檔和符號伺服器，但不會查詢登錄或使用中的可執行檔的路徑。</span><span class="sxs-lookup"><span data-stu-id="2f933-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="2f933-120">如果`searchPath`提供參數，則一律會搜尋這些目錄。</span><span class="sxs-lookup"><span data-stu-id="2f933-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f933-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f933-121">See also</span></span>

- [<span data-ttu-id="2f933-122">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="2f933-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="2f933-123">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="2f933-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
