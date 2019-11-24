---
title: CorSymVarFlag 列舉
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: 86cac53508665c3c97caaa415d8d3c38660928bb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448557"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="569dc-102">CorSymVarFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="569dc-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="569dc-103">Indicates whether a variable is compiler-generated.</span><span class="sxs-lookup"><span data-stu-id="569dc-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="569dc-104">語法</span><span class="sxs-lookup"><span data-stu-id="569dc-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="569dc-105">Members</span><span class="sxs-lookup"><span data-stu-id="569dc-105">Members</span></span>  
  
|<span data-ttu-id="569dc-106">成員</span><span class="sxs-lookup"><span data-stu-id="569dc-106">Member</span></span>|<span data-ttu-id="569dc-107">描述</span><span class="sxs-lookup"><span data-stu-id="569dc-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="569dc-108">Indicates that the given variable is compiler-generated.</span><span class="sxs-lookup"><span data-stu-id="569dc-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="569dc-109">需求</span><span class="sxs-lookup"><span data-stu-id="569dc-109">Requirements</span></span>  
 <span data-ttu-id="569dc-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="569dc-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="569dc-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="569dc-111">See also</span></span>

- [<span data-ttu-id="569dc-112">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="569dc-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
