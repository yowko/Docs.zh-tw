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
ms.openlocfilehash: 97b9fa537fdd9147d6d9eda036013add5393e33c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441704"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="804cc-102">ISymUnmanagedBinder2::GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="804cc-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="804cc-103">提供中繼資料介面和檔案名，會傳回正確的[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面，以便讀取與模組相關聯的偵錯工具符號。</span><span class="sxs-lookup"><span data-stu-id="804cc-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="804cc-104">這個方法比[ISymUnmanagedBinder：： GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md)方法提供更廣泛的程式資料庫（PDB）檔案搜尋。</span><span class="sxs-lookup"><span data-stu-id="804cc-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="804cc-105">語法</span><span class="sxs-lookup"><span data-stu-id="804cc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="804cc-106">參數</span><span class="sxs-lookup"><span data-stu-id="804cc-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="804cc-107">在中繼資料匯入介面的指標。</span><span class="sxs-lookup"><span data-stu-id="804cc-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="804cc-108">在檔案名的指標。</span><span class="sxs-lookup"><span data-stu-id="804cc-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="804cc-109">在搜尋路徑的指標。</span><span class="sxs-lookup"><span data-stu-id="804cc-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="804cc-110">在[CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md)列舉的值，指定搜尋符號讀取器時要使用的原則。</span><span class="sxs-lookup"><span data-stu-id="804cc-110">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="804cc-111">脫銷設定為所傳回[ISymUnmanagedReader](isymunmanagedreader-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="804cc-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="804cc-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="804cc-112">Return Value</span></span>  
 <span data-ttu-id="804cc-113">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="804cc-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="804cc-114">需求</span><span class="sxs-lookup"><span data-stu-id="804cc-114">Requirements</span></span>  
 <span data-ttu-id="804cc-115">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="804cc-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="804cc-116">備註</span><span class="sxs-lookup"><span data-stu-id="804cc-116">Remarks</span></span>  
 <span data-ttu-id="804cc-117">這個版本的方法可以在模組旁邊的區域中搜尋 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="804cc-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="804cc-118">搜尋原則可以藉由結合[CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md)來控制。</span><span class="sxs-lookup"><span data-stu-id="804cc-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="804cc-119">例如， `AllowReferencePathAccess | AllowSymbolServerAccess` 會在可執行檔和符號伺服器上尋找 PDB，但不會查詢登錄或使用可執行檔中的路徑。</span><span class="sxs-lookup"><span data-stu-id="804cc-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="804cc-120">如果 `searchPath` 提供參數，則一律會搜尋這些目錄。</span><span class="sxs-lookup"><span data-stu-id="804cc-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804cc-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="804cc-121">See also</span></span>

- [<span data-ttu-id="804cc-122">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="804cc-122">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="804cc-123">GetReaderForFile 方法</span><span class="sxs-lookup"><span data-stu-id="804cc-123">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)
