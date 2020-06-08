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
ms.openlocfilehash: e6921a0f6420546ba1e866e37a7a7cb129a77c67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491455"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="24fdc-102">IMetaDataImport::GetCustomAttributeByName 方法</span><span class="sxs-lookup"><span data-stu-id="24fdc-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="24fdc-103">取得自訂屬性，並指定其名稱和擁有者。</span><span class="sxs-lookup"><span data-stu-id="24fdc-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24fdc-104">語法</span><span class="sxs-lookup"><span data-stu-id="24fdc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24fdc-105">參數</span><span class="sxs-lookup"><span data-stu-id="24fdc-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="24fdc-106">在元資料標記，代表擁有自訂屬性的物件。</span><span class="sxs-lookup"><span data-stu-id="24fdc-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="24fdc-107">在自訂屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="24fdc-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="24fdc-108">脫銷資料陣列的指標，這是自訂屬性的值。</span><span class="sxs-lookup"><span data-stu-id="24fdc-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="24fdc-109">脫銷傳回的資料大小（以位元組為單位） \* `ppData` 。</span><span class="sxs-lookup"><span data-stu-id="24fdc-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24fdc-110">備註</span><span class="sxs-lookup"><span data-stu-id="24fdc-110">Remarks</span></span>  
 <span data-ttu-id="24fdc-111">為相同擁有者定義多個自訂屬性是合法的：他們甚至可能會有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="24fdc-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="24fdc-112">不過， `GetCustomAttributeByName` 只會傳回一個實例。</span><span class="sxs-lookup"><span data-stu-id="24fdc-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="24fdc-113">（傳回 `GetCustomAttributeByName` 第一個遇到的實例）。若要尋找自訂屬性的所有實例，請呼叫[IMetaDataImport：： EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="24fdc-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24fdc-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="24fdc-114">Requirements</span></span>  
 <span data-ttu-id="24fdc-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24fdc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24fdc-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="24fdc-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24fdc-117">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="24fdc-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24fdc-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24fdc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24fdc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24fdc-119">See also</span></span>

- [<span data-ttu-id="24fdc-120">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="24fdc-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="24fdc-121">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="24fdc-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
