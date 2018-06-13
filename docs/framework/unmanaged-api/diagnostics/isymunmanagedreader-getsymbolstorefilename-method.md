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
ms.openlocfilehash: b36f4007f286938169cc5d583908493916b9e6f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425336"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="6f154-102">ISymUnmanagedReader::GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="6f154-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="6f154-103">提供符號存放區的磁碟上檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6f154-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f154-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f154-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f154-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f154-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6f154-106">[in]大小`szName`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6f154-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6f154-107">[out]接收中傳回的名稱長度變數的指標`szName`，包括 null 結束。</span><span class="sxs-lookup"><span data-stu-id="6f154-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="6f154-108">[out]指標，此變數會接收符號存放區的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6f154-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f154-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f154-109">Return Value</span></span>  
 <span data-ttu-id="6f154-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f154-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f154-111">需求</span><span class="sxs-lookup"><span data-stu-id="6f154-111">Requirements</span></span>  
 <span data-ttu-id="6f154-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6f154-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f154-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f154-113">See Also</span></span>  
 [<span data-ttu-id="6f154-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="6f154-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
