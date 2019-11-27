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
ms.openlocfilehash: 393984241412f543b6ac082484cf5e23edb2d9f4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448977"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="92d57-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 方法</span><span class="sxs-lookup"><span data-stu-id="92d57-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="92d57-103">允許編譯器省略未從程式資料庫（PDB）資料流程修改的函式，但前提是行資訊符合需求。</span><span class="sxs-lookup"><span data-stu-id="92d57-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="92d57-104">您可以使用舊的 PDB 行資訊，以及函式中所有行的一個差異來判斷正確的行資訊。</span><span class="sxs-lookup"><span data-stu-id="92d57-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92d57-105">語法</span><span class="sxs-lookup"><span data-stu-id="92d57-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92d57-106">參數</span><span class="sxs-lookup"><span data-stu-id="92d57-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="92d57-107">在包含行資訊之[IStream](/windows/desktop/api/objidl/nn-objidl-istream)的指標。</span><span class="sxs-lookup"><span data-stu-id="92d57-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="92d57-108">在[SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md)結構的指標，其中包含已變更的行。</span><span class="sxs-lookup"><span data-stu-id="92d57-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="92d57-109">在`ULONG`，表示已變更的行數。</span><span class="sxs-lookup"><span data-stu-id="92d57-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92d57-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="92d57-110">Return Value</span></span>  
 <span data-ttu-id="92d57-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="92d57-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92d57-112">需求</span><span class="sxs-lookup"><span data-stu-id="92d57-112">Requirements</span></span>  
 <span data-ttu-id="92d57-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="92d57-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d57-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92d57-114">See also</span></span>

- [<span data-ttu-id="92d57-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="92d57-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
