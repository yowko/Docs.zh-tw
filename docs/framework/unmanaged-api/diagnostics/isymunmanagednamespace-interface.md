---
title: ISymUnmanagedNamespace 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace
helpviewer_keywords:
- ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: d42bea4e-5848-4e43-a883-69af7a313ce9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87dd6db9624c2216ab13e77b04cfa63f95aee7e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939447"
---
# <a name="isymunmanagednamespace-interface"></a><span data-ttu-id="963d9-102">ISymUnmanagedNamespace 介面</span><span class="sxs-lookup"><span data-stu-id="963d9-102">ISymUnmanagedNamespace Interface</span></span>
<span data-ttu-id="963d9-103">代表命名空間。</span><span class="sxs-lookup"><span data-stu-id="963d9-103">Represents a namespace.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="963d9-104">方法</span><span class="sxs-lookup"><span data-stu-id="963d9-104">Methods</span></span>  
  
|<span data-ttu-id="963d9-105">方法</span><span class="sxs-lookup"><span data-stu-id="963d9-105">Method</span></span>|<span data-ttu-id="963d9-106">描述</span><span class="sxs-lookup"><span data-stu-id="963d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="963d9-107">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="963d9-107">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-getname-method.md)|<span data-ttu-id="963d9-108">取得這個命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="963d9-108">Gets the name of this namespace.</span></span>|  
|[<span data-ttu-id="963d9-109">GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="963d9-109">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-getnamespaces-method.md)|<span data-ttu-id="963d9-110">取得這個命名空間的子系。</span><span class="sxs-lookup"><span data-stu-id="963d9-110">Gets the children of this namespace.</span></span>|  
|[<span data-ttu-id="963d9-111">GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="963d9-111">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-getvariables-method.md)|<span data-ttu-id="963d9-112">傳回在此命名空間內的全域範圍中定義的所有變數。</span><span class="sxs-lookup"><span data-stu-id="963d9-112">Returns all variables defined at global scope within this namespace.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="963d9-113">需求</span><span class="sxs-lookup"><span data-stu-id="963d9-113">Requirements</span></span>  
 <span data-ttu-id="963d9-114">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="963d9-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="963d9-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="963d9-115">See also</span></span>

- [<span data-ttu-id="963d9-116">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="963d9-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
