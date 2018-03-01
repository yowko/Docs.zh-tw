---
title: "ISymUnmanagedENCUpdate 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f68d000824779fcffb90ec031b86b50e8c80eccd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="a5636-102">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="a5636-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="a5636-103">[編輯後繼續] 功能提供函式。</span><span class="sxs-lookup"><span data-stu-id="a5636-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5636-104">方法</span><span class="sxs-lookup"><span data-stu-id="a5636-104">Methods</span></span>  
  
|<span data-ttu-id="a5636-105">方法</span><span class="sxs-lookup"><span data-stu-id="a5636-105">Method</span></span>|<span data-ttu-id="a5636-106">描述</span><span class="sxs-lookup"><span data-stu-id="a5636-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5636-107">GetLocalVariableCount 方法</span><span class="sxs-lookup"><span data-stu-id="a5636-107">GetLocalVariableCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="a5636-108">取得區域變數的數目。</span><span class="sxs-lookup"><span data-stu-id="a5636-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="a5636-109">GetLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="a5636-109">GetLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="a5636-110">取得區域變數。</span><span class="sxs-lookup"><span data-stu-id="a5636-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="a5636-111">InitializeForEnc 方法</span><span class="sxs-lookup"><span data-stu-id="a5636-111">InitializeForEnc Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="a5636-112">可讓方法的第一個呼叫之前要計算的界限[isymunmanagedencupdate:: Updatesymbolstore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a5636-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="a5636-113">UpdateMethodLines 方法</span><span class="sxs-lookup"><span data-stu-id="a5636-113">UpdateMethodLines Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="a5636-114">允許更新的方法，具有未重新編譯，但其中的行已獨立的行資訊。</span><span class="sxs-lookup"><span data-stu-id="a5636-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="a5636-115">允許每個陳述式的差異。</span><span class="sxs-lookup"><span data-stu-id="a5636-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="a5636-116">UpdateSymbolStore2 方法</span><span class="sxs-lookup"><span data-stu-id="a5636-116">UpdateSymbolStore2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="a5636-117">讓編譯器將省略程式資料庫 (PDB) 資料流，從尚未經過修改的函式，前提是行資訊符合的需求。</span><span class="sxs-lookup"><span data-stu-id="a5636-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="a5636-118">使用舊的 PDB 行資訊和函式中的所有行的一個差異，您可以判斷正確的行資訊。</span><span class="sxs-lookup"><span data-stu-id="a5636-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5636-119">需求</span><span class="sxs-lookup"><span data-stu-id="a5636-119">Requirements</span></span>  
 <span data-ttu-id="a5636-120">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a5636-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5636-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5636-121">See Also</span></span>  
 [<span data-ttu-id="a5636-122">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="a5636-122">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
