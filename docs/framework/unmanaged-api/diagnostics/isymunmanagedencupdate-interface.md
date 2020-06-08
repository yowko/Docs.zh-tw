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
ms.openlocfilehash: 1986d5f91a3dcfa31a43f729ee1f50129e083f5f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501738"
---
# <a name="isymunmanagedencupdate-interface"></a><span data-ttu-id="5319a-102">ISymUnmanagedENCUpdate 介面</span><span class="sxs-lookup"><span data-stu-id="5319a-102">ISymUnmanagedENCUpdate Interface</span></span>
<span data-ttu-id="5319a-103">提供 [編輯後繼續] 功能的功能。</span><span class="sxs-lookup"><span data-stu-id="5319a-103">Provides functions for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5319a-104">方法</span><span class="sxs-lookup"><span data-stu-id="5319a-104">Methods</span></span>  
  
|<span data-ttu-id="5319a-105">方法</span><span class="sxs-lookup"><span data-stu-id="5319a-105">Method</span></span>|<span data-ttu-id="5319a-106">描述</span><span class="sxs-lookup"><span data-stu-id="5319a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5319a-107">GetLocalVariableCount 方法</span><span class="sxs-lookup"><span data-stu-id="5319a-107">GetLocalVariableCount Method</span></span>](isymunmanagedencupdate-getlocalvariablecount-method.md)|<span data-ttu-id="5319a-108">取得本機變數的數目。</span><span class="sxs-lookup"><span data-stu-id="5319a-108">Gets the number of local variables.</span></span>|  
|[<span data-ttu-id="5319a-109">GetLocalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="5319a-109">GetLocalVariables Method</span></span>](isymunmanagedencupdate-getlocalvariables-method.md)|<span data-ttu-id="5319a-110">取得本機變數。</span><span class="sxs-lookup"><span data-stu-id="5319a-110">Gets the local variables.</span></span>|  
|[<span data-ttu-id="5319a-111">InitializeForEnc 方法</span><span class="sxs-lookup"><span data-stu-id="5319a-111">InitializeForEnc Method</span></span>](isymunmanagedencupdate-initializeforenc-method.md)|<span data-ttu-id="5319a-112">允許在第一次呼叫[ISymUnmanagedENCUpdate：： UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md)方法之前計算方法界限。</span><span class="sxs-lookup"><span data-stu-id="5319a-112">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>|  
|[<span data-ttu-id="5319a-113">UpdateMethodLines 方法</span><span class="sxs-lookup"><span data-stu-id="5319a-113">UpdateMethodLines Method</span></span>](isymunmanagedencupdate-updatemethodlines-method.md)|<span data-ttu-id="5319a-114">允許更新尚未重新編譯之方法的行資訊，但其行已獨立移動。</span><span class="sxs-lookup"><span data-stu-id="5319a-114">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="5319a-115">允許每個語句的差異。</span><span class="sxs-lookup"><span data-stu-id="5319a-115">A delta for each statement is allowed.</span></span>|  
|[<span data-ttu-id="5319a-116">UpdateSymbolStore2 方法</span><span class="sxs-lookup"><span data-stu-id="5319a-116">UpdateSymbolStore2 Method</span></span>](isymunmanagedencupdate-updatesymbolstore2-method.md)|<span data-ttu-id="5319a-117">允許編譯器省略未從程式資料庫（PDB）資料流程修改的函式，但前提是行資訊符合需求。</span><span class="sxs-lookup"><span data-stu-id="5319a-117">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements.</span></span> <span data-ttu-id="5319a-118">您可以使用舊的 PDB 行資訊，以及函式中所有行的一個差異來判斷正確的行資訊。</span><span class="sxs-lookup"><span data-stu-id="5319a-118">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5319a-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="5319a-119">Requirements</span></span>  
 <span data-ttu-id="5319a-120">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="5319a-120">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5319a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5319a-121">See also</span></span>

- [<span data-ttu-id="5319a-122">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="5319a-122">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
