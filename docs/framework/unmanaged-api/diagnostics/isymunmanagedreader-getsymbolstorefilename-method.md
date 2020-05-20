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
ms.openlocfilehash: 6ffab3b2f81680404f870cfd63ae5125173a346c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615510"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="e6fc6-102">ISymUnmanagedReader::GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="e6fc6-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="e6fc6-103">提供符號存放區的磁片檔案名。</span><span class="sxs-lookup"><span data-stu-id="e6fc6-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6fc6-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6fc6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6fc6-105">參數</span><span class="sxs-lookup"><span data-stu-id="e6fc6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e6fc6-106">在緩衝區的大小 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="e6fc6-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e6fc6-107">脫銷變數的指標，其接收傳回的名稱長度 `szName` ，包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="e6fc6-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="e6fc6-108">脫銷接收符號存放區檔案名之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="e6fc6-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6fc6-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6fc6-109">Return Value</span></span>  
 <span data-ttu-id="e6fc6-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e6fc6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6fc6-111">需求</span><span class="sxs-lookup"><span data-stu-id="e6fc6-111">Requirements</span></span>  
 <span data-ttu-id="e6fc6-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="e6fc6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6fc6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6fc6-113">See also</span></span>

- [<span data-ttu-id="e6fc6-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="e6fc6-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
