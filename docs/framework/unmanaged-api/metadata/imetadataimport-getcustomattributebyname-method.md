---
title: IMetaDataImport::GetCustomAttributeByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c25304bef4d240eedea749bb2829595056f9b74d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449243"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="5f3fd-102">IMetaDataImport::GetCustomAttributeByName 方法</span><span class="sxs-lookup"><span data-stu-id="5f3fd-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="5f3fd-103">取得自訂屬性，指定其名稱和擁有者。</span><span class="sxs-lookup"><span data-stu-id="5f3fd-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f3fd-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f3fd-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f3fd-105">參數</span><span class="sxs-lookup"><span data-stu-id="5f3fd-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="5f3fd-106">[in]表示擁有的自訂屬性的物件中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5f3fd-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="5f3fd-107">[in]自訂屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f3fd-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="5f3fd-108">[out]資料做為自訂屬性的值的陣列指標。</span><span class="sxs-lookup"><span data-stu-id="5f3fd-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="5f3fd-109">[out]以位元組為單位的中傳回的資料大小 \*`ppData`。</span><span class="sxs-lookup"><span data-stu-id="5f3fd-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f3fd-110">備註</span><span class="sxs-lookup"><span data-stu-id="5f3fd-110">Remarks</span></span>  
 <span data-ttu-id="5f3fd-111">它是合法為相同的擁有者; 定義多個自訂屬性他們甚至可能會遇到相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="5f3fd-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="5f3fd-112">不過，`GetCustomAttributeByName`傳回只有一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="5f3fd-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="5f3fd-113">(`GetCustomAttributeByName`傳回遇到的第一個執行個體。)若要尋找自訂屬性的所有執行個體，請呼叫[imetadataimport:: Enumcustomattributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5f3fd-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f3fd-114">需求</span><span class="sxs-lookup"><span data-stu-id="5f3fd-114">Requirements</span></span>  
 <span data-ttu-id="5f3fd-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f3fd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f3fd-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5f3fd-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f3fd-117">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5f3fd-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f3fd-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f3fd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f3fd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f3fd-119">See Also</span></span>  
 [<span data-ttu-id="5f3fd-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5f3fd-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="5f3fd-121">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5f3fd-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
