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
ms.openlocfilehash: 21e92d8f2fb80c4c41d516ef281bf4fc8a75f4e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176639"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="28bb3-102">CorSymVarFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="28bb3-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="28bb3-103">指示變數是否為編譯器生成。</span><span class="sxs-lookup"><span data-stu-id="28bb3-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28bb3-104">語法</span><span class="sxs-lookup"><span data-stu-id="28bb3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="28bb3-105">成員</span><span class="sxs-lookup"><span data-stu-id="28bb3-105">Members</span></span>  
  
|<span data-ttu-id="28bb3-106">member</span><span class="sxs-lookup"><span data-stu-id="28bb3-106">Member</span></span>|<span data-ttu-id="28bb3-107">描述</span><span class="sxs-lookup"><span data-stu-id="28bb3-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="28bb3-108">指示給定變數是編譯器生成的。</span><span class="sxs-lookup"><span data-stu-id="28bb3-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28bb3-109">需求</span><span class="sxs-lookup"><span data-stu-id="28bb3-109">Requirements</span></span>  
 <span data-ttu-id="28bb3-110">**標題：** 科西姆.伊德爾，科西姆.h</span><span class="sxs-lookup"><span data-stu-id="28bb3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28bb3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28bb3-111">See also</span></span>

- [<span data-ttu-id="28bb3-112">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="28bb3-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
