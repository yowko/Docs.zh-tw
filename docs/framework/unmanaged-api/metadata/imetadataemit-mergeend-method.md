---
title: IMetaDataEmit::MergeEnd 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 99c1decf27685f027d6baa8412bf20fdf693d161
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67664025"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd 方法

合併到目前的範圍由一或多個先前的呼叫，以指定的所有中繼資料領域[imetadataemit:: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)。

## <a name="syntax"></a>語法

```cpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>參數

這個方法會接受任何參數。

## <a name="remarks"></a>備註

這個常式會觸發實際的合併中繼資料，所有匯入指定的方法是呼叫範圍`IMetaDataEmit::Merge`，到目前的輸出範圍。

合併，適用下列的特殊狀況：

- 模組版本識別項 （mvid） 發生會永遠不會匯入，因為它是唯一的中繼資料匯入範圍中。

- 會覆不寫任何現有的整個模組的屬性。

  如果模組屬性已設定為目前的範圍，則會匯不入任何模組屬性。 不過，如果模組屬性尚未設定目前範圍中，它們會匯入一次，當他們第一次發生。 如果這些模組內容發生一次，它們是重複的項目。 如果 （MVID) 除外的所有模組屬性的值進行比較，而且沒有重複項目找到，則會引發錯誤。

- 如需類型定義 (`TypeDef`)，沒有重複項目會合併到目前的範圍。 `TypeDef` 物件會檢查是否有重複項目，針對每個*完整物件名稱* + *GUID* + *版本號碼*。 如果沒有相符項目名稱或 GUID，而且有任何其他兩個項目不同，則會引發錯誤。 否則，如果所有的三個項目相符，`MergeEnd`粗略的檢查，以確保項目確實是在重複的項目; 如果沒有，則會引發錯誤。 這項快速檢查會尋找：

  - 同一個成員宣告，以相同的順序發生。 標示為的成員`mdPrivateScope`(請參閱 < [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列舉型別) 中這項檢查; 不包含特殊合併。

  - 相同的類別配置。

  這表示`TypeDef`物件必須一律完整且一致地定義每個中繼資料範圍內宣告中，如果其成員的實作 （類別） 會分散到多個編譯單位中，完整的定義假設為每個範圍中存在且不增量至每個範圍。 比方說，如果參數名稱與合約相關，它們必須發出相同的方式為每個範圍中，如果它們不相關，它們應該不發出至中繼資料。

  例外狀況是，`TypeDef`物件可以有標示為增量成員`mdPrivateScope`。 在發生這些`MergeEnd`以累加方式將它們新增至目前的範圍，而不必考慮重複項目。 因為編譯器了解私用範圍，編譯器必須負責強制執行規則。

- 未匯入或合併; 相對虛擬位址 (Rva)編譯器應該重新發出這項資訊。

- 只有在所連接的項目合併時，才合併自訂屬性。 比方說，第一次遇到類別時，會合併與類別相關聯的自訂屬性。 如果自訂屬性相關聯`TypeDef`或`MemberDef`專屬於編譯單位 （例如將成員編譯的時間戳記），它們不會合併，將由編譯器移除或更新這類中繼資料。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** Cor.h

**LIBRARY:** 做為 MSCorEE.dll 中的資源

**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
