---
title: ISymUnmanagedReader::GetSymbolStoreFileName 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 50cd6d1e3666dd1f15c1e6a6b4f7dcb931b79d8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777073"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="79213-102">ISymUnmanagedReader::GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="79213-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="79213-103">提供符號存放區的磁碟上檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="79213-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79213-104">語法</span><span class="sxs-lookup"><span data-stu-id="79213-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79213-105">參數</span><span class="sxs-lookup"><span data-stu-id="79213-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="79213-106">[in]大小`szName`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="79213-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="79213-107">[out]接收傳回的名稱的長度變數的指標`szName`，包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="79213-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="79213-108">[out]接收符號存放區的檔案名稱的變數的指標。</span><span class="sxs-lookup"><span data-stu-id="79213-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79213-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="79213-109">Return Value</span></span>  
 <span data-ttu-id="79213-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="79213-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79213-111">需求</span><span class="sxs-lookup"><span data-stu-id="79213-111">Requirements</span></span>  
 <span data-ttu-id="79213-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="79213-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79213-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79213-113">See also</span></span>

- [<span data-ttu-id="79213-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="79213-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
