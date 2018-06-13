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
ms.openlocfilehash: a6a9c5ff91989fc1ad7da4e23df0e80d9d74ec7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424972"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="fd8a0-102">CorSymVarFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="fd8a0-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="fd8a0-103">指出變數是否為編譯器產生。</span><span class="sxs-lookup"><span data-stu-id="fd8a0-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd8a0-104">Syntax</span></span>  
  
```  
typedef enum CorSymVarFlag   
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="fd8a0-105">成員</span><span class="sxs-lookup"><span data-stu-id="fd8a0-105">Members</span></span>  
  
|<span data-ttu-id="fd8a0-106">成員</span><span class="sxs-lookup"><span data-stu-id="fd8a0-106">Member</span></span>|<span data-ttu-id="fd8a0-107">描述</span><span class="sxs-lookup"><span data-stu-id="fd8a0-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="fd8a0-108">指出指定的變數是由編譯器產生。</span><span class="sxs-lookup"><span data-stu-id="fd8a0-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fd8a0-109">需求</span><span class="sxs-lookup"><span data-stu-id="fd8a0-109">Requirements</span></span>  
 <span data-ttu-id="fd8a0-110">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fd8a0-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8a0-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd8a0-111">See Also</span></span>  
 [<span data-ttu-id="fd8a0-112">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="fd8a0-112">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
