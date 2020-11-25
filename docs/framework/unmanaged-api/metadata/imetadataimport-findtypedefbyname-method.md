---
title: IMetaDataImport::FindTypeDefByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
ms.openlocfilehash: df1516a916b2b48080e4f94937fba063926330ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711295"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="220f4-102">IMetaDataImport::FindTypeDefByName 方法</span><span class="sxs-lookup"><span data-stu-id="220f4-102">IMetaDataImport::FindTypeDefByName Method</span></span>

<span data-ttu-id="220f4-103">取得具有指定名稱之的 TypeDef 元資料標記的指標 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="220f4-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="220f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="220f4-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="220f4-105">參數</span><span class="sxs-lookup"><span data-stu-id="220f4-105">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="220f4-106">在要取得其 TypeDef token 的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="220f4-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="220f4-107">在表示封閉類別的 TypeDef 或 TypeRef token。</span><span class="sxs-lookup"><span data-stu-id="220f4-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="220f4-108">如果要尋找的型別不是嵌套類別，請將此值設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="220f4-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="220f4-109">擴展對應之 TypeDef token 的指標。</span><span class="sxs-lookup"><span data-stu-id="220f4-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="220f4-110">需求</span><span class="sxs-lookup"><span data-stu-id="220f4-110">Requirements</span></span>  

 <span data-ttu-id="220f4-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="220f4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="220f4-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="220f4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="220f4-113">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="220f4-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="220f4-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="220f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="220f4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="220f4-115">See also</span></span>

- [<span data-ttu-id="220f4-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="220f4-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="220f4-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="220f4-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
