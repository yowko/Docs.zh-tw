---
title: IMetaDataImport::GetUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
ms.openlocfilehash: af3de5454ce3d4a763c216de6e8efdb39407457b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729131"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="3fe74-102">IMetaDataImport::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="3fe74-102">IMetaDataImport::GetUserString Method</span></span>

<span data-ttu-id="3fe74-103">取得指定中繼資料語彙基元所代表的常值字串。</span><span class="sxs-lookup"><span data-stu-id="3fe74-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fe74-104">語法</span><span class="sxs-lookup"><span data-stu-id="3fe74-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fe74-105">參數</span><span class="sxs-lookup"><span data-stu-id="3fe74-105">Parameters</span></span>  

 `stk`  
 <span data-ttu-id="3fe74-106">在要傳回相關聯之字串的字串標記。</span><span class="sxs-lookup"><span data-stu-id="3fe74-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="3fe74-107">擴展要求的字串複本。</span><span class="sxs-lookup"><span data-stu-id="3fe74-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="3fe74-108">在要求的大小上限（以寬字元為單位） `szString` 。</span><span class="sxs-lookup"><span data-stu-id="3fe74-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="3fe74-109">擴展傳回之的大小（以寬字元為單位） `szString` 。</span><span class="sxs-lookup"><span data-stu-id="3fe74-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fe74-110">需求</span><span class="sxs-lookup"><span data-stu-id="3fe74-110">Requirements</span></span>  

 <span data-ttu-id="3fe74-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3fe74-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fe74-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3fe74-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fe74-113">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="3fe74-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fe74-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fe74-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe74-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fe74-115">See also</span></span>

- [<span data-ttu-id="3fe74-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="3fe74-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3fe74-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="3fe74-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
