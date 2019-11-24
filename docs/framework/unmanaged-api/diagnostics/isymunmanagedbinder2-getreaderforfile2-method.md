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
ms.openlocfilehash: 756ba2e71ca2e3e817a0a8b89165bb807368c1f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449327"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="5264f-102">ISymUnmanagedBinder2::GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="5264f-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="5264f-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span><span class="sxs-lookup"><span data-stu-id="5264f-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="5264f-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="5264f-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5264f-105">語法</span><span class="sxs-lookup"><span data-stu-id="5264f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5264f-106">參數</span><span class="sxs-lookup"><span data-stu-id="5264f-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="5264f-107">[in] A pointer to the metadata import interface.</span><span class="sxs-lookup"><span data-stu-id="5264f-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="5264f-108">[in] A pointer to the file name.</span><span class="sxs-lookup"><span data-stu-id="5264f-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="5264f-109">[in] A pointer to the search path.</span><span class="sxs-lookup"><span data-stu-id="5264f-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="5264f-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span><span class="sxs-lookup"><span data-stu-id="5264f-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5264f-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="5264f-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5264f-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="5264f-112">Return Value</span></span>  
 <span data-ttu-id="5264f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="5264f-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5264f-114">需求</span><span class="sxs-lookup"><span data-stu-id="5264f-114">Requirements</span></span>  
 <span data-ttu-id="5264f-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5264f-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5264f-116">備註</span><span class="sxs-lookup"><span data-stu-id="5264f-116">Remarks</span></span>  
 <span data-ttu-id="5264f-117">This version of the method can search for the PDB file in areas other than right next to the module.</span><span class="sxs-lookup"><span data-stu-id="5264f-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="5264f-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="5264f-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="5264f-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span><span class="sxs-lookup"><span data-stu-id="5264f-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="5264f-120">If the `searchPath` parameter is provided, those directories will always be searched.</span><span class="sxs-lookup"><span data-stu-id="5264f-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5264f-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="5264f-121">See also</span></span>

- [<span data-ttu-id="5264f-122">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="5264f-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="5264f-123">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="5264f-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
