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
ms.openlocfilehash: 147b33a3f49f9163daea776779ca26f62561a84e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670010"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="7f796-102">ISymUnmanagedReader::GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="7f796-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="7f796-103">提供符號存放區的磁碟上檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="7f796-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f796-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f796-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f796-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f796-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="7f796-106">[in]大小`szName`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7f796-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7f796-107">[out]接收傳回的名稱的長度變數的指標`szName`，包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="7f796-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="7f796-108">[out]接收符號存放區的檔案名稱的變數的指標。</span><span class="sxs-lookup"><span data-stu-id="7f796-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f796-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="7f796-109">Return Value</span></span>  
 <span data-ttu-id="7f796-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="7f796-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f796-111">需求</span><span class="sxs-lookup"><span data-stu-id="7f796-111">Requirements</span></span>  
 <span data-ttu-id="7f796-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f796-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f796-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f796-113">See also</span></span>

- [<span data-ttu-id="7f796-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="7f796-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
