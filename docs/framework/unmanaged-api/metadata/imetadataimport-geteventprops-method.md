---
title: IMetaDataImport::GetEventProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 369335deb67d74ee3cb9fa407533e40716aa3a3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676854"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps 方法

取得指定之事件標記所代表事件的中繼資料資訊，包括宣告類型、委派的加入和移除方法，以及任何旗標和其他相關聯的資料。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,
   [out] LPCWSTR       szEvent,
   [in]  ULONG         cchEvent,
   [out] ULONG         *pchEvent,
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,
   [out] mdMethodDef   *pmdRemoveOn,
   [out] mdMethodDef   *pmdFire,
   [out] mdMethodDef   rmdOtherMethod[],
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a>參數  

 `ev`  
 在代表要取得中繼資料之事件的事件元資料標記。  
  
 `pClass`  
 擴展表示宣告事件之類別的 TypeDef token 指標。  
  
 `szEvent`  
 擴展所參考之事件的名稱 `ev` 。  
  
 `pchEvent`  
 在要求的長度（以寬字元為單位） `szEvent` 。  
  
 `pdwEventFlags`  
 擴展傳回的長度（以寬字元為單位） `szEvent` 。  
  
 `ptkEventType`  
 擴展表示事件種類之 TypeRef 或 TypeDef 元資料標記的指標 <xref:System.Delegate> 。  
  
 `pmdAddOn`  
 擴展元資料標記的指標，表示新增事件處理常式的方法。  
  
 `pmdRemoveOn`  
 擴展代表移除事件處理常式之方法的元資料標記指標。  
  
 `pmdFire`  
 擴展代表引發事件之方法的元資料標記指標。  
  
 `rmdOtherMethod`  
 擴展與事件相關聯之其他方法的 token 指標陣列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 陣列的大小上限。  
  
 `pcOtherMethod`  
 擴展傳回的權杖數目 `rmdOtherMethod` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cor。h  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IMetaDataImport 介面](imetadataimport-interface.md)
- [IMetaDataImport2 介面](imetadataimport2-interface.md)
