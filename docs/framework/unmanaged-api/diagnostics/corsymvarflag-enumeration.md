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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5b387ee7fd4cc0088c90d2b8278fbf18bb36f51
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755677"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="c2a1d-102">CorSymVarFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="c2a1d-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="c2a1d-103">指出變數是否為編譯器所產生。</span><span class="sxs-lookup"><span data-stu-id="c2a1d-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2a1d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="c2a1d-105">成員</span><span class="sxs-lookup"><span data-stu-id="c2a1d-105">Members</span></span>  
  
|<span data-ttu-id="c2a1d-106">成員</span><span class="sxs-lookup"><span data-stu-id="c2a1d-106">Member</span></span>|<span data-ttu-id="c2a1d-107">描述</span><span class="sxs-lookup"><span data-stu-id="c2a1d-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="c2a1d-108">指出指定的變數是由編譯器產生。</span><span class="sxs-lookup"><span data-stu-id="c2a1d-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2a1d-109">需求</span><span class="sxs-lookup"><span data-stu-id="c2a1d-109">Requirements</span></span>  
 <span data-ttu-id="c2a1d-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c2a1d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a1d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2a1d-111">See also</span></span>

- [<span data-ttu-id="c2a1d-112">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="c2a1d-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
