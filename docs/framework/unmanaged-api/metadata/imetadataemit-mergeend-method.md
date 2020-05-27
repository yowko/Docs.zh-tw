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
ms.openlocfilehash: feb81b86190f953b50f43f244f4e58a0a482f86e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003915"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd 方法

將一個或多個先前呼叫[IMetaDataEmit：： Merge](imetadataemit-merge-method.md)所指定的所有中繼資料範圍合併到目前的範圍。

## <a name="syntax"></a>語法

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>參數

這個方法不接受任何參數。

## <a name="remarks"></a>備註

此常式會將先前呼叫所指定的所有匯入範圍之中繼資料的實際合併，觸發 `IMetaDataEmit::Merge` 至目前的輸出範圍。

下列特殊條件適用于合併：

- 模組版本識別碼（MVID）永遠不會匯入，因為它對匯入範圍中的中繼資料是唯一的。

- 不會覆寫任何現有的模組範圍屬性。

  如果已針對目前的範圍設定模組屬性，則不會匯入任何模組屬性。 不過，如果目前的範圍內尚未設定模組屬性，則會在第一次遇到時匯入。 如果再次發現這些模組屬性，它們就是重複的。 如果比較所有模組屬性（MVID 除外）的值，但找不到任何重複專案，就會引發錯誤。

- 若為類型定義（ `TypeDef` ），則不會將任何重複專案合併到目前的範圍。 `TypeDef`系統會針對每個*完整的物件名稱*  +  *GUID*  +  *版本號碼*，檢查物件是否有重複的專案。 如果名稱或 GUID 有相符專案，而且其他兩個專案的任何一個都不同，就會引發錯誤。 否則，如果這三個專案都相符， `MergeEnd` 會粗略檢查以確保專案確實重複; 如果不是，則會引發錯誤。 這個粗略的檢查會尋找：

  - 相同的成員宣告，以相同的順序出現。 標記為 `mdPrivateScope` （請參閱[CorMethodAttr](cormethodattr-enumeration.md)列舉）的成員不會包含在這項檢查中，而是以特殊方式合併。

  - 相同的類別版面配置。

  這表示物件在宣告的 `TypeDef` 每個中繼資料範圍中一律必須完全且一致地定義; 如果其成員執行（針對類別）會分散到多個編譯單位，則完整定義會假設存在於每個範圍中，而不會累加到每個範圍。 例如，如果參數名稱與合約有關，則它們必須以相同方式發出到每個範圍;如果不相關，則不應該將它們發出至中繼資料。

  例外狀況是 `TypeDef` 物件可以有標記為的累加成員 `mdPrivateScope` 。 遇到這些情況時，以 `MergeEnd` 累加方式將它們加入至目前的範圍，而不考慮重複專案。 因為編譯器瞭解私用範圍，所以編譯器必須負責強制執行規則。

- 相對虛擬位址（Rva）不會匯入或合併;編譯器應該會重新發出這則資訊。

- 自訂屬性只有在其附加的專案合併時才會合並。 例如，當第一次遇到類別時，會合並與類別相關聯的自訂屬性。 如果自訂屬性與 `TypeDef` `MemberDef` 特定于編譯單位的或相關聯（例如成員編譯的時間戳記），它們就不會合並，而是由編譯器負責移除或更新這類中繼資料。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** Cor。h

連結**庫：** 做為 Mscoree.dll 中的資源使用

**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>另請參閱

- [IMetaDataEmit 介面](imetadataemit-interface.md)
- [IMetaDataEmit2 介面](imetadataemit2-interface.md)
