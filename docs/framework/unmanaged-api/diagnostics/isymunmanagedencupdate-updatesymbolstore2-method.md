---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 方法
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
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
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9082a05900330be27066b64f2ad0e99b87e04c61
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="da220-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 方法</span><span class="sxs-lookup"><span data-stu-id="da220-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="da220-103">讓編譯器將略過程式資料庫 (PDB) 資料流，從尚未經過修改的函式，提供行資訊符合的需求。</span><span class="sxs-lookup"><span data-stu-id="da220-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="da220-104">使用舊的 PDB 行資訊和函式中的所有行的一個差異，您可以判斷正確的行資訊。</span><span class="sxs-lookup"><span data-stu-id="da220-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da220-105">語法</span><span class="sxs-lookup"><span data-stu-id="da220-105">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da220-106">參數</span><span class="sxs-lookup"><span data-stu-id="da220-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="da220-107">[in]指標[IStream](https://msdn.microsoft.com/library/aa380034.aspx)包含行資訊。</span><span class="sxs-lookup"><span data-stu-id="da220-107">[in] A pointer to an [IStream](https://msdn.microsoft.com/library/aa380034.aspx) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="da220-108">[in]指標[SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md)結構，其中包含已變更的行。</span><span class="sxs-lookup"><span data-stu-id="da220-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="da220-109">[in]A `ULONG` ，代表已變更的行數。</span><span class="sxs-lookup"><span data-stu-id="da220-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da220-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="da220-110">Return Value</span></span>  
 <span data-ttu-id="da220-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="da220-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da220-112">需求</span><span class="sxs-lookup"><span data-stu-id="da220-112">Requirements</span></span>  
 <span data-ttu-id="da220-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="da220-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da220-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da220-114">See Also</span></span>  
 [<span data-ttu-id="da220-115">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="da220-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
