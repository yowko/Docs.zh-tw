---
title: "ISymUnmanagedBinder2::GetReaderForFile2 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 270a154c40b85ad4774bececf12685393f4d6c58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="030de-102">ISymUnmanagedBinder2::GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="030de-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="030de-103">提供中繼資料介面和檔案名稱，傳回的正確 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 會讀取偵錯符號的模組相關聯的介面。</span><span class="sxs-lookup"><span data-stu-id="030de-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="030de-104">這個方法提供程式資料庫 (PDB) 檔比更廣泛的搜尋[isymunmanagedbinder:: Getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="030de-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="030de-105">語法</span><span class="sxs-lookup"><span data-stu-id="030de-105">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="030de-106">參數</span><span class="sxs-lookup"><span data-stu-id="030de-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="030de-107">[in]中繼資料匯入介面指標。</span><span class="sxs-lookup"><span data-stu-id="030de-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="030de-108">[in]指向的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="030de-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="030de-109">[in]加入搜尋路徑中的指標。</span><span class="sxs-lookup"><span data-stu-id="030de-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="030de-110">[in]值為[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)列舉，指定要進行搜尋的符號讀取器時使用的原則。</span><span class="sxs-lookup"><span data-stu-id="030de-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="030de-111">[out]設定的指標所傳回 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 介面。</span><span class="sxs-lookup"><span data-stu-id="030de-111">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="030de-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="030de-112">Return Value</span></span>  
 <span data-ttu-id="030de-113">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="030de-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="030de-114">需求</span><span class="sxs-lookup"><span data-stu-id="030de-114">Requirements</span></span>  
 <span data-ttu-id="030de-115">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="030de-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="030de-116">備註</span><span class="sxs-lookup"><span data-stu-id="030de-116">Remarks</span></span>  
 <span data-ttu-id="030de-117">這個版本的方法可以搜尋 PDB 檔案的旁邊，模組以外的區域。</span><span class="sxs-lookup"><span data-stu-id="030de-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="030de-118">搜尋原則可以控制結合[CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md)。</span><span class="sxs-lookup"><span data-stu-id="030de-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="030de-119">例如，`AllowReferencePathAccess | AllowSymbolServerAccess`尋找 PDB 旁的可執行檔和符號伺服器上，但不會查詢登錄或可執行檔中使用的路徑。</span><span class="sxs-lookup"><span data-stu-id="030de-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="030de-120">如果`searchPath`提供參數，則一律會搜尋這些目錄。</span><span class="sxs-lookup"><span data-stu-id="030de-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="030de-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="030de-121">See Also</span></span>  
 [<span data-ttu-id="030de-122">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="030de-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="030de-123">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="030de-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
