---
title: COINITIEE 列舉
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
ms.openlocfilehash: 673450bb8209abede15e3cb65dd764b418073bc2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724191"
---
# <a name="coinitiee-enumeration"></a><span data-ttu-id="d165d-102">COINITIEE 列舉</span><span class="sxs-lookup"><span data-stu-id="d165d-102">COINITIEE Enumeration</span></span>

<span data-ttu-id="d165d-103">指定初始化 common language runtime 時， [CoInitializeEE](../hosting/coinitializeee-function.md) 所使用的常數。</span><span class="sxs-lookup"><span data-stu-id="d165d-103">Specifies constants used by [CoInitializeEE](../hosting/coinitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d165d-104">語法</span><span class="sxs-lookup"><span data-stu-id="d165d-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="d165d-105">成員</span><span class="sxs-lookup"><span data-stu-id="d165d-105">Members</span></span>  
  
|<span data-ttu-id="d165d-106">member</span><span class="sxs-lookup"><span data-stu-id="d165d-106">Member</span></span>|<span data-ttu-id="d165d-107">描述</span><span class="sxs-lookup"><span data-stu-id="d165d-107">Description</span></span>|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|<span data-ttu-id="d165d-108">預設初始化模式。</span><span class="sxs-lookup"><span data-stu-id="d165d-108">Default initialization mode.</span></span> <span data-ttu-id="d165d-109">這會初始化執行時間並建立預設值 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="d165d-109">This initializes the runtime and creates the default <xref:System.AppDomain>.</span></span>|  
|`COINITEE_DLL`|<span data-ttu-id="d165d-110">初始化以執行 managed DLL。</span><span class="sxs-lookup"><span data-stu-id="d165d-110">Initializes to run a managed DLL.</span></span>|  
|`COINITEE_MAIN`|<span data-ttu-id="d165d-111">初始化以執行 managed EXE。</span><span class="sxs-lookup"><span data-stu-id="d165d-111">Initializes to run a managed EXE.</span></span> <span data-ttu-id="d165d-112">這會初始化執行時間，但不會建立預設值 <xref:System.AppDomain> ，它會在進入 EXE 的主要常式之後建立。</span><span class="sxs-lookup"><span data-stu-id="d165d-112">This initializes the runtime but does not create the default <xref:System.AppDomain>, which is created after entering the main routine of the EXE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d165d-113">需求</span><span class="sxs-lookup"><span data-stu-id="d165d-113">Requirements</span></span>  

 <span data-ttu-id="d165d-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d165d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d165d-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d165d-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d165d-116">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d165d-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d165d-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d165d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d165d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d165d-118">See also</span></span>

- [<span data-ttu-id="d165d-119">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="d165d-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
