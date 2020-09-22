---
title: 剪貼簿的格式無效
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: 429d1e120a0044152a358a87663eb09989f45b0e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874587"
---
# <a name="clipboard-format-is-not-valid"></a>剪貼簿的格式無效

指定的剪貼簿格式與所執行的方法不相容。 此錯誤的可能原因包括：  
  
- 使用剪貼簿 `GetText` 或方法搭配或以外的 `SetText` 剪貼簿格式 `vbCFText` `vbCFLink` 。  
  
- 使用剪貼簿的 `GetData` 或 `SetData` 方法搭配、或以外的剪貼簿格式 `vbCFBitmap` `vbCFDIB` `vbCFMetafile` 。  
  
- 使用的 `GetData` 或 `SetData` 方法，會 `DataObject` 在 microsoft windows 保留的範圍中，將剪貼簿格式用於已註冊的格式 ( # B0 HC000-&HFFFF) ，則表示該剪貼簿格式尚未向 microsoft windows 註冊。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 請移除不正確格式，並指定一個有效的格式。  
  
## <a name="see-also"></a>另請參閱

- [剪貼簿：加入其他格式](/cpp/mfc/clipboard-adding-other-formats)
