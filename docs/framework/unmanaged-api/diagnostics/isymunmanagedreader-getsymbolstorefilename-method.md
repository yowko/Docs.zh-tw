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
ms.openlocfilehash: df503e44f20a0b1f02e2c609cc4b52712520faea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720564"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="4826a-102">ISymUnmanagedReader::GetSymbolStoreFileName 方法</span><span class="sxs-lookup"><span data-stu-id="4826a-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>

<span data-ttu-id="4826a-103">提供符號存放區的磁片上檔案名。</span><span class="sxs-lookup"><span data-stu-id="4826a-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4826a-104">語法</span><span class="sxs-lookup"><span data-stu-id="4826a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4826a-105">參數</span><span class="sxs-lookup"><span data-stu-id="4826a-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="4826a-106">在緩衝區的大小 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="4826a-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4826a-107">擴展變數的指標，此變數會接收傳回的名稱長度 `szName` ，包括 null 終止。</span><span class="sxs-lookup"><span data-stu-id="4826a-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="4826a-108">擴展變數的指標，此變數會接收符號存放區的檔案名。</span><span class="sxs-lookup"><span data-stu-id="4826a-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4826a-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="4826a-109">Return Value</span></span>  

 <span data-ttu-id="4826a-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="4826a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4826a-111">需求</span><span class="sxs-lookup"><span data-stu-id="4826a-111">Requirements</span></span>  

 <span data-ttu-id="4826a-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="4826a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4826a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4826a-113">See also</span></span>

- [<span data-ttu-id="4826a-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="4826a-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
