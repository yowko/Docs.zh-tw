---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d2c641f011c55ee726e319cb581705e334c840d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774670"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="f7bed-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 方法</span><span class="sxs-lookup"><span data-stu-id="f7bed-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="f7bed-103">讓編譯器將省略尚未經過修改的程式資料庫 (PDB)，從資料流的函式，提供行資訊符合需求。</span><span class="sxs-lookup"><span data-stu-id="f7bed-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="f7bed-104">使用舊的 PDB 行資訊和函式中的所有行的一個差異，您可以判斷正確的行資訊。</span><span class="sxs-lookup"><span data-stu-id="f7bed-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7bed-105">語法</span><span class="sxs-lookup"><span data-stu-id="f7bed-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7bed-106">參數</span><span class="sxs-lookup"><span data-stu-id="f7bed-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="f7bed-107">[in]指標[IStream](/windows/desktop/api/objidl/nn-objidl-istream)包含行資訊。</span><span class="sxs-lookup"><span data-stu-id="f7bed-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="f7bed-108">[in]指標[SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md)包含已變更的資料行的結構。</span><span class="sxs-lookup"><span data-stu-id="f7bed-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="f7bed-109">[in]A `ULONG` ，代表已變更的行數。</span><span class="sxs-lookup"><span data-stu-id="f7bed-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7bed-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f7bed-110">Return Value</span></span>  
 <span data-ttu-id="f7bed-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="f7bed-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7bed-112">需求</span><span class="sxs-lookup"><span data-stu-id="f7bed-112">Requirements</span></span>  
 <span data-ttu-id="f7bed-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f7bed-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7bed-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7bed-114">See also</span></span>

- [<span data-ttu-id="f7bed-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="f7bed-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
