---
title: ICeeGen::GetIlSection 方法
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
ms.openlocfilehash: 7ef944fd06d07dc8c4e49061a5e72d8acc4d0465
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436340"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="36d81-102">ICeeGen::GetIlSection 方法</span><span class="sxs-lookup"><span data-stu-id="36d81-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="36d81-103">取得指定控制碼所參考之中繼語言程式碼基底的區段。</span><span class="sxs-lookup"><span data-stu-id="36d81-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="36d81-104">這個方法已過時，不應使用。</span><span class="sxs-lookup"><span data-stu-id="36d81-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d81-105">語法</span><span class="sxs-lookup"><span data-stu-id="36d81-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36d81-106">參數</span><span class="sxs-lookup"><span data-stu-id="36d81-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="36d81-107">在要取得之區段的控制碼。</span><span class="sxs-lookup"><span data-stu-id="36d81-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36d81-108">需求</span><span class="sxs-lookup"><span data-stu-id="36d81-108">Requirements</span></span>  
 <span data-ttu-id="36d81-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36d81-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36d81-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="36d81-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36d81-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="36d81-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36d81-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d81-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d81-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36d81-113">See also</span></span>

- [<span data-ttu-id="36d81-114">ICeeGen 介面</span><span class="sxs-lookup"><span data-stu-id="36d81-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
