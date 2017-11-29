---
title: "ISymUnmanagedReader::GetSymbolStoreFileName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymbolStoreFileName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 951dfd45f6b313b6cde28f3f65f2799380a33a78
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="e2e65-102">ISymUnmanagedReader::GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="e2e65-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="e2e65-103">提供符號存放區的磁碟上檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e2e65-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2e65-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2e65-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2e65-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2e65-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e2e65-106">[in]大小`szName`緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e2e65-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e2e65-107">[out]接收中傳回的名稱長度變數的指標`szName`，包括 null 結束。</span><span class="sxs-lookup"><span data-stu-id="e2e65-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="e2e65-108">[out]指標，此變數會接收符號存放區的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="e2e65-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2e65-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e2e65-109">Return Value</span></span>  
 <span data-ttu-id="e2e65-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="e2e65-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2e65-111">需求</span><span class="sxs-lookup"><span data-stu-id="e2e65-111">Requirements</span></span>  
 <span data-ttu-id="e2e65-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e2e65-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e65-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2e65-113">See Also</span></span>  
 [<span data-ttu-id="e2e65-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="e2e65-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
