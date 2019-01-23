---
title: ISymUnmanagedENCUpdate 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 634716b36a0e5826cd7667a9ae948e8172724a1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630862"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="7c762-102">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="7c762-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="7c762-103">[編輯後繼續] 功能提供函式。</span><span class="sxs-lookup"><span data-stu-id="7c762-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c762-104">方法</span><span class="sxs-lookup"><span data-stu-id="7c762-104">Methods</span></span>  
  
|<span data-ttu-id="7c762-105">方法</span><span class="sxs-lookup"><span data-stu-id="7c762-105">Method</span></span>|<span data-ttu-id="7c762-106">描述</span><span class="sxs-lookup"><span data-stu-id="7c762-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c762-107">GetLocalVariableCount 方法</span><span class="sxs-lookup"><span data-stu-id="7c762-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="7c762-108">取得區域變數的數目。</span><span class="sxs-lookup"><span data-stu-id="7c762-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="7c762-109">GetLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="7c762-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="7c762-110">取得本機變數。</span><span class="sxs-lookup"><span data-stu-id="7c762-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="7c762-111">InitializeForEnc 方法</span><span class="sxs-lookup"><span data-stu-id="7c762-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="7c762-112">可讓要計算的第一個呼叫之前的方法界限[ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="7c762-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="7c762-113">UpdateMethodLines 方法</span><span class="sxs-lookup"><span data-stu-id="7c762-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="7c762-114">允許更新的方法，具有未重新編譯，但其中的行已獨立的行資訊。</span><span class="sxs-lookup"><span data-stu-id="7c762-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="7c762-115">允許每個陳述式的差異。</span><span class="sxs-lookup"><span data-stu-id="7c762-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="7c762-116">UpdateSymbolStore2 方法</span><span class="sxs-lookup"><span data-stu-id="7c762-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="7c762-117">讓編譯器將省略尚未經過修改的程式資料庫 (PDB)，從資料流的函式，前提是行資訊符合需求。</span><span class="sxs-lookup"><span data-stu-id="7c762-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="7c762-118">使用舊的 PDB 行資訊和函式中的所有行的一個差異，您可以判斷正確的行資訊。</span><span class="sxs-lookup"><span data-stu-id="7c762-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c762-119">需求</span><span class="sxs-lookup"><span data-stu-id="7c762-119">Requirements</span></span>  
 <span data-ttu-id="7c762-120">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7c762-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c762-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c762-121">See also</span></span>
- [<span data-ttu-id="7c762-122">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="7c762-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
